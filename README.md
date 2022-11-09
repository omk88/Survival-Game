# Survival Game Prototype

## Features:

## Player movement system.



## Random generation of trees, rocks and berry bushes on terrain.

Spawn points are selected on the terrain during runtime by generating random X and Z co-ordinates, then the terrain is sampled for its height value which is set to the Y value, and a tree, rock or berry bush is generated at that position. This means a random set of trees/rocks/berry bushes is generated each time.

![Random Generation](https://user-images.githubusercontent.com/46501575/200926357-e762a373-f4dd-4090-96d9-cfc30bdefb01.png)

## Axe and pickaxe equipment system.

When the player first enters the game, they have the ability to pick up an axe or pickaxe by pressing the "E" key. Doing so will "equip" the item, meaning the model of the item on the floor will be destroyed and an animated first person version will be enabled in the game hierarchy which is attached to the player. The axe and pickaxe both have idle and swing animations that are triggered by idling or clicking the left mouse button, using a script. Picking up an axe/pickaxe will add the respective item to the players inventory. The player also has the ability to drop the axe/pickaxe by pressing F. This will instantiate a new item model on the floor and disable the first person view of that item.

## Tree/rock destruction and item collection system.

All trees and rocks spawned in the game can be broken, provided the player has equipped the correct tool. For instance, trees can only be broken if the player has an axe equipped, rocks can only be broken if the player has a pickaxe equipped. Once a tree or rock has been broken an item is dropped that the player can pick up by pressing "E" (rocks have to broken multiple times to drop items). Once a player picks up an item, the tag of that item is then added to the inventory system. Berries can be picked up simply by pressing "E". This is done by using a raycast and tagging gameobjects to distinguish between different objects in the game and storing health values for each tree/rock which are decreased when the player clicks on them. Once the health reaches zero, that gameobject is destroyed and an item object is instantiated in its place.

## Inventory system and inventory UI.

Picked up items are added to a list which stores the tags of each item that has been picked up. A UI to display these values is enabled in the hierarchy when the player presses the "I" key, which also disables scripts for movement and camera control. These can be re-enabled, along with disabling the UI element when the user presses "I" once more. The inventory UI will look through the inventory list when it is opened, and instantiate UI icons (at the moment they are just different coloured squares) in different positions relative to available slots in the inventory. Put simply, this means the player is able to open an inventory by pressing "I", which logs current items that have been gathered.

## Day/Night system and enemy spawning.

The time of day slowly progresses as the player plays the game. This is done by altering the values of the directional light in the scene and using a lighting preset to make the scene appear as though it is a different time of day. We also log the time of day with a variable, and use it to determine whether or not to enable the "EnemySpawner" gameobject, which contains a script to select random points - relative to the player - to spawn enemy gameobjects. The enemy spawner is enabled during the night and disabled at sunrise, along with destroying all enemy gameobjects. Effectively this means that there is a day and night system, which spawns enemies at night, and despawns them at sunrise.
