


[3D Health Bar in Godot 4](https://www.youtube.com/watch?v=Afq4P6sS-xY)
* <span style="color:tomato;">Sprite3D</span> Node
	* Can take a `SubViewPort` Texture (reference [3D Health Bar in Godot 4](https://www.youtube.com/watch?v=Afq4P6sS-xY))
	* Under `Flags -> Billboard`, enable it
	* <span style="color:DimGray;">SubViewPort</span> Node
		* Toggle on `Disable 3D` (if you don't want to treat it with 3D aspects)
		* Toggle on `Transparet BG`
		* <span style="color:DarkOliveGreen;">UI</span> Node (Like <span style="color:DarkOliveGreen;">ProgressBar</span> Node for `health`)
			* Note if you change values here, it WILL BREAK the <span style="color:tomato;">Sprite3D</span> Node
			* So BE CAREFUL if you make changes to this on a more substantially completed product


[YouTube Tutorial](https://www.youtube.com/watch?v=NZ7EP1Kt_sI)

---
### Archive

[(Godot 3) Viewport Node | Godot Basics Tutorial | Ep 42](https://www.youtube.com/watch?v=euQZ-jddoBo)
+ UI Control Nodes in a 3D scene
+ Node Structure
	+ Control
		+ SubViewportContainer
			+ SubViewport