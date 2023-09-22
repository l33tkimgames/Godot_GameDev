#code 

# To be Organized

+ <span style="color:HotPink;"> is_instance_valid()</span> - Do this instead of checking for `null`
	+ [YouTube Reference](https://www.youtube.com/watch?v=NpoYYJyWWgU)
	+ Example
	```python
	# actually gdscript, but using python colors for codeblock
	
	@onready var furcifer = $Furcifer
	func _on_timer_timeout():
		if is_instance_valid(furciver):
	```

+ If you make to make sure tween pauses correctly, do
	+ <span style="color:HotPink;">tween = get_tree().create_tween()</span>
		+ **DO NOT DO:** <span style="color:HotPink;">tween = create_tween()</span>

+ <span style="color:HotPink;">@export var things : Array[TypeOfThing]</span>
	+ If you are using exports for an array, and you only want certain things to be able to go in the array, you can use this syntax in Godot 4
	+ <span style="color:HotPink;">TypeOfThing</span> is the <span style="color:HotPink;">class_name</span> you give (somewhere near the top, usually) to a script you have attached to a `packedscene` or some other resource. 
	+ Then, you can't screw it up later on and don't have to rely on comments inside your code to remind you what should go there.
	+ Instead, it will enforce the rule that ONLY <span style="color:HotPink;">TypeOfThing</span> can be added to that array.

* <span style="color:HotPink;">@export var [VAR_NAME] : [VAR_TYPE]</span>
	* <span style="color:HotPink;">@export</span> allows the variable to be modifiable from the UI
	* It also allows different nodes that use this script to have different values of the same variable
	* Also allows us to not set a variable and let the user drag and drop the relevant object

+ <span style="color:HotPink;">preload()</span>
	+ Create a reference or link to something when the game starts
	+ Example:
	```python
# this is gdscript, but using python colors in this codeblock
var star_scene = preload("res://Loops/Star.tscn")
```

* <span style="color:HotPink;">_physics_process(delta)</span>
	* Game engines like consistently for physics (uses a consistent tick rate) since frame rate usually isn't consistent
		* Use the <span style="color:HotPink;">_physics_process(delta)</span> function
			* This function gets called at a fixed rate per second
			* Instead of the <span style="color:HotPink;">_physics_process(delta)</span> which is once per frame
---
# Get Node Tree in Scene

+ `get_tree()` - built-in method that allows you to obtain a reference to the game's global scene tree
	+ Not an actual nature tree (had previous confusion is a scene where a player collides with a tree)

---
# Get <span style="color:Gold;">Resource</span> from <span style="color:Gold;">FileSystem</span> Window

+ `preload()` - this function will read the file from disk and load it at compile-time. As a result, you cannot call `preload` with a variable path: you need to use a constant string
```python
# this is gdscript, but using python colors in this codeblock
func _ready():
    # Godot loads the resource at compile-time
    var imported_resource = preload("res://robi.png")
    get_node("sprite").texture = imported_resource
```
+ `load()` - just load the resource
```python
# this is gdscript, but using python colors in this codeblock
func _ready():
    # Godot loads the Resource when it reads this very line.
    var imported_resource = load("res://robi.png")
    $sprite.texture = imported_resource
```

---
# Pause

### What does this line of code do: `await get_tree().create_timer(0.5).timeout`
+ It pauses the code for 0.5 seconds

---
# Restart / Reload a Scene

+ `.reload_current_scene` - reloads the scene:
+ Reload the current scene by grabbing the scene tree:
```python
# actually gdscript, just using python md colors in this codeblock
get_tree().reload_current_scene()
```

---

# <span style="color:HotPink;">Reference</span>s - No Hardcoded Paths

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

3. **Load the Resource**: You can use the `load()` function to load the resource associated with the <span style="color:Gold;">UID</span>.
```python
# this is gdscript, but using python colors in this codeblock
var myResource = load(myResourceUID)
```
Now, `myResource` will contain the resource associated with the specified <span style="color:Gold;">UID</span>, whether it's a scene, texture, sound, or any other resource type.

4. **Use the Resource**: You can now use `myResource` in your script. For example, if it's a scene, you can instance it as a node:
```python
# this is gdscript, but using python colors in this codeblock
var instance = myResource.instance()
```

Keep in mind that UIDs are particularly useful for referencing resources or nodes that might be dynamically created or moved within your project. They provide a stable reference even if the path or location of the resource changes. However, be cautious when using UIDs, as they won't automatically update if you change or delete the resource in the editor. It's essential to keep track of UIDs and ensure they remain valid in your project.

---
# Destroy / Remove a Node

+ `queue_free()`: destroys the current node and deallocates it

+ `remove_child()`: is a subset of `queue_free()` and only "removes them from the world", without actually loosing their data
	* `remove_child()` can be useful in some scenarios. For example, you might want to enter a house, but remember the state of the outside map: remove the map from the tree, add the house, but without destroying either of them. You can then swap nodes in and out.  

---
# Random

### <span style="color:HotPink;">randi_range()</span> - to get random integer
```python
# this is gdscript, but using python colors in this codeblock
star.position.x = randi_range(-280, 280)
star.position.y = randi_range(-150, 150)
```
 
### <span style="color:HotPink;">randf_range()</span> - to get random float
```python
# this is gdscript, but using python colors in this codeblock
var star_size = randf_range(0.5, 1.0)
```

---


# Resource Sharing

## [In Godot 4.1](https://godotengine.org/article/godot-4-1-is-here/)
Until now, in GDScript, you needed to use a resource or an autoload to share data between multiple instances of the same script.

Thanks to [George Marques](https://github.com/vnen), you can now create and use static variables instead. Static variables store data on the class instead of each instance, so they’re shared between every instance of the class.

To make a variable static, add the `static` keyword in front of a variable defined at the top of your script.

---
# Signals

## Subscribe to a Signal NOT in a Scene w/ UID

+ `References - No Hardcoded Paths -> Outside a Scene` (look above for more detail about <span style="color:HotPink;">Reference</span>s)
```python
# this is gdscript, but using python colors in this codeblock

# Placeholder variables for the node that has signals 
#   I want to subscirbe to. Referencing by FileSystem UID
var turnBasedBattle_node_uid = "uid://abcd1234"
var turnBasedBattle_resource = null
var turnBasedBattle_reference = null

# Called when the node enters the scene tree for the first time.
func _ready():
	# Load the target node using the UID
	turnBasedBattle_resource = load(turnBasedBattle_node_uid)
	
	# Check if the target node exists
	if turnBasedBattle_resource:
		# Instantiate the resource
		turnBasedBattle_reference = \
			turnBasedBattle_resource.instantiate()
		# Connect to the signal
		turnBasedBattle_reference.signal_character_begin_turn.connect(
				_on_signal_FUNCTION_NAME) # signal listern function name
		print("signal_character_begin_turn connected")

func _on_signal_FUNCTION_NAME(variable):
	pass
```
In this code:
1. We declare `target_node_uid` as a string variable and assign it the UID of the target node you want to connect to. Replace `"uid://da04133isku3q"` with the actual UID you want to use.
2. In the `_ready()` function, we load the target resource using `load()` based on the UID. If the resource can be loaded (i.e., it exists), we instance it to create the target node and then connect to its signal.
3. If the resource cannot be loaded (i.e., it doesn't exist or there's an issue with the UID), we handle the situation by printing an error message.
4. This code should effectively connect to the signal of the target node specified by its UID.
## Subscribe to Signal in a Scene

```python
# this is gdscript, but using python colors in this codeblock

var target_node = null # This will be the actual target node if it exists

func _ready():
    # Check if the target node exists in the scene
    if has_node("TargetNode"):
        target_node = %NODE_UNIQUE_NAME
        target_node.connect("signal_name", self, "_on_signal_name")
    else:
        print("TargetNode does not exist in the scene.")

func _on_signal_name(param1, param2):
    pass
```

---
# VSCode Extension
+ the `godot-tools` extension in VSCode and connect to godot's language server
	+ Default looks at port 6008
	+ Godot 4 uses 6005
		+ you need to go to extension settings for the godot extension, paste the absolute path for the godot version executable you are using, and also the port 6005

