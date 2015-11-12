# File: common/event.py

*You should not change this file.*

Events are actions that occur as the game is played, but may not
be represented in the objects that describe the game data.
For example, if a missile is fired, then a new missile object
will appear in the game data, but it will be hard for your
program to know that the missile is new.

Events are useful for making sounds play based on these changes in the game.
Look at [`process_event()`](client_pygame/display.md).

You can find out the kind of message received with the `get_kind()`
method.

Events Kinds
------------

## MISSILE_FIRE

When a missile is fired.

Available data in the event:

*   get_player_oid() returns the object id of the player that shot the missile
*   get_missile_oid() returns the object id of the missile that was fired
*   get_missile_range() returns the range of the missile that was fired
*   get_missile_power() returns the power of the missile that was fired

## MISSILE_MISFIRE

When a player tries to fire but doesn't have enough missile mana.

Available data in the event:

*   get_player_oid() returns the object id of the player that tried to fire the missile


## MISSILE_HIT

When a missile hits something.

Available data in the event:

*   get_player_oid() returns the object id of the player that shot the missile
*   get_missile_oid() returns the object id of the missile that hit something
*   get_target_oid() returns the object id of the object hit by the missile

## MISSILE_DYING

When a missile hits its maximum range and begins dying.

Available data in the event:

*   get_player_oid() returns the object id of the player that shot the dying missile
*   get_missile_oid() returns the object id of the missile that is dying

