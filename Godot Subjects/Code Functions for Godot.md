#code 

+ When in the `Scene` Window, you can
	+ Right-Click a Node
	+ Select `% Access a Unique Name`
	+ Now you can access this variable in code in a way that's unique (instead of hard coded drag & drop)

+ `is_instance_valid()` - Do this instead of checking for `null`
	+ [YouTube Reference](https://www.youtube.com/watch?v=NpoYYJyWWgU)
	+ Example
	```python
	# actually gdscript, but using python colors for codeblock
	
	@onready var furcifer = $Furcifer
	func _on_timer_timeout():
		if is_instance_valid(furciver):
	```

+ If you make to make sure tween pauses correctly, do
	+ `tween = get_tree().create_tween()`
		+ Don't do: `tween = create_tween()`

+ `@export var things : Array[TypeOfThing]`
	+ If you are using exports for an array, and you only want certain things to be able to go in the array, you can use this syntax in Godot 4
	+ `TypeOfThing` is the `class_name` you give (somewhere near the top, usually) to a script you have attached to a packedscene or some other resource. 
	+ Then, you can't screw it up later on and don't have to rely on comments inside your code to remind you what should go there.
	+ Instead, it will enforce the rule that ONLY `TypeOfThing` can be added to that array.

* `@export var [VAR_NAME] : [VAR_TYPE]`
	* `@export` allows the variable to be modifiable from the UI
	* It also allows different nodes that use this script to have different values of the same variable
	* Also allows us to not set a variable and let the user drag and drop the relevant object

+ `preload()`
	+ Create a reference or link to something when the game starts
	+ Example:
	```python
# this is gdscript, but using python colors in this codeblock
var star_scene = preload("res://Loops/Star.tscn")
```

* `_physics_process(delta)`
	* Game engines like consistently for physics (uses a consistent tick rate) since frame rate usually isn't consistent
		* Use the `_physics_process(delta)` function
			* This function gets called at a fixed rate per second
			* Instead of the `_process(delta)` which is once per frame
---
### Get Node Tree in Scene
+ `get_tree()` - built-in method that allows you to obtain a reference to the game's global scene tree
	+ Not an actual nature tree (had previous confusion is a scene where a player collides with a tree)

---
### Restart / Reload a Scene
+ `.reload_current_scene` - reloads the scene:
+ Reload the current scene by grabbing the scene tree:
```python
# actually gdscript, just using python md colors in this codeblock
get_tree().reload_current_scene()
```

---
### Destroy / Remove a Node

+ `queue_free()`: destroys the current node and deallocates it

+ `remove_child()`: is a subset of `queue_free()` and only "removes them from the world", without actually loosing their data
	* `remove_child()` can be useful in some scenarios. For example, you might want to enter a house, but remember the state of the outside map: remove the map from the tree, add the house, but without destroying either of them. You can then swap nodes in and out.  

---
### Random

+ `randi_range()` - to get random integer
```python
# this is gdscript, but using python colors in this codeblock
star.position.x = randi_range(-280, 280)
star.position.y = randi_range(-150, 150)
```
 
+  `randf_range()` - to get random float
```python
# this is gdscript, but using python colors in this codeblock
var star_size = randf_range(0.5, 1.0)
```

---

# VSCode Extension
+ the `godot-tools` extension in VSCode and connect to godot's language server
	+ Default looks at port 6008
	+ Godot 4 uses 6005
		+ you need to go to extension settings for the godot extension, paste the absolute path for the godot version executable you are using, and also the port 6005

