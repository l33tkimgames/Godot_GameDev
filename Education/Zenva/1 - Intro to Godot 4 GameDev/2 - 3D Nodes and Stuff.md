#nodes #3dnodes #reference
### 2D vs 3D
* `SpriteNode` is for 2D what `MeshInstanceNode` is for 3D
* 2D measures in pixels while 3D measures in meters
+ Camera
	+ Can change `FOV` (Field of View) in 3D
	+ This is `Zoom` for 2D nodes

# 3D

## <span style="color:tomato;">Area3D</span>
+ Can detect `collisions`
+ Can detect `Physics` interactions
+ Can detect user clicks
+ Can make a <span style="color:tomato;">MeshInstance3D</span> child of this

## <span style="color:tomato;">MeshInstance3D</span>
* The actual 3D object
* When creating a <span style="color:tomato;">MeshInstance3D</span> you can select the `Mesh` in the `Inspector`
* You can set the mesh shape if you just want a shape
+ Can put this under <span style="color:tomato;">Area3D</span> if you want this to be interactable

## <span style="color:tomato;">CollisionShape3D</span>
+ Can select of collision `Shape`
+ Can change the scale
+ Put this under <span style="color:tomato;">Area3D</span> if you want to be able to detect a collision and fire off a `signal`
	+ [[6 - Signals]]
+ Makes object interactable with Physics
	* [[8 - Physics]]

- `CollisionShape3D` is a node used to define the shape of an object for collision detection.
- It is typically used for objects that do not need physics simulation or movement but still require collision detection, such as walls, static obstacles, or trigger volumes.
- `CollisionShape3D` nodes are often added as children to `StaticBody3D` or `KinematicBody3D` nodes to define the collision shape of these objects.
- These shapes are usually considered immovable and do not respond to forces or gravity.
- `CollisionShape3D` is lightweight and doesn't have the computational overhead associated with physics simulation.
* Example use cases for `CollisionShape3D`:
	- Creating walls, floors, and ceilings in your 3D environment.
	- Defining collision boundaries for trigger volumes or areas of interest.
	- Creating objects that should not move but still need collision detection.


## <span style="color:tomato;">RigidBody3D</span>
* Makes objects be affected by physics and make object INTERACT with the physics engine
	* [[8 - Physics]]
* Often used for things like **CHARACTERS**

- `RigidBody3D` is a node used for simulating physics behavior and movement of 3D objects.
- It is used for objects that need to INTERACT with the physics engine, respond to forces (e.g., gravity, impulses), and simulate realistic physics behavior, such as bouncing, rolling, or falling.
- `RigidBody3D` nodes are often used for **DYNAMIC** objects, like **CHARACTERS**, vehicles, or objects that need to be pushed, pulled, or affected by external forces.
- `RigidBody3D` objects can be controlled programmatically to move, rotate, or apply forces to simulate physical interactions.

* Example use cases for `RigidBody3D`:
	- Controlling the movement and physics interactions of a player character.
	- Simulating rigid bodies like crates, vehicles, or pendulum swings.
	- Creating objects that respond to external forces and gravity.
## <span style="color:tomato;">Camera3D</span>
+ The actual camera to be used
+ Set `Current` on if the given camera is the one that's on
+ Can change `FOV` (Field of View)
	+ This is `Zoom` for 2D nodes

## <span style="color:tomato;">Light/Lighting</span>
[[4 - Lights]]


## <span style="color:tomato;">StandardMaterial3D</span>
[[3 - Materials]]




