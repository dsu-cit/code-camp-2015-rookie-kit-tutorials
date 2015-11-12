# File: common/event.py

*You should not change this file.*

This file handles different events. Currently the `kind` of events created
are missile events including: `E_MISSILE_FIRE`, `E_MISSILE_MISFIRE`, `E_MISSILE_HIT`, and `E_MISSILE_DYING`.

Events are actions that occur as the game is played, but may not
be represented in the objects that describe the game data.
For example, if a missile is fired, then a new missile object
will appear in the game data, but it will be hard for your
program to know that the missile is new.

Events are useful for making sounds play based on these changes in the game.
Look at [`process_event()`](../client_pygame/display.md).


## Notable Event Methods

### `get_kind()`

Returns the `kind` or type of event the event is. One you have this, you can check if it is one of the following listed below and use the appropriate methods.


## E&#95;MISSILE&#95;FIRE

E&#95;MISSILE&#95;FIRE events occur when a missile is fired. Its methods include:

*   `get_player_oid()` returns the object id of the player that shot the missile
*   `get_missile_oid()` returns the object id of the missile that was fired
*   `get_missile_range()` returns the range of the missile that was fired
*   `get_missile_power()` returns the power of the missile that was fired



## E&#95;MISSILE&#95;MISFIRE

E&#95;MISSILE&#95;MISFIRE events occur when a player tries to fire but doesn't have enough mana (ie not enough bullets). Its methods include:

*   `get_player_oid()` returns the object id of the player that tried to fire the missile



## E&#95;MISSILE&#95;HIT

E&#95;MISSILE&#95;HIT events occur when a missile hits something (wall, npc, player, or bullet). Its methods include:

*   `get_player_oid()` returns the object id of the player that shot the missile
*   `get_missile_oid()` returns the object id of the missile that hit something
*   `get_target_oid()` returns the object id of the object hit by the missile



## E&#95;MISSILE&#95;DYING

E&#95;MISSILE&#95;DYING events occur when a missile hits its maximum range and begins dying (missile misses completely). Its methods include:

*   `get_player_oid()` returns the object id of the player that shot the dying missile
*   `get_missile_oid()` returns the object id of the missile that is dying



## Example Usage

	event_kind = event.get_kind()

	if event_kind == E_MISSILE_FIRE:
		player_oid = event.get_player_oid()
		player_object = engine.get_object(player_oid)
		missile_oid = event.get_missile_oid()
		missile_object = engine.get_object(missile_oid)

		# Stuff you want to do when a missile is fired
		# ie Play Sound or some other cool feature.

	elif event_kind == E_MISSILE_MISFIRE:
		# do some cool action when a player fires a missile without enough mana.

	elif event_kind == E_MISSILE_HIT:
		# do some cool action when a missile hits an object. Maybe some kind of sound effect?

	elif event_kind == E_MISSILE_DYING:
		#do some cool action when a missile misses an object or runs out of range too early.

