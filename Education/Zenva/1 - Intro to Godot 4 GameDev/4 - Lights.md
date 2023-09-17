#lights #lighting
* Light is a node
	* Can change Color (like blue) of the light
	* Energy is for intensity / brightness
	* Enable the `Shadow` if you want this light to cast a **shadow**

* In 3D, you have 3 options:
	1. <span style="color:tomato;">DirectionalLight3D</span>
		* Light pointing in a certain direction
	2. <span style="color:tomato;">OmnitLight3D</span>
		* You get a sphere
		* It emits light from a source (center) in all directions till the sphere
			* Think of a **lightbulb / candle**
		* Also has a `Range` field you can modify
	3. <span style="color:tomato;">SpotLight3D</span>
		* Emits light in a cone
		* Good for **headlights / streetlights / torch**
		* Can change range / width of cone

