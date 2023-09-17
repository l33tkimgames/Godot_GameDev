#tool #code
### Question
Is there a way to grab a `MeshInstance3D` that is a 3D character model and auto apply an animation tree to it and create a new .tscn representing the newly rigged model in Godot?


In Godot, you can programmatically manipulate and export scenes, including character models with animations, to create new `.tscn` files. However, this process requires some scripting and knowledge of the Godot API. Here's a general outline of how you can achieve this:

1. **Load the Original Model**:
    - Load the original `.tscn` or `.glb` (or other supported format) file that contains your 3D character model with its animations into a `PackedScene` or `SceneTree` in your Godot script.

2. **Add an Animation Tree**:
    - Create an `AnimationTree` and configure it with the necessary nodes (e.g., `AnimationNodeBlendTree`, `AnimationNodeStateMachine`, etc.) and animations. You can do this programmatically in your script.

3. **Attach the Animation Tree**:
    
    - Attach the `AnimationTree` to your character model's `AnimationPlayer` or another appropriate node that controls animations. This step connects your animation tree to the character model.

4. **Capture the Modified Model**:
    
    - To capture the modified model, you can use the `SceneTree.capture_node_3d` method to capture a snapshot of the modified character model with animations. This will return a `ViewportTexture` containing the rendered image of the model with animations applied.

5. **Create a New Scene**:
    
    - Create a new scene by instantiating a `PackedScene` and adding the captured model as a child node to the new scene.

6. **Export the New Scene**:
    
    - Use the `ResourceSaver.save` method to export the new scene to a `.tscn` file.

Here's a simplified example in GDScript:

```python
extends Node

func capture_and_export_character():
    # 1. Load the original character scene
    var original_scene = load("res://path/to/original_character.tscn")

    # 2. Create an AnimationTree and configure it programmatically
	# TODO
	
    # 3. Attach the AnimationTree to the character's AnimationPlayer
    # TODO
    
    # 4. Capture the modified character model
    var captured_model = $SceneTree.capture_node_3d(original_scene.instance(), Vector2(800, 600))

    # 5. Create a new scene and add the captured model
    var new_scene = PackedScene.new()
    new_scene.instance()  # Create an instance of the new scene
    new_scene.get_node("CapturedModel").add_child(captured_model)

    # 6. Export the new scene to a `.tscn` file
    ResourceSaver.save("res://path/to/exported_scene.tscn", new_scene)
```

Please note that this is a simplified example, and you may need to adapt it to your specific project and requirements. Additionally, it's important to handle resource management and clean up after exporting the scene.