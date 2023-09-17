+ This code adds, or “spawns,” a certain number of star nodes 
	+ (defined by `spawn_count`) 
	+ to a 2D game scene in Godot. 
	+ Each star’s appearance and position is randomly generated: 
		+ their x and y coordinates, and their size all vary.

```python
# this is gdscript, but using python colors in this codeblock
extends Node2D
@export var spawn_count : int = 200

# The star we want to spawn
# Will have the reference loaded when the game starts cause of `preload()`
var star_scene = preload("res://Loops/Star.tscn")

# Called when the node enters the scene tree for the first time.
func _ready():
  for i in spawn_count:

    # Instantiate / Spawn new star
    var star = star_scene.instantiate()
    
	# Current node it the root node
	# So will add the star to the root node scene
    add_child(star)
    
	# Using `randi_range()` to get random integer
    star.position.x = randi_range(-280, 280)
    star.position.y = randi_range(-150, 150)
    
    # Using `randf_range()` to get random float
    var star_size = randf_range(0.5, 1.0)
    star.scale.x = star_size
    star.scale.y = star_size
```