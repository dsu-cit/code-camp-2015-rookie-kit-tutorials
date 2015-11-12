# The Rookie Kit Game

The game is a two player battle.  It's you against an
opponent.  Both players start with the same health
levels, and the same abilities.  Each player can move
around the world and shoot missiles.  There are walls
around the world that prevent escape.  There are also
small obstacles on the field that block movement and
missiles.  There are non-player characters (NPCs)
that move around the field.  The winner is the first
player to destroy their opponent by causing its health
to reach 0.

## Mana

Each player has an amount of movement mana.  As the player moves,
mana is consumed.  If movement mana reaches 0, the player will be
stopped.  Movement mana automatically recharges over time.

Each player has an amount of missile mana.  As the player fires
missiles,  mana is consumed.  If missile mana reaches 0, the player
will not be able to fire missiles.  Missile mana automatically
recharges over time.

Smart players manage their mana level to make sure they don't
run out at critical times.


## Experience Points

Experience points are awarded to a player every time one
of its missiles cause damage to another player, NPC, or missile.
Experience points are used to provide power ups.  As the power ups
are achieved, the player is allowed to move faster, shoot further,
shoot with more powerful missiles, recharge mana more quickly,
and store more mana.

Smart players try to accumulate experience points faster than
their opponent to obtain an advantage.


## Player Movement

Each player can move in any direction, as long as there is
no wall, NPC, or other player in the way.

Each player can move at 4 different speeds:  stop, slow, medium,
and fast.  Faster movement consumes more mana than slower movement.

Smart players will
keep an eye on mana levels and stop and rest to allow mana to
recharge.  


## Missile Range

When the player fires a missile, the missile will be configured
to travel up to a maximum range.

Missiles can be configured for one of four ranges:
none, short, medium, or long.  Longer ranges use more
mana than shorter ranges.

Smart players will fire missiles at the smallest range
that will hit their target.  They also don't charge into
battle with low mana levels.


## Missile Power

When the player fires a missile, the missile will be configured
with an amount of explosives to cause damage.

Missiles can be configured for one of four powers:
none, low, medium, or high.  Higher powers use more
mana than lower powers.

Smart players will fire missiles at the smallest power
that will destroy their target.


## Missile Direction

Missiles can be fired in any direction.


## Missile Speed

All missiles travel at the same speed.


## Missile Count

Missiles are unlimited.  Missile mana, however,
is limited.
