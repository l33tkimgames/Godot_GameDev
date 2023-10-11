#code #signals

---

# Node - Check if Signal is Connected
+ [is_connected](https://docs.godotengine.org/en/stable/classes/class_object.html#class-object-method-is-connected) **(** [StringName](https://docs.godotengine.org/en/stable/classes/class_stringname.html#class-stringname) signal, [Callable](https://docs.godotengine.org/en/stable/classes/class_callable.html#class-callable) callable **)** const

---

# Messenger Bus Pattern to Organize Signals

+ Project -> Project Settings -> Autoload
	+ Select the `Messenger.gd` (or whatever you named it)
Example Setup:
+ `Messenger.gd`:
```python
# this is gdscript, but using python colors in this codeblock
extends Node

# emitter is so we know which node initiated this signal
signal HELLO_WORLD(emitter)
```
+ `Game_World.gd`
```python
# this is gdscript, but using python colors in this codeblock


```
+ `Enemy.gd`

YouTube References:
1. [Smarter Godot Signals with the Event Autoload pattern (tutorial)](https://www.youtube.com/watch?v=S6PbC4Vqim4)
2. [Godot 4 Tutorial - The Message Bus Pattern](https://www.youtube.com/watch?v=vbw1ncvSUYg)

---
# Dynamically Connect to Signals
In <span style="color:SteelBlue;">Godot</span>, you cannot directly _**subscribe**_ to a <span style="color:HotPink;">signal</span> for a <span style="color:Gold;">node</span> that may be embedded in a <span style="color:Gold;">scene</span> at a future point because <span style="color:HotPink;">signals</span> are connected to existing nodes in the <span style="color:Gold;">scene</span> hierarchy. 

However, you can _**design your code**_ in a way that allows you to _**connect**_ <span style="color:HotPink;">signals</span> dynamically when <span style="color:Gold;">nodes</span> are added or embedded at runtime. Here's a common approach to achieve this:

1. **Use a Placeholder <strong><span style="color:Gold;">Node</span></strong>**: In your scene where you want to _**subscribe**_ to a <span style="color:HotPink;">signal</span>, create a placeholder <span style="color:Gold;">node</span>. This <span style="color:Gold;">node</span> will act as a reference point for _**connecting**_ <span style="color:HotPink;">signals</span>
    
2. **Connect <strong><span style="color:HotPink;">Signals</span></strong> Dynamically**: In the <span style="color:HotPink;">script</span> of the <span style="color:Gold;">node</span> containing the placeholder, you can connect <span style="color:HotPink;">signals</span> dynamically when a <span style="color:Gold;">node</span> is added or embedded at runtime. Use the <span style="color:HotPink;">_ready</span> or <span style="color:HotPink;">_enter_tree</span> callback to perform these dynamic connections
```python
# this is gdscript, but using python colors in this codeblock
extends Node

var root_node = null

func _ready():
	root_node = get_tree().get_root()
	_connect_signals()

func _connect_signals():

	# Check if the [PLACEHOLDER] node exists in the scene tree
	if root_node.has_node("[PLACEHOLDER]"):
		# Get the [PLACEHOLDER] node
		placeholder_node = root_node.get_node("[PLACEHOLDER]")
		
		# Get Callable reference to the signal handling function
		var func_on_signal_handler = Callable(self, "_on_signal_handler")
		# Check if the target signal is already connected
		if not placeholder_node.is_connected(
			"signal_name", func_on_signal_handler):
			
			# If not connected, connect the signal dynamically
			placeholder_node.connect(
				"signal_name", 
				func_on_signal_handler)

func _on_signal_handler(param1, param2):
    # Handle the signal when it's emitted
    print("Signal received:", param1, param2)
```
In this <span style="color:HotPink;">script</span>:

- We check if the <span style="color:Gold;">placeholder node</span> ("<span style="color:HotPink;">Placeholder</span>") exists in the <span style="color:Gold;">scene</span>
- We check if the <span style="color:HotPink;">signal</span> is already connected to avoid duplicate connections
- If the <span style="color:HotPink;">signal</span> is not connected, we connect it dynamically to the <span style="color:HotPink;">_on_signal_name</span> method

3. **Adding/Embedding <strong><span style="color:Gold;">Nodes</span></strong> at Runtime**: Whenever you add or embed <span style="color:Gold;">nodes</span> that emit the <span style="color:HotPink;">signal</span> named "<span style="color:HotPink;">signal_name</span>", this dynamic connection will ensure that your <span style="color:HotPink;">script</span> responds to those <span style="color:HotPink;">signals</span>

This way, your <span style="color:HotPink;">code</span> will be prepared to <span style="color:Gold;">connect</span> to <span style="color:HotPink;">signals</span> of <span style="color:Gold;">nodes</span> that may be added or embedded in the <span style="color:Gold;">scene</span> at a future point during runtime

---
# Subscribe to <span style="color:HotPink;">Signal</span> in a <span style="color:Gold;">Scene</span>

```python
# this is gdscript, but using python colors in this codeblock
var target_node = null # This will be the actual target node if it exists
func _ready():
# Check if the target node exists in the scene
if has_node("TargetNode"):
target_node = %NODE_UNIQUE_NAME
target_node.connect("signal_name", self, "_on_signal_name")
else:
print("TargetNode does not exist in the scene.")
func _on_signal_name(param1, param2):
pass
```

---

# Archive?
## Subscribe to a <span style="color:HotPink;">Signal</span> NOT in a <span style="color:Gold;">Scene</span> w/ UID

+ `References - No Hardcoded Paths -> Outside a Scene` (look above for more detail about <span style="color:HotPink;">Reference</span>s)
```python
# this is gdscript, but using python colors in this codeblock

# Placeholder variables for the node that has signals 
#   I want to subscirbe to. Referencing by FileSystem UID
var turnBasedBattle_node_uid = "uid://abcd1234"
var turnBasedBattle_resource = null
var turnBasedBattle_reference = null

# Called when the node enters the scene tree for the first time.
func _ready():
	# Load the target node using the UID
	turnBasedBattle_resource = load(turnBasedBattle_node_uid)
	
	# Check if the target node exists
	if turnBasedBattle_resource:
		# Instantiate the resource
		turnBasedBattle_reference = \
			turnBasedBattle_resource.instantiate()
		# Connect to the signal
		turnBasedBattle_reference.signal_character_begin_turn.connect(
				_on_signal_FUNCTION_NAME) # signal listern function name
		print("signal_character_begin_turn connected")

func _on_signal_FUNCTION_NAME(variable):
	pass
```
In this code:
1. We declare `target_node_uid` as a string variable and assign it the UID of the target node you want to connect to. Replace `"uid://da04133isku3q"` with the actual UID you want to use.
2. In the `_ready()` function, we load the target resource using `load()` based on the UID. If the resource can be loaded (i.e., it exists), we instance it to create the target node and then connect to its signal.
3. If the resource cannot be loaded (i.e., it doesn't exist or there's an issue with the UID), we handle the situation by printing an error message.
4. This code should effectively connect to the signal of the target node specified by its UID.
---

