#code 


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



