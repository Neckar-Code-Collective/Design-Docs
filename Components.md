# Components for the game

These are just the foundational Components, so these should be created directly at the beginning and are held very generic.

The following components/nodes should be created for the game:

## Player Component
The Playercomponent makes up most of the logic of the player.

It holds the information about the player, their stats and holds their weapons. Due to its complexity, it should probably be broken down in a logical and a visual part.

# Mage Component

The Mage component holds all the logic of the mage.

its job is to keep track of mana (incrementing etc.) and to hold the information
for spawnable mobs (e.g. which mobs the mage can spawn)

Its should provide a clean interface to access mana and modify its data.
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

## NetworkedTransform Component

The Networkedtranform Component is responsible for syncing the position and rotation of a gameobject. it also applies lerping to smooth movement.

This should be pretty easy to implement thanks to godots property replication system.

*note*: animation of an entity is handled by the entity bas class 