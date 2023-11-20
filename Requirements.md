# Requirements 

## 1. Introduction

This document specifies all functionality that should be supported by our system.

## 1.1. Purpose of the system
The systems purpose is to simulate the game world and to replicate everything relevant to other players.
## 1.2. Scope of the system
?
## 1.3. Objectives and success criteria of the project
The objective of this system is to have a stable base game simulation and network replication to easily add new weapons, enemies etc.
## 1.4. Definitions, acronyms, and abbreviations
**Game Definitions**:
- *Mage*: The mage's job is to spawn the enemies into the game world, and their goal is to eliminate the other players (*Shooters*). They see the world from a higher position and have full visibility of everything.
- *Shooters*: The shooter's job is to survive the hordes of enemies that the mages summons. The Shooters have access to a arsenal of weapons to defend themselves.
- *Mobs*: The enemies of the shooters. They get spawned by the mage and get controlled through AI.


## 1.5. References
?
## 1.6. Overview
The game is a asymmetrical survival twin-stick shooter, where one player assumes the role of the enemy spawning
## 2. Proposed system
## 2.1. Overview
As stated above, the main goal is to create a system, which acts as a foundation for all the important elements in the game. Most importantly, this means having a viable weapon architecture to easily add new content and a network foundation, which takes care of replication
## 2.2. Functional requirements

### 2.2.1 The Mage
The Mages ability allows him to spawn enemies to fight the shooters. For this the mage needs mana. Mana regenerates itself (timer).

The mages spawns mobs by first clicking on an interface and then on a spot in the world (needs enough mana to be clickable). The spot where the mobs will spawn is in a certain area around the shooter. The spawned enemies will  be spawned on all other clients and its properties will be replicated (2.2.3).

The UI allows the mage to upgrade the mobs or unlock new ones. The UI also shows the current mana of the mage.                                   

### 2.2.2 The Shooters

The shooters move around in the world, either by using a keyboard and mouse or a controller. They walk around using the WASD keys or the left joystick and look at the direction of their mouse or their right joystick. Using a button makes them shoot with their currently equiped gun.

The players information will be replicated for all clients. This includes their position, their currently active weapon etc.

Players have health, which is shown in the UI.

When a players health drop to zero, they drop to the ground, are unable to shoot and need to be revived in a certain amount of time.

### 2.2.3 The Mobs

The mobs are controlled by the computer, so they work automatically. Depending on their type, they do different actions, e.g. run towards the player, shoot the player etc.

Mob spawns will be replicated across all clients and their information as well.




### 2.2.4 The Currencies/Progression

**Cash**:

- is dropped by dead mobs
- is shown on a random spot on the UI
- is exchangeable for goods
- only collectable by shooters

**Mana**:
- is used to spawn mobs
- regenrates by itself
- is shown on the screen of the mage
- only the mage has mana

**Blood**:
- is dropped when a shooter gets damaged
- is shown on the mages UI
- exchangeable for new mobs/upgrades
- only the mage collects blood


### 2.2.5 The Weapons/Items

Weapons are the main way of the shooters to defend themselves. When shooting with a weapon, a projectile gets emitted. This is replicated on all clients. 

The idea is that all weapons follow a given architecture, so we can easily create new ones without having to do any new networking.

---

Items interact with the players stats. This means stats are recalculated when picking up an item and when throwing one away.

### 2.2.6 The Networking Architecture

The Networking Architecture keeps the networking side simple, all players are responsible for their own game logic. This means, that a client by themselves decides, whether they got hit by a projectile or dealt damage to an enemy. This keeps the networking simple and allows us to do easy unit testing.

This simple architecture is possible because of the game type. There is no direct combat between players, so they won't feel any lag or unfair hits.


## 2.3 Nonfunctional requirements
## 2.3.1. User interface and human factors
The biggest part of the users vision is the game world, so they can have the most vision of the action.

On small UI widgets, the player can see their current currencies, their weapons and other useful information.
## 2.3.2. Documentation
There is a documentation for commonly used functionality, e.g. the weapons interface. Also docs for the network API.
## 2.3.3. Hardware considerations
The user is able to decide between keyboard and mouse and a controller
## 2.3.4. Performance characteristics
The game runs with at least 60 fps. There will be no stuttering during the action.
## 2.3.5. Error handling and extreme conditions
There will be Unit tests, which test the most commenly operations. This is achievable through the simple networking.
## 2.3.6. Quality issues
(to #1 functional):  The timespan in which the mobs show on all other clients relies on the outer conditions but has to be within 200 milliseconds.  (to #2 functional): When the hitboxes of the shooter and a mob collide , the shooter receives a fixed amount of damage which is displayed on the UI.
(to #3 functional): Different types of mobs result in differences in walking / running speed and also in the fix amount of damage they deal when colliding with hitbox of shooter.
(to #4 functional): When killing mobs (cash) or when damaging the shooter (blood) the currencies will only be dropped for an amount relative to the players health.
(to #5 functional): Shooting rate relies on game engine. There will be a general weapon Interface which specifies characteristics about the weapon eg. Bullet-Node.
(to #6 functional): The networking aspects of this game are heavily assisted by the game engine.
## 2.3.7. System modifications
?
## 2.3.8. Physical environment
?
## 2.3.9. Security issues
?
## 2.3.10. Resource issues
?
## 2.4. Pseudo requirements
The game should be fun.
## 2.5. System models
The models can be found [here](https://github.com/Neckar-Code-Collective/Design-Docs)
## 2.5.1. Scenarios
Either all shooters die and the mage wins or the endboss gets beaten and the shooters win
## 2.5.2. Use case model
## 2.5.3. Object model
## 2.5.3.1. Data dictionary
## 2.5.3.2. Class diagrams
## 2.5.4. Dynamic models
## 2.5.5. User-interface -- navigational paths and screen mock-ups
The UI should look similar to the one in League of Legends

## 3. Glossary
