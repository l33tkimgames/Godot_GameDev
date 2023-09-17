
 * Access the root node
 ```python
 # Actually gdscript, but using python colors for this codeblock
      get_node("/root/[NAME_OF_ROOT_NODE]")
 ```
* Resources are assets in Godot
	* `Right-Click` -> `New` -> `Resource`

* If sprite is blurry:
	* Can be cause of filtering of textures
	*  Go to `Project -> Project Settings -> General -> Rendering -> Textures`
	* Change `Canvas Textures -> Default Texutre Filter` to `Nearest`
	* Typically you do this for Pixel art, but use `Linear` for higher definition images
# Unity  -> Blender -> Godot
1. [Exporting Characters and Animations From Mixamo To Godot4!](https://www.youtube.com/watch?v=AoiRvmSfGOo)
2. [Godot 4 Gets Blender Support! | Lets Look At Godot 4.0](https://www.youtube.com/watch?v=AoiRvmSfGOo)


* Godot can use `.blend` objects directly in the engine

* If I imported a `.glb` / `.fbx`, I can:
	* `Right-Click` -> `New Inherited Scene`
	* This will make a new scene for it and I can save it as a `.tscn`
	* [YouTube Reference](https://www.youtube.com/watch?v=AoiRvmSfGOo)





