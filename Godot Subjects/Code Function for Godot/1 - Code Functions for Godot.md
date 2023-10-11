#code 

# Get <span style="color:Gold;">Node Tree</span> in <span style="color:Gold;">Scene</span>

+ <span style="color:HotPink;">get_tree()</span> - built-in method that allows you to obtain a reference to the game's <span style="color:Gold;">global scene tree</span>
	+ Not an actual nature tree (had previous confusion is a <span style="color:Gold;">scene</span> where a player collides with a tree)

---
# Get <span style="color:Gold;">Resource</span> from <span style="color:Gold;">FileSystem</span> Window

+ <span style="color:HotPink;">preload()</span> - this function will read the file from disk and load it at compile-time. As a result, you cannot call `preload` with a variable path: you need to use a constant string
```python
# this is gdscript, but using python colors in this codeblock
var imported_resource = preload("res://robi.png")
func _ready():
    # Godot loads the resource at compile-time
    get_node("sprite").texture = imported_resource
```

+ <span style="color:HotPink;">load()</span> - just load the resource
```python
# this is gdscript, but using python colors in this codeblock
func _ready():
    # Godot loads the Resource when it reads this very line.
    var imported_resource = load("res://robi.png")
    $sprite.texture = imported_resource
```

---
# Pause

### What does this line of code do: <span style="color:HotPink;">await get_tree().create_timer(0.5).timeout</span>
+ It pauses the code for 0.5 seconds

---
# Restart / Reload a <span style="color:Gold;">Scene</span>

+ <span style="color:HotPink;">.reload_current_scene()</span> - reloads the <span style="color:Gold;">scene</span>:
	+ Reload the <span style="color:Gold;">current scene</span> by grabbing the <span style="color:Gold;">scene tree</span>:
```python
# actually gdscript, just using python md colors in this codeblock
get_tree().reload_current_scene()
```

---

# <span style="color:Gold;">Reference</span>s - No Hardcoded Paths

## Within a Scene
+ When in the <span style="color:Gold;">Scene</span> Window, you can
	+ Right-Click a Node
	+ Select "<span style="color:Gold;">% Access a Unique Name</span>"
		+ This will make a <span style="color:Gold;">Unique Name</span> for that node
	+ Drag & Drop that Node into you code
		+ Now you can access this variable in code in a way that's unique (instead of hard coded drag & drop)

## Outside a Scene
In Godot, use <span style="color:Gold;">UIDs (Unique Identifiers)</span> to reference objects and resources. <span style="color:Gold;">UIDs</span> are particularly useful for referring to objects that may change their path or hierarchy within the scene. Here's how you can use a <span style="color:Gold;">UID</span> to reference an object or resource:

1. **Obtain the <span style="color:Gold;">UID</span>**: 
	+ _To get the <span style="color:Gold;">UID</span> of an object or resource_, you can:
		+ **Right-click** on the target in the <span style="color:Gold;">FileSystem</span> window
		+ Select <span style="color:Gold;">Copy Unique ID</span> from the context menu.
2. **Declare a Variable with the <span style="color:Gold;">UID</span>**: 
	+ In your script, declare a variable and assign the <span style="color:Gold;">UID</span> to it. 
	+ You don't need to specify the variable type
		+ Godot will automatically infer it as <span style="color:Gold;">RID (Resource ID)</span>, which is the type used for <span style="color:Gold;">UIDs</span>.
```python
# this is gdscript, but using python colors in this codeblock
var myResourceUID = "uid://da04133isku3q"
```

3. **Load the Resource**: You can use the <span style="color:HotPink;">load()</span> function to load the resource associated with the <span style="color:Gold;">UID</span>.
```python
# this is gdscript, but using python colors in this codeblock
var myResource = load(myResourceUID)
```
Now, <span style="color:HotPink;">myResource</span> will contain the resource associated with the specified <span style="color:Gold;">UID</span>, whether it's a scene, texture, sound, or any other resource type.

4. **Use the <strong><span style="color:Gold;">Resource</span></strong>**: You can now use <span style="color:HotPink;">myResource</span> in your script. For example, if it's a <span style="color:Gold;">scene</span>, you can instance it as a <span style="color:Gold;">node</span>:
```python
# this is gdscript, but using python colors in this codeblock
var instance = myResource.instance()
```

Keep in mind that <span style="color:Gold;">UIDs</span> are particularly useful for referencing resources or nodes that might be dynamically created or moved within your project. They provide a stable reference even if the path or location of the resource changes. However, be cautious when using <span style="color:Gold;">UIDs</span>, as they won't automatically update if you change or delete the resource in the editor. It's essential to keep track of <span style="color:Gold;">UIDs</span> and ensure they remain valid in your project.

---
# Destroy / Remove a <span style="color:Gold;">Node</span>

+ <span style="color:HotPink;">queue_free()</span>: destroys the current node and deallocates it

+ <span style="color:HotPink;">remove_child()</span>: is a subset of <span style="color:HotPink;">queue_free()</span> and only "removes them from the world", without actually loosing their data
	* <span style="color:HotPink;">remove_child()</span> can be useful in some scenarios. For example, you might want to enter a house, but remember the state of the outside map: remove the map from the tree, add the house, but without destroying either of them. You can then swap nodes in and out.  

---
# Random

**<strong><span style="color:HotPink;">randi_range()</span></strong> - to get random integer**
```python
# this is gdscript, but using python colors in this codeblock
star.position.x = randi_range(-280, 280)
star.position.y = randi_range(-150, 150)
```
 
**<strong><span style="color:HotPink;">randf_range()</span></strong> - to get random float**
```python
# this is gdscript, but using python colors in this codeblock
var star_size = randf_range(0.5, 1.0)
```

---


# <span style="color:Gold;">Resource</span> Sharing

## [In Godot 4.1](https://godotengine.org/article/godot-4-1-is-here/)
Until now, in GDScript, you needed to use a resource or an autoload to share data between multiple instances of the same script.

Thanks to [George Marques](https://github.com/vnen), you can now create and use static variables instead. Static variables store data on the class instead of each instance, so they’re shared between every instance of the class.

To make a variable static, add the `static` keyword in front of a variable defined at the top of your script.

---

---
# VSCode Extension
+ the `godot-tools` extension in VSCode and connect to godot's language server
	+ Default looks at port 6008
	+ Godot 4 uses 6005
		+ you need to go to extension settings for the godot extension, paste the absolute path for the godot version executable you are using, and also the port 6005


