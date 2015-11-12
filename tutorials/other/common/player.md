# File: common/player.py

There are two player objects in the game.  Your player
and your opponent.  Players have all of the functionality
of [object](object.md)s, plus, the features listed below.

Do not make changes to this file.  You will break
your program if you do.


Information methods available for all PlayerData objects
--------------------------------------------------------

* `get_experience()` - The current number of experience points.
  Experience points are used to make power ups available.
* `get_missile_range()` - The current missile range setting.
* `get_missile_dx()` - The horizontal part of the current
  missile direction setting.
* `get_missile_dy()` - The vertical part of the current
  missile direction setting.
* `get_missile_power()` - The current missile power setting.
* `get_missile_mana()` - The current amount of missile mana available.
* `get_missile_mana_recharge_rate()` - How fast missile mana is recharging.
* `get_missile_mana_max()` - The maximum amount of missile mana that can be stored.
* `get_move_mana()` - The current amount of movement mana available.
* `get_move_mana_recharge_rate()` - How fast movement mana is recharging.
* `get_move_mana_max()` - The maximum amount of movement mana that can be stored.

