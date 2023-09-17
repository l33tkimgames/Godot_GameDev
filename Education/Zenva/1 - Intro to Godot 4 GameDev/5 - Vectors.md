#code #vectors

* Can change global position
```python
# 	// (it's acutally gdscript, but using python md colors)
global_position.x = 200
```

* Can use Vectors as direction
```python
# 	// (it's acutally gdscript, but using python md colors)
var direction = Vector3(1,1,1)
global_position += direction
```


* Use delta control time
	* Below is moving a direction a 100m per second
```python
# 	// (it's acutally gdscript, but using python md colors)
func _process(delta):
	var direction = Vector3(1,1,1)
	global_position += direction * 100 * delta
```

* Add to timer every second using `delta` as opposed to frame
```python
# 	// (it's acutally gdscript, but using python md colors)
var timer : float = 0.0

func _process(delta):
	timer += 1.0 * delta
	print(timer) # should print every second
```