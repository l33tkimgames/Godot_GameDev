+ This script controls the movement of a 3D rigid body in Godot. 
+ It responds to left and right arrow key presses to move at a defined speed. 
+ If the body collides with a body in the “Tree” group, the current scene is reloaded.
	+ If using <span style="color:tomato;">RigidBody3D</span>, make sure to enable `Contact Monitor`
```python
# this is gdscript, but using python colors in this codeblock
extends RigidBody3D

@export var move_speed : float = 2.0

func _physics_process(delta):
  
  if Input.is_key_pressed(KEY_LEFT):
    linear_velocity.x = -move_speed
    
  if Input.is_key_pressed(KEY_RIGHT):
    linear_velocity.x = move_speed

# RigidBody3D's `body_entered()` signal triggers this function
func _on_body_entered(body):
  if body.is_in_group("Tree"):
	# This gets the `GLOBAL SCENE TREE` (not the tree model)
	# Then it reloads the current scene
    get_tree().reload_current_scene()
```