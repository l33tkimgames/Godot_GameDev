#code 


* `@export var [VAR_NAME] : [VAR_TYPE]`
	* `@export` allows the variable to be modifiable from the UI
	* It also allows different nodes that use this script to have different values of the same variable
	* Also allows us to not set a variable and let the user drag and drop the relevant object

+ `preload()`
	+ Create a reference or link to something when the game starts
	+ Example:
	```python
# (it's acutally gdscript, but using python colors for this codeblock)
var star_scene = preload("res://Loops/Star.tscn")
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
# (it's acutally gdscript, but using python colors for this codeblock)
star.position.x = randi_range(-280, 280)
star.position.y = randi_range(-150, 150)
```
 
+  `randf_range()` - to get random float
```python
# (it's acutally gdscript, but using python colors for this codeblock)
var star_size = randf_range(0.5, 1.0)
```

---



