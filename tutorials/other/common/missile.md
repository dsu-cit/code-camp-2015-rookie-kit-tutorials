# File: common/missile.py

There are can be many missile objects in the game, depending
on how many shots the players are taking.  
Missiles have all of the functionality
of [object](object.md)s, plus, the features listed below.

*	`get_range()` how far it is able to travel.
*	`get_power()` how much damage it will cause, if it hits something.
*	`get_player_oid()` the object id of the player that launched it.
*	`get_hit_max_range()` True if it traveled maximum range.  Usually,
        this will be a dying object.


