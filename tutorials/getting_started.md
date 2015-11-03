# Getting Started with the Rookie Kit

## First Steps

After installing Python and PyGame on your computer. Download the rookie-kit.zip file, decompress it, and test that it is working by opening **client_pygame > main.py** and running the file.

Below is a description of all the files and folders in the rookie-kit starter files. You will do all your customizations in the "client_pygame" folder.


### client
*	`__init__.py` - Do not edit
*	`base_control.py` - Do not edit
*	`base_display.py` - Do not edit
*	`client_game_socket.py` - Do not edit
*	`pygame_game.py` - Do not edit
*	`pygame_socket_game.py` - Do not edit

### client_pygame
*	`config.py`
	*	Update `DEFAULT_GAME_TITLE` and `DEFAULT_TEAM_NAME`
	*	You may edit other values if you know what you are doing
*	**control** - The controls for your game
	*	`__init__.py` - Do not edit
	*	`control.py` - controls for your player
*	**display** - The display of your game (add images, sounds, etc here)
	*	`__init__.py` - Do not edit
	*	`display.py` - display for your game
*	`main.py` - Main game controller
	*	You should not edit this file
	*	This is the file you should run to start the game.
*	`pygame_client.py` - Do not edit

### common
*	`__init__.py` - Do not edit
*	`command_message.py` - Do not edit
*	`event_message.py` - Do not edit
*	`event.py` - Do not edit (the events of the game)
	*	**Event types and the methods for each:**
		*	`MISSILE_FIRE` - when a missile is fired
			*	`get_player_oid()` returns the object id of the player that shot the missile
			*	`get_missile_oid()` returns the object id of the missile that was fired
			*	`get_missile_range()` returns the range of the missile that was fired
			*	`get_missile_power()` returns the power of the missile that was fired
		*	`MISSILE_MISFIRE` - when a player tries to fire but doesn't have enough mana
			*	`get_player_oid()` returns the object id of the player that tried to fire the missile
		*	`MISSILE_HIT` - when a missile hits something
			*	`get_player_oid()` returns the object id of the player that shot the missile
			*	`get_missile_oid()` returns the object id of the missile that hit something
			*	`get_target_oid()` returns the object id of the object hit by the missile
		*	`MISSILE_DYING` - when a missile hits its maximum range and begins dying
			*	`get_player_oid()` returns the object id of the player that shot the dying missile
			*	`get_missile_oid()` returns the object id of the missile that is dying
*	`game_comm.py` - Do not edit
*	`game_message.py` - Do not edit
*	`game.py` - Do not edit
*	`missile.py` - Do not edit
	*	**Information methods in the MissileData class**
		*	`get_range()` how far it is able to travel
		*	`get_power()` how much damage it will cause
		*	`get_player_oid()` which player launched it
		*	`get_hit_max_range()` true if it traveled maximum range
*	`npc.py` - Do not edit
*	`object_message.py` - Do not edit
*	`object.py` - Do not edit
	*	**Information methods available for all ObjectData**
		*	`get_x()` x position
		*	`get_y()` y position
		*	`get_w()` width
		*	`get_h()` height
		*	`get_center()` (x,y) pair of center of rectangle
		*	`get_dx()` fraction of speed in the x direction
		*	`get_dy()` fraction of speed in the y direction
		*	`get_distance()` distance traveled
		*	`get_speed()` speed
		*	`get_state()` STATE_ALIVE, STATE_DYING, or STATE_DEAD
		*	`is_alive()` True if alive
		*	`is_dying()` True if dying (0 health, but not removed from game)
		*	`is_dead()` True if dead (0 health, being removed from game)
		*	`get_health()` health amount
		*	`get_max_health()` maximum health amount
		*	`get_dying_percent()` a number from 0 to 1.
			*	Each object spends 3 seconds in the "dying" state.  This tells how much of that 3 seconds has passed
		*	`get_px()` x position, rounded to nearest integer
		*	`get_py()` y position, rounded to nearest integer
		*	`get_pw()` width, rounded to nearest integer
		*	`get_ph()` height, rounded to nearest integer
		*	`get_pdistance()` distance traveled, rounded to nearest integer
*	`player.py` - Do not edit
	*	Information methods available for all PlayerData objects
		*	`get_experience()`
		*	`get_missile_range()`
		*	`get_missile_dx()`
		*	`get_missile_dy()`
		*	`get_missile_power()`
		*	`get_missile_mana()`
		*	`get_missile_mana_recharge_rate()`
		*	`get_missile_mana_max()`
		*	`get_move_mana()`
		*	`get_move_mana_recharge_rate()`
		*	`get_move_mana_max()`
*	`wall.py` - Do not edit

### engine_client
*	`__init__.py` - Do not edit
*	`game_engine.py` - Do not edit
	*	**Information methods on the game engine:**
		*	`get_player_oid()` return the object id of your player
		*	`get_opponent_oid()`  return the object id of your opponent
		*	`get_data()` return the game data object 
		*	`get_name()` return your display name
		*	`get_opponent_name()` return your opponent's display name
		*	`get_winner_name()` return the winner's name, if there is a winner
		*	`get_object(oid)` return the object identified by oid
		*	`get_objects()` return the dictionary of all objects
	*	**Action methods on the game engine:**
		*	Movement speed:
			*	`set_player_speed_stop()` stop moving
			*	`set_player_speed_slow()` move slowly, if enough mana
			*	`set_player_speed_medium()` move medium, if enough mana, and enough experience
			*	`set_player_speed_fast()` move fast, if enough mana, and enough experience
		*	Movement direction:
			*	`set_player_direction(degrees)` specify the direction to move, when you are not stopped
		*	Missile range:
			*	`set_missile_range_none()` disable missiles
			*	`set_missile_range_short()` shoot short range, at next fire
			*	`set_missile_range_medium()` shoot medium range, at next fire, if enough experience
			*	`set_missile_range_long()` shoot long range, at next fire, if enough experience
		*	Missile power:
			*	`set_missile_power_none()` disable missiles
			*	`set_missile_power_low()` shoot low power, at next fire
			*	`set_missile_power_medium()` shoot medium power, at next fire, if enough experience
			*	`set_missile_power_high()` shoot high power, at next fire, if enough experience
		*	Missile direction:
			*	`set_missile_direction(degrees)` specify the direction to fire, at next fire
		*	Missile fire:
			*	`fire_missile()` fire a missile, if enough mana for range and power combination

### engine_server
*	`__init__.py` - Do not edit
*	`config.py` - Do not edit