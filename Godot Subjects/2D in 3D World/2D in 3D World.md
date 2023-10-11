
[YouTube Reference Video](https://www.youtube.com/watch?v=Afq4P6sS-xY)
* <span style="color:tomato;">Sprite3D</span> Node
	* Can take a `SubViewPort` Texture (reference [3D Health Bar in Godot 4](https://www.youtube.com/watch?v=Afq4P6sS-xY))
	* Under `Flags -> Billboard`, enable it
* <span style="color:DimGray;">SubViewPort</span> Node
	* Toggle on `Disable 3D` (if you don't want to treat it with 3D aspects)
	* Toggle on `Transparet BG`
	* <span style="color:SteelBlue;">Node2D</span>
		* Use a <span style="color:SteelBlue;">Node2D</span> and save as a separate scene (otherwise you can't see it without previewing it in the <span style="color:DimGray;">SubViewPort</span> node)
			* Within this new scene you can just do 2D stuff as normal
	* <strong><span style="color:DarkOliveGreen;">UI</span></strong> Node (Like <span style="color:DarkOliveGreen;">ProgressBar</span> Node for `health`)
		* Note if you change values here, it WILL BREAK the <span style="color:tomato;">Sprite3D</span> Node? Maybe not, I just don't see it in the <strong><span style="color:DarkOliveGreen;">UI</span></strong>, but it renders when running the game. I can preview the value by click the respective <span style="color:DimGray;">SubViewPort</span> node
![[2d_on_3D_Sprite2D.png]]
+ The above picture shows the <span style="color:tomato;">Sprite3D</span> that is showing the contents of <span style="color:SteelBlue;">Node2D</span>
	+ notice that <span style="color:SteelBlue;">Node2D</span> is a separate scene
![[2d_on_3D_Sprite2D-2.png]]
+ The above picture shows the contents <span style="color:SteelBlue;">Node2D</span> (2 <span style="color:SteelBlue;">Sprite2D</span>s)


[YouTube Tutorial](https://www.youtube.com/watch?v=NZ7EP1Kt_sI)

---
# Archive

[(Godot 3) Viewport Node | Godot Basics Tutorial | Ep 42](https://www.youtube.com/watch?v=euQZ-jddoBo)
+ <strong><span style="color:DarkOliveGreen;">UI</span></strong> Control Nodes in a 3D scene
+ Node Structure
	+ <strong><span style="color:DarkOliveGreen;">Control</span></strong>
		+ <span style="color:DimGray;">SubViewportContainer</span>
			+ <span style="color:DimGray;">SubViewPort</span>

