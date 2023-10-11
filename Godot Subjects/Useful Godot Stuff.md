[Unity -> Godot](https://www.applovin.com/blog/migrating-from-unity-to-other-game-engines/) <-- visit again
+ [UniFree Tool](https://github.com/ProjectUnifree/unifree)


 * Access the root node
 ```python
 # Actually gdscript, but using python colors for this codeblock
      get_node("/root/[NAME_OF_ROOT_NODE]")
 ```

* Resources are assets in Godot
	* `Right-Click` -> `New` -> `Resource`
	* A texture is a type of resource

* If sprite is blurry:
	* Can be cause of filtering of textures
	*  Go to `Project -> Project Settings -> General -> Rendering -> Textures`
	* Change `Canvas Textures -> Default Texutre Filter` to `Nearest`
	* Typically you do this for Pixel art, but use `Linear` for higher definition images

# UI

+ When observing a UI node you get new green options up top (right below the scene tabs)
	+ If you have `Anchor Preset` you can auto snap your UI node into the part of the screen you want it to be

# Unity  -> Blender -> Godot
1. [Exporting Characters and Animations From Mixamo To Godot4!](https://www.youtube.com/watch?v=AoiRvmSfGOo)
2. [Godot 4 Gets Blender Support! | Lets Look At Godot 4.0](https://www.youtube.com/watch?v=AoiRvmSfGOo)
+ How to use in Godot
	+ Go to `Project -> Project Settings...`
		+ Go to `General` tab
		+ Toggle on `Advanced Settings`
		+ Search for `Blender`
			+ Should be under `File System -> Import`
		+ Make sure Blender is `enabled`
			+ May have to toggle off and on agian
		+ Click `Save & Restart` button on bottom right
	+ Go to `Editor -> Editor Settings...`
		+ Search for `Blender`
			+ Should be under `File System -> Import`
		+ Set the `Blender 3 Path`
+ Now you can use `.blend` files
	+ Try to save directly into the Godot project
	+ If you have it as a node, try right-clicking it and toggling on `Editable Children`
		+ This shows anything else imported from blender (like camera an lighting)
	+ If you don't want certain thing in blender to be imported into Godot
		+ In `Blender` add `-noimp` to things you don't want imported 
	+ If you want things to have mesh imported
		+ In `Blender`, add a `-col` suffix
+ You can import Blender `Materials` into Godot
	+ You can import a `Texture` into Godot
	+ Make sure to do this in Blender before doing this (cause Godot might try to import textures after material and cause errors):
		+ Go to `File -> Export Data -> Pack Resources`
		+ In the image file from the `Shader` tab in `Blender`
			+ Click the `Unpack Item` button
			+ Choose the `Use file from current directory (create when necessary)`


* Godot can use `.blend` objects directly in the engine

* If I imported a `.glb` / `.fbx`, I can:
	* `Right-Click` -> `New Inherited Scene`
	* This will make a new scene for it and I can save it as a `.tscn`
	* [YouTube Reference](https://www.youtube.com/watch?v=AoiRvmSfGOo)


# Pixel Tools

### Aesprite Animatione

* Some time ago on the GameFromScratch YouTube channel there was a YouTube video about the plugin [Aseprite Animation Importers](https://youtu.be/FPtJ1fgjQSg "https://youtu.be/FPtJ1fgjQSg") for Godot.  
	* The author of this plugin, introduced a more [advanced plugin](https://discord.com/channels/245092069415190528/640547771790917636/1138108258469556334)







# CLOSE ALL SCENES BEFORE YOU START MOVING THINGS IN THE FILESYSTEM