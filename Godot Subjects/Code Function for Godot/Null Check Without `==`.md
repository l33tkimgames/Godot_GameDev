+ <span style="color:HotPink;"> is_instance_valid()</span> - Do this instead of checking for `null`
	+ [YouTube Reference](https://www.youtube.com/watch?v=NpoYYJyWWgU)
	+ Example
	```python
	# actually gdscript, but using python colors for codeblock
	
	@onready var furcifer = $Furcifer
	func _on_timer_timeout():
		if is_instance_valid(furciver):
	```

