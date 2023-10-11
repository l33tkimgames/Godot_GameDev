# Print Node Tree
```python
# actually gdscript, just using python colors for codeblock
func _ready():
	# send the root node to print_scene_nodes function
	print_scene_nodes(get_tree().get_root())

func print_scene_nodes(node, indent = 0):
	var indent_str = ""
	for i in range(0, indent):
		indent_str += "  "
	print(indent_str, node.get_name())

	for child in node.get_children():
		print_scene_nodes(child, indent + 1)
```


