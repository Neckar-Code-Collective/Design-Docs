# Components for the game

The following components/nodes should be created for the game:

## Movement Component
The MovementComponent is responsible for using the input the players provides and using it on the local player object.

## Health Component
The healthcomponent is responsible for keeping track of a entities health, applying damage and notifying on death (health <= 0).

The functions should include getting the current health and health regeneration, setting these values, applying damage.

This component should expose signals for when the entity gets damaged, healed and killed.

The Healthcomponent should broadcast its state to all clients and have a boolean switch for a puppet mode.

## Weapon Component
The Weaponcomponent acts as a blueprint for all weapons. It exposes functions and signals that are used for all weapons, which are the following:

The component should have a function, which gets called on other clients, which spawns a puppet bullet on their machine

There should be signals for when a projectile gets emitted.

## Bullet Component
The Bulletcomponent holds information about a bullet. Bullets should know the damage they have to apply, their owner, their remaining lifetime etc.

It also needs a boolean switch for puppet mode.
