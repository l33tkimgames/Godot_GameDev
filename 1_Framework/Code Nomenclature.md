#### Table of Contents
	1. Resource
	2. Signals

# 1. <span style="color:Gold;">Resource</span>
+ TL;DR -> <span style="color:HotPink;">class_name</span> must start with <span style="color:HotPink;">R</span>

1. Create a resource in the `res://` folder
	+ Right-Click: <span style="color:Gold;">res://</span>
	+ Select: <span style="color:Gold;">+ Create New      -></span>
	+ Change the <span style="color:Gold;">Inherits:</span> to <span style="color:Gold;">Resource</span>
	+ Set the script name
2. The class_name of the <span style="color:Gold;">Resource</span> should start with a <span style="color:HotPink;">R</span>
	+ Template: <span style="color:HotPink;">class_name RClass_Name</span>
	+ Example: <span style="color:HotPink;">class_name RCombat_Action</span>


# 2. <span style="color:HotPink;">Signals</span>

## Signals - Emit Signal
+ Start with <span style="color:HotPink;">signal_</span> so I know it's a signal
+ Example:
```python
# this is gdscript, but using python colors in this codeblock
signal signal_character_begin_turn(character)
signal signal_character_end_turn(character)
```

## Signal Reception
+ Start with <span style="color:HotPink;">_on_signal_</span>
+ Example:
```python
# this is gdscript, but using python colors in this codeblock
func _on_signal_character_begin_turn(character):
	print("_on_signal_character_begin_turn function ran")
```