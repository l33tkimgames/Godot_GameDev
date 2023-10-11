#### Table of Contents
1. Resource
2. Template
3. Signals

---
# 1. <span style="color:Gold;">Resource</span>
## TL;DR -> <span style="color:HotPink;">class_name</span> must start with <span style="color:HotPink;">R</span>

1. Create a resource in the `res://` folder
	+ Right-Click: <span style="color:Gold;">res://</span>
	+ Select: <span style="color:Gold;">+ Create New      -></span>
	+ Change the <span style="color:Gold;">Inherits:</span> to <span style="color:Gold;">Resource</span>
	+ Set the script name
2. The class_name of the <span style="color:Gold;">Resource</span> should start with a <span style="color:HotPink;">R</span>
	+ Template: <span style="color:HotPink;">class_name RClass_Name</span>
	+ Example: <span style="color:HotPink;">class_name RCombat_Action</span>

---
# 2. <span style="color:Gold;">Template</span> / <span style="color:HotPink;">Template</span>
## TL;DR -> must start with <span style="color:HotPink;">T</span>
+ Example: <span style="color:HotPink;">var TSpite3DChar_node = get_node("Template_Sprite3D_Character")</span>

+ This is **NOT** a traditional template in coding (NOT `<T>`)
+ This is just an arbitrary template **I MADE FOR MODULARIZATION**

---
# 3. <span style="color:HotPink;">Signals</span>

# Use a Messenger Bus Pattern
[Godot 4 Tutorial - The Message Bus Pattern]

## Signals - Emit Signal
+ Start with <span style="color:HotPink;">signal_</span> so I know it's a signal
+ Example:
```python
# this is gdscript, but using python colors in this codeblock
signal signal_character_begin_turn(character)
signal signal_character_end_turn(character)
```
## Signal Reception
+ Start with <span style="color:HotPink;">_on_[NODE]_[SIGNAL_NAME]_</span>
	+ Example:
```python
	# this is gdscript, but using python colors in this codeblock
	func _on_button_character_begin_turn(character):
		print("_on_button_character_begin_turn function ran")
```

---



