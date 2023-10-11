+ <span style="color:HotPink;">@export var things : Array</span>
	+ You can manually set this in the <span style="color:Gold;">Inspector</span> <strong><span style="color:DarkOliveGreen;">UI</span></strong>
	+ This can potentially take any type ([Zenva Video on this @ 1:45ish](https://academy.zenva.com/lesson/combat-actions-part-2/?zva_less_compl=3242679))

+ <span style="color:HotPink;">@export var things : Array[TypeOfThing]</span>
	+ [Zenva Video on this @ 1:45ish](https://academy.zenva.com/lesson/combat-actions-part-2/?zva_less_compl=3242679)
	+ Same things about being able to add elements in the <strong><span style="color:DarkOliveGreen;">UI</span></strong> applies here
	+ If you are using exports for an array, and you only want certain things to be able to go in the array, you can use this syntax in <span style="color:SteelBlue;">Godot 4</span>
	+ <span style="color:HotPink;">TypeOfThing</span> is the <span style="color:HotPink;">class_name</span> you give (somewhere near the top, usually) to a script you have attached to a <span style="color:Gold;">packedscene</span> or some other resource. 
	+ Then, you can't screw it up later on and don't have to rely on comments inside your code to remind you what should go there.
	+ Instead, it will enforce the rule that ONLY <span style="color:HotPink;">TypeOfThing</span> can be added to that array.

* <span style="color:HotPink;">@export var [VAR_NAME] : [VAR_TYPE]</span>
	* <span style="color:HotPink;">@export</span> allows the variable to be modifiable from the <strong><span style="color:DarkOliveGreen;">UI</span></strong>
	* It also allows different nodes that use this script to have different values of the same variable
	* Also allows us to not set a variable and let the user drag and drop the relevant object

+ <span style="color:HotPink;">preload()</span>
	+ Create a reference or link to something when the game starts
	+ Example:
	```python
# this is gdscript, but using python colors in this codeblock
var star_scene = preload("res://Loops/Star.tscn")
```

* <span style="color:HotPink;">_physics_process(delta)</span>
	* Game engines like consistently for physics (uses a consistent tick rate) since frame rate usually isn't consistent
		* Use the <span style="color:HotPink;">_physics_process(delta)</span> function
			* This function gets called at a fixed rate per second
			* Instead of the <span style="color:HotPink;">_physics_process(delta)</span> which is once per frame


---


