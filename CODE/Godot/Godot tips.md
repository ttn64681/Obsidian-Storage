# Basic Concepts
## Signals
1. Via Automatically in Editor
2. Custom Signals: Via Manual Code

```
# Player.gd
extends CharacterBody2D

signal health_changed(new_health)

var health = 100

func take_damage(amount):
	health -= amount
	health = max(0, health) # Don't let health go below 0
	
	# Emit the signal to notify anyone who is listening (via connect()).
	health_changed.emit(health)
```

## Singleton (Autoload)
- Singleton: script/scene that is only instantiated once
- Autoload Singleton: script or scene that is **always available globally**
	- For managing score, player inv, game state, etc.

```
# GameManager.gd
extends Node

var score = 0
var player_name = "Hero"

func add_score(points):
	score += points
	print("New score is: ", score)

func reset_game():
	score = 0
```

```
# AnyOtherScript.gd

func _on_player_hit_checkpoint(): # You can access its variables directly. print(GameManager.player_name, " reached a checkpoint!")
```

## 2D Character Movement
- For physics-based characters, Godot's `CharacterBody2D` node is the best tool
	- has built-in func: `move_and_slide()` that handles collisions for you

```
# PlayerMovement.gd
extends CharacterBody2D

# Speed in pixels per second
@export var speed = 300.0

func _physics_process(delta):
	# Get input from arrow keys or WASD
	# returns direction vector, e.g., (1, 0) for right
	var direction = Input.get_vector("ui_left", "ui_right", "ui_up", "ui_down") 
	
	# Set the velocity. velocity = direction * speed 
	
	# moves the character and handles # sliding along walls if there's a collision.
	move_and_slide()
```

## NavigationAgent2D and Pathfinding
**Scene Setup:**
- Walkable Area: Create `NavigationRegion2D` node. Add a `NavigationPolygon2D` child to it.
	- In toolbar above viewport, use polygon tool to "draw" the areas where AI can walk
- AI Character: The AI character scene (e.g., a `CharacterBody2D`) needs a NavigationAgent2D node as a child

```
# EnemyAI.gd
extends CharacterBody2D

@export var speed = 150.0

# Get reference to NavigationAgent2D node.
@onready var nav_agent: NavigationAgent2D = $NavigationAgent2D

func _ready():
	# Set target location you want the AI to move to.
	# For example, the player's position.
	nav_agent.target_position = get_node("/root/Game/Player").global_position

func _physics_process(delta):
	# If agent hasn't reached its destination yet...
	if not nav_agent.is_navigation_finished():
		# Get the next point on the calculated path.
		var next_path_position = nav_agent.get_next_path_position()
		
		# Get the direction from the AI's current position to that next point.
		var direction = global_position.direction_to(next_path_position)
		
		# Move towards that point.
		velocity = direction * speed
		move_and_slide()
```

<hr>
# Basic Cheatsheet
## Var types
- var cursor_sprite: Sprite2D

## Functions
### Built-in:
- 
- max(0, health) # won't let health go under zero



<hr>
# Code Snippets
## Manual Animation:
```
@onready var cursor: Sprite2D = $Cursor

var current_frame: float = 5.3:
    set(value):
        current_frame = value # redundant
        # frame # never goes below 0 or above 5.3
        current_frame = clamp(current_frame, 0, 5.3) 

func _ready():
    Input.set_mouse_mode(Input.MOUSE_MODE_HIDDEN)
    cursor.frame = current_frame
  
func _process(delta):
    cursor.frame = int(current_frame - 0.1)
    cursor.global_position = get_global_mouse_position()
```




**Custom Signals:**

- **slot_clicked(slot_index: int)**
	- Emitted in: _inventory_slot_ui.gd_
		- slot_clicked.emit(slot_index)
	- Received in: _inspect_state.gd_
		- slot_ui.slot_clicked.connect(_on_inventory_slot_clicked)
	- Handler:
		- _on_inventory_slot_clicked(slot_index: int)

**Prebuilt Signals:**

- Emitted in: _inventory_slot_ui.gd (clicking inventory_slot_ui.tscn)_
	- gui_input(event: InputEvent)
- Received in: _inventory_slot_ui.gd_
	- gui_input.connect(_on_gui_input)
- Connected in:
	- _on_gui_input(event: InputEvent)

