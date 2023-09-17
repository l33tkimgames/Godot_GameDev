#vfx #userinteraction #mouseclick #specialeffects #code #signals 
#vectormath #vectors

[Video](https://academy.zenva.com/lesson/balloon-popper-part-2-7/)

## BalloonPopper.gd
* This script controls a 3D area in Godot, a “balloon”,
	* allowing it to be clicked a set number of times before disappearing. 
* With each click, 
	* the area increases in size. 
* Once the area has been clicked the defined number of `clicks_to_pop` times, 
	* it adds a defined score to the main game and then removes itself from the game.
```python
# this is gdscript, but using python colors in this codeblock
extends Area3D
@export var clicks_to_pop : int = 5 # how many times to click to pop
@export var size_increase : float = 0.2 # scale of how much to increase ballon size when we click on it
@export var score_to_give : int = 1

# This function is trigger when the respective CollisionObject3D 
# `input_event` signal is triggered
func _on_input_event(camera, event, position, normal, shape_idx):

  # Only do something if it's a mouse click with the left button,
  #   but only when it's pressed
  if event is InputEventMouseButton and event.button_index == MOUSE_BUTTON_LEFT and event.pressed:

	# multiply integer by Vecotor3.ONE to easily create scaled vection
    scale += Vector3.ONE * size_increase
    clicks_to_pop -= 1
    
    if clicks_to_pop == 0:
      # calls function in a script from a hardcoded place "/root/Main"
      # This is because the root Node is name Main
      get_node("/root/Main").increase_score(score_to_give)
      
      queue_free() # the deletes (deallocates) the current node,
				   # thus destroying the balloon
```



## BalloonManager.gd
+ This script acts as a score manager for a 3D Game (balloon) in Godot. 
+ It holds a score value which can be increased through the `increase_score` function, 
	+ and updates the displayed score on a user interface label each time the score changes.
```c#
 // (it's acutally gdscript, but using C# md colors)
extends Node3D
var score : int = 0
@export var score_text : Label
func increase_score (amount):
  score += amount
  score_text.text = str("Score: ", score)
```