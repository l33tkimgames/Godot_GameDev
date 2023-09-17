#nodes #visuals #art 

* `Material`s are a `Resource`
* `Resource`s are assets in Godot
### How to Make a Material
1. `Right-Click` -> `New` -> `Resource`
2. Search for `Material`
3. You should see a list of materials
4. Select `StandardMaterial3D` for most materials
5. The new material should be a `.tres` file
### Change Configurations of the `Material`
1. Select `Albedo` in the material
	* You can Select `Color`
	* You can set the `Texture`
		* Can drag and drop a sprite / png here
1. `Roughness`
	+ Closer to `0` means smoother (so it'll be shinier)
2. `Metallic`
	+ Closer to `1` means a more metallic looking material
3. `Transparency`
	* Set to `Alpha` (`Alpha Hash` will only make certain parts transparent)
	* Go back to `Color` and set the `A` field (leftmost is fully transparent)
	* `Blend Mode`:
		* Controls what it does with other
			* So if `Add` will add blue transparent color on anything you see through it
			* Typically use `Mix`
	

### Applying a `Material` to a `MeshInstance3D`
+ You can just drag and drop the `Material` to the `MeshInstance3D`

### Can I Convert Unity Material to Godot?
```
No, you cannot directly convert Unity materials to Godot materials because Unity and Godot use different rendering engines and material systems. Unity uses its own proprietary material system, while Godot uses a physically-based rendering (PBR) material system.

To use assets created in Unity in Godot, you would need to recreate the materials manually in Godot using the PBR shader system provided by Godot. This means setting up the material properties like albedo (base color), metallic, roughness, normal maps, and so on, in a way that is compatible with Godot's rendering engine.

Here's a general process you can follow when transitioning assets from Unity to Godot:

1. Export textures: Export the textures used in your Unity materials (e.g., albedo, normal maps, etc.) to image files (e.g., PNG or JPEG).
    
2. Create new materials in Godot: In Godot, create new PBR materials for your 3D objects or sprites.
    
3. Assign textures: Import the exported textures into Godot and assign them to the appropriate slots in your Godot materials (albedo, normal, metallic, roughness, etc.).
    
4. Adjust material properties: Adjust the material properties in Godot to match the look and feel you had in Unity. This may involve tweaking values like roughness, metallic, and emission to achieve the desired appearance.
    
5. Test and iterate: Test your materials in the Godot scene to ensure they look as expected. You may need to iterate and make further adjustments to fine-tune the appearance.
    
6. Implement shaders (if needed): If your Unity materials used custom shaders, you may need to recreate those shaders in Godot's shader language (GDScript) to achieve the same visual effects.
    

While there isn't an automatic conversion process, following these steps should help you recreate the materials and achieve a similar visual result in Godot as you had in Unity. Keep in mind that some features and effects available in Unity may not have direct equivalents in Godot, so you may need to adapt your assets accordingly.
```


