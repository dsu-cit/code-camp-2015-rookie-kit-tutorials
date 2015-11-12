# File: engine&#95;client/game&#95;engine.py

*You should not change this file.*

This file describes the methods that are available to be
called on the `engine` object.  Some allow you to
obtain information about the game state.  Others allow you
to send action requests to the server.

Editing this file will *NOT* change the game.  It will *BREAK*
your program.


## Information methods on the game engine

These methods fetch information about the game state.

*   `get_player_oid()` return the object id of your player.
    Useful in combination with get_object to fetch your
    player object.
*   `get_opponent_oid()`  return the object id of your opponent.
    Useful in combination with get_object to fetch your
    opponent's player object.
*   `get_data()` return the game data object .
*   `get_name()` return your display name.
*   `get_opponent_name()` return your opponent's display name.
*   `get_winner_name()` return the winner's name, if there is a winner.
*   `get_object(oid)` return the object identified by `oid`.
    See [object documentation](../common/object.md).
*   `get_objects()` return the dictionary of all objects.


## Action methods on the game engine:

These methods ask the server to make a change to
the game.  Note that the server doesn't always
make the change.  Experience points and mana
are required for most actions.

### Movement speed:

These are the possible speed settings.  If the
player is not stopped, it will try to move.
If the movement mana reaches 0, the server
will automatically set the player speed to stop.
Faster speeds consume more movement mana than
slower speeds.

*    `set_player_speed_stop()` stop moving.
*    `set_player_speed_slow()` move slowly, if enough mana.
*    `set_player_speed_medium()` move medium, if enough mana, and enough experience.
*    `set_player_speed_fast()` move fast, if enough mana, and enough experience.


### Movement direction:

This method controls the direction the
player will try to move, if it is not stopped.
The most recent call to this function controls
the direction.

Note that because the display
has y increasing in the down direction, an angle
of 90 is down.

*    `set_player_direction(degrees)` specify the direction to move, when you are not stopped.

###  Missile range:

The range of the missile is controlled with these methods.
Note that the most recent call to one of these functions
controls the range of a fired missile.
Higher ranges consume more missile mana than
lower ranges.

*    `set_missile_range_none()` disable missiles.
*    `set_missile_range_short()` shoot short range, at next fire.
*    `set_missile_range_medium()` shoot medium range, at next fire, if enough experience.
*    `set_missile_range_long()` shoot long range, at next fire, if enough experience.


###  Missile power:

The power of the missile is controlled with these methods.
Note that the most recent call to one of these functions
controls the power of a fired missile.
Higher powers consume more missile mana than
lower powers.  Higher powers cause more damage than
lower powers.

*    `set_missile_power_none()` disable missiles
*    `set_missile_power_low()` shoot low power, at next fire
*    `set_missile_power_medium()` shoot medium power, at next fire, if enough experience
*    `set_missile_power_high()` shoot high power, at next fire, if enough experience


###  Missile direction:

This method controls the direction fired missiles
will move.
The most recent call to this function controls
the direction.

Note that because the display
has y increasing in the down direction, an angle
of 90 is down.

*    `set_missile_direction(degrees)` specify the direction to fire, at next fire.

###  Missile fire:

This method will fire a missile.  However, the range and
power must not be none, and the required missile mana must
be available.  The missile mana will be reduced when the
missile fires.

*    `fire_missile()` fire a missile, if enough mana for range and power combination.


