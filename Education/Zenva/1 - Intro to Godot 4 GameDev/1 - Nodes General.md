#nodes
# Nodes
* Children nodes inherit the following from the parent node:
	1. position
	2. rotation
	3. scale

* You can `Right-Click` a node and save it as a scene (`.tscn`)

* You can associate a Node with a Group (like `TAGS` in Unity)
	* For tagging nodes like `Enemy`, `Player`, etc.
	* Put this on things like <span style="color:tomato;">RigidBody3D</span> , <span style="color:tomato;">StaticBody3D</span>, etc.
	* How to:
		1. Select Node in `Scene` window (should be on left)
		2. Select `Node` window (should be on the right)
		3. Select `Groups` in the `Node` window (should be right of `Signals`)

---
## Starting a Scene
* You'll want a camera and lighting. Typically:
	* <span style="color:tomato;">Camera3D</span>
	* <span style="color:tomato;">DirectionalLight3D</span>

---
## Players / Character

+ When making a player / character you typically have this node structure:
	+ <span style="color:tomato;">RigidBody3D</span>
		+ <span style="color:tomato;">MeshInstance3D</span>
		+ <span style="color:tomato;">CollisionShape3D</span>

---