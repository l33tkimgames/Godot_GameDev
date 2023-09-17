#physics #collision #interaction #rigidbody #code

Relevant Nodes:
+ <span style="color:tomato;">RigidBody3D</span>
+ <span style="color:tomato;">CollisionObject3D</span>
+ <span style="color:tomato;">StaticBody3D</span>
+ etc?
+ Reference for more detail: [[2 - 3D Nodes and Stuff]]
---
If a <span style="color:tomato;">RigidBody3D</span> needs to be able to DETECT a COLLISION,
+ [[2 - 3D Nodes and Stuff]] - there should be a section in <span style="color:tomato;">RigidBody3D</span> for what to do
---
_(Did the following apply to all physics nodes?)_
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

---
### For things like Character / Object Movement, use `_physics_process(delta)` instead of `_process(delta)`
+ Particularly if physics is paramount to how it functions (like skiing / driving)
* Game engines like consistently for physics (uses a consistent tick rate) since frame rate usually isn't consistent
	* `_physics_process(delta)`
		* Use the `_physics_process(delta)` function
			* This function gets called at a fixed rate per second
			* Instead of the `_process(delta)` which is once per frame
---
### Example Code: Moving a Direction

+ This code, for a 2D physics-enabled node in Godot, 
	+ applies an impulse towards the mouse’s position 
		+ whenever the left mouse button is pressed. 
		+ The strength of the impulse is determined by `hit_force`.

```python
#this is gdscript, but using python colors in this codeblock
extends RigidBody2D
var hit_force : float = 50.0

func _process(delta):

  if Input.is_mouse_button_pressed(MOUSE_BUTTON_LEFT):

	# Get direction from current node location to the mouse position
	#   `global_position` is the current node's position
    var dir = global_position.direction_to(get_global_mouse_position())
    
    apply_impulse(dir * hit_force)
```

---