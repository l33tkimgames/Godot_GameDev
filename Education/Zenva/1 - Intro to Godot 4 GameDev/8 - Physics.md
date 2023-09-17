#physics #collision #interaction #rigidbody #code

* You'll typically use a `RigidBody` node such as <span style="color:tomato;">RigidBody3D</span> to make a node interactable with physics (anything with a <span style="color:tomato;">CollisionObject3D</span> type node)

Can control things like:
  + Mass
	  + Making mass bigger may change things like force and speed (depends on what you are doing)
  + Inertia
  + Gravity Scale
  + Linear (Linear Drag)
	  + Velocity
	  + Damp Mode
	  + Damp (damps velocity over time)
  + Angular (Angular Drag)

### Example Code 

This code, for a 2D physics-enabled node in Godot, applies an impulse towards the mouse’s position whenever the left mouse button is pressed. The strength of the impulse is determined by `hit_force`.

```js
// this is gdscript, but using js colors in this codeblock
extends RigidBody2D
var hit_force : float = 50.0

func _process(delta):

  if Input.is_mouse_button_pressed(MOUSE_BUTTON_LEFT):

	# Get direction from current node location to the mouse position
	#   `global_position` is the current node's position
    var dir = global_position.direction_to(get_global_mouse_position())
    
    apply_impulse(dir * hit_force)
```