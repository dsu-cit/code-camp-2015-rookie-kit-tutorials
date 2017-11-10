# Play sound when missile fires

If you haven't already read up on [how to load and play sound files](../sounds/adding_sound_effects.md), you should do that first.

There are many events that occur in the game, and you can use those events to make sounds, change the display, etc. In this tutorial, we examine how to have an action occur when a missile is fired.  The location for this is in the `display/display.py` file in the `process_event` method.  You can check the type of event that has occurred with `event.get_kind()`.  If the kind of event is `E_MISSILE_FIRE`, then you could take an action, such as playing a sound.

There are several types of events:

* E_MISSILE_FILE    - a missile was just fired
* E_MISSILE_MISFIRE - a player tried to fire, but did not have enough missle mana
* E_MISSILE_HIT     - a missile just hit something
* E_MISSILE_DYING   - a missile has reached its maximum range, and is going away



