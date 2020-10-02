# Lunar-Base-Camp-SIM
# Example code for NASA VIPER movementon moon
#Move to left mouse click
extends KinematicBody2D
export (int) var speed = 18
#var velocity = Vector2.ZERO
var target = Vector2()
var velocity = Vector2()
onready var sprite : Sprite = get_node("Sprite")
func _input(event):
	if event.is_action_pressed('find'):
		target = get_global_mouse_position()

func _physics_process(delta):
	velocity = position.direction_to(target) * speed
	# look_at(target)
	if position.distance_to(target) > 5:
		velocity = move_and_slide(velocity)
	if velocity.x < 0:
		sprite.flip_h = false
	elif velocity.x > 0:
		sprite.flip_h = true
