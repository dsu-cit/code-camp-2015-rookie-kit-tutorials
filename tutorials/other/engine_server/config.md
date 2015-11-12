# File: engine_server/config.py

### *You should not change this file.*

This file describes various constant values that are
used by the game server.  You can use the values
in here to control features in your program.

Editing this file will **NOT** change the game.


## Object Sizes

These sizes are important if you want to replace the
rectangles with images.  You must make your images
the correct size for the game to be displayed correctly.

* `PLAYER_WIDTH`  width of the player objects
* `PLAYER_HEIGHT` height of the player objects
* `WALL_THICK` width and height of wall objects
* `NPC_WIDTH` width of npc objects
* `NPC_HEIGHT` height of npc objects
* `MISSILE_WIDTH` width of missile objects
* `MISSILE_HEIGHT` height of missile objects

## Field Size

These describe the size of the field.

* `FIELD_WIDTH` width of the playing field
* `FIELD_HEIGHT` height of the playing field

## Maximum Health Values

These describe the maximum amount of health different
objects have.  Objects can take damage, which reduces
their current health.  If current health reaches
0, they die.

* `HEALTH_MISSILE` health of missiles.
* `HEALTH_NPC`     health of npcs
* `HEALTH_PLAYER`  health of players
* `HEALTH_WALL`    health of walls


## Experience Levels

These describe the total number of experience points
required to obtain various power ups for the
player.

* `XP_LEVELS[XP_LEVEL_0]`
* `XP_LEVELS[XP_LEVEL_SPEED_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_MISSILE_MANA_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_RANGE_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_MOVE_MANA_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_POWER_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_MOVE_MANA_RECHARGE_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_MISSILE_MANA_RECHARGE_MEDIUM]`
* `XP_LEVELS[XP_LEVEL_SPEED_FAST]`
* `XP_LEVELS[XP_LEVEL_MISSILE_MANA_HIGH]`
* `XP_LEVELS[XP_LEVEL_RANGE_LONG]`
* `XP_LEVELS[XP_LEVEL_MOVE_MANA_HIGH]`
* `XP_LEVELS[XP_LEVEL_POWER_HIGH]`
* `XP_LEVELS[XP_LEVEL_MOVE_MANA_RECHARGE_FAST]`
* `XP_LEVELS[XP_LEVEL_MISSILE_MANA_RECHARGE_FAST]`


## Player Speeds

These describe the speed levels for available for the player.
Remember that the player must obtain the required experience
points to activate the speed.  Values are in pixels per second.

* `PLAYER_SPEED_STOP[0]`
* `PLAYER_SPEED_SLOW[0]`
* `PLAYER_SPEED_MEDIUM[0]`
* `PLAYER_SPEED_FAST[0]`

## Missile Ranges

These describe the missile distance levels available for
the player.
Remember that the player must obtain the required experience
points to activate the range.  Values are in pixels.

* `MISSILE_RANGE_NONE[0]`
* `MISSILE_RANGE_SHORT[0]`
* `MISSILE_RANGE_MEDIUM[0]`
* `MISSILE_RANGE_LONG[0]`

## Missile Speed

This is the speed of the missile.  It is in pixels per second.
There is only one missile speed.

* `MISSILE_SPEED`

## Missile Powers

These describe the missile power levels available for
the player.
Remember that the player must obtain the required experience
points to activate the power.  Values are in health points.

* `MISSILE_POWER_NONE[0]`
* `MISSILE_POWER_LOW[0]`
* `MISSILE_POWER_MEDIUM[0]`
* `MISSILE_POWER_HIGH[0]`

## Dying Time

This describes the number of seconds that an object
will be available for display after its health
reaches 0.  This is mainly used to animate a
death sequence.

* `DYING_TIME`


## Game Over Time

This describes the number of seconds that the game
over screen is available before the game goes
back to the pre-game screen.

* `GAME_OVER_TIME`



