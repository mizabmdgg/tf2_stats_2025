<div align="center">
  <h1><code>tf2_stats_2025</code></h1>
  <p>
    <strong>Fork of tf2_stats_2025 by gladoncio</strong>
  </p>
</div>

# TF2 Stats Plugin (Beta)

This plugin is currently under development. The idea is to create a statistics system next to a level system.

## Requirements
- Sourcemod and Metamod
- SQLite/MySQL/MariaDB

## Installation
1. Download the latest version from the release page and break it on your sourcemod folder.

## Configuration
- Once the plugin is loaded, you can modify the specifications in `addons/sourcemod/config/Playerstats.cfg`.
- To configure points per type of map, prefixes, etc., you can edit `Addons/Sourcemod/Conf/PlayerstatsMaps/vsh_.cfg`.
- Configure the points by type of event in `Addons/Sourcemod/Conf/Playerlevels.cfg`.
- To enable mysql, Be sure to configure the database in `Addons/Sourcemod/Conf/Databases.cfg`:

```json
"playerstats"
{
	"driver"		"mysql"
	"host"			"localhost"
	"database"		"steamdata"
	"user"			"root"
	"pass"			""
	//"timeout"		"0"
	//"port"		"0"
}
```

## Usage (Beta)
This plugin is still in beta. Currently ** does not keep all statistics **, however, it represents a great advance since the last update.

### Statistics events
The plugin records the following death and destruction events, assigning points according to the type of event. These points are configurable in plugin configuration files:

- **Death**: Kills, Deaths and Assistance statistics are recorded. 
- **Domination**: If a player kills another with a domination, he registers.
- **Personalized death events**: events such as Headshots, Backstabs, burns, suicides, and other special events are included.
Personalized events allow you to add special scores for outstanding actions.
- **Destruction of objects**: If a player destroys an object or construction, destruction statistics are recorded.
- **Rounds won/losses**: The rounds won and lost by the players are recorded.

### Example of code (death events)
The plugin manages several types of events, including headshots, backstabs, burns, etc. Here is an example of the code for the death event:

#### Setting points per event
The points associated with each event can be configured in the plugin files. Example:

```plaintext
"steamdata"
{
    "use_hud" "0"  // Disables HUD for statistics
    "puntosg_PlayerKills" = "20"  // Points for killing a player
    "puntosg_PlayerDeaths" = "20"  // Points for dying
    "puntosg_PlayerSuicides" = "20"  // Points for suicide
    "puntosg_PlayerHeadshots" = "20"  // Points for headshots
    "puntosg_PlayerLevel" = "20"  // Points for level
    "puntosg_dominando" = "20"  // Points for dominating a player
    "puntosg_dominado" = "20"  // Points for being dominated
    "puntosg_assist" = "20"  // Points for assist
    "puntosg_roundWins" = "20"  // Points for winning a round
    "puntosg_roundLose" = "20"  // Points for losing a round
    "puntosbackstabEvent" = "20"  // Points for backstab
    "puntosburningEvent" = "20"  // Points for burning
    "puntossuicideEvent" = "20"  // Points for suicide
    "puntostauntHadoukenEvent" = "20"  // Points for Hadouken taunt
    "puntosburningFlareEvent" = "20"  // Points for flare burning
    "puntostauntHighNoonEvent" = "20"  // Points for High Noon taunt
    "puntostauntGrandSlamEvent" = "20"  // Points for Grand Slam taunt
    "puntospenetrateMyTeamEvent" = "20"  // Points for penetrating a teammate
    "puntospenetrateHeadshotEvent" = "20"  // Points for penetrating headshot
    "puntostelefragEvent" = "20"  // Points for telefrag
    "puntosflyingBurnEvent" = "20"  // Points for burning while flying
    "puntospumpkinBombEvent" = "20"  // Points for pumpkin bomb
    "puntosdecapitationEvent" = "20"  // Points for decapitation
    "puntosshotgunRevengeCritEvent" = "20"  // Points for shotgun revenge crit
    "puntosfishKillEvent" = "20"  // Points for fish kill
    "puntostauntAllclassGuitarRiffEven" = "20"  // Points for guitar taunt
    "puntoskartEvent" = "20"  // Points for kart event
    "puntosdragonsFuryIgniteEvent" = "20"  // Points for Dragon's Fury ignite
    "puntosslapKillEvent" = "20"  // Points for slap kill
    "puntosaxtinguishBoosterEvent" = "20"  // Points for extinguisher boost
    "puntosg_ObjectsDestroyed" = "20"  // Points for destroying objects
    "puntosg_BuildingsDestroyed" = "20"  // Points for destroying buildings
    "puntosg_EventsAssisted" = "20"  // Points for assisting in events
}

```
