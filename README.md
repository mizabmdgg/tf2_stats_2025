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

- ** Death **: Kills, Deaths and Assistance statistics are recorded. 
- ** Domination **: If a player kills another with a domination, he registers.
- ** Personalized death events **: events such as Headshots, Backstabs, burns, suicides, and other special events are included.
Personalized events allow you to add special scores for outstanding actions.
- ** Destruction of objects **: If a player destroys an object or construction, destruction statistics are recorded.
- ** Rounds won/losses **: The rounds won and lost by the players are recorded.

### Example of code (death events)
The plugin manages several types of events, including headshots, backstabs, burns, etc. Here is an example of the code for the death event:

#### Setting points per event
The points associated with each event can be configured in the plugin files. Example:

```plaintext
"steamdata"
{
    "Use_HUD" "0" // Disable the HUD for statistics
    "Pointsg_Playerkills" = "20" // points for killing a player
    "Pointsg_playerdeaths" = "20" // points to die
    "Pointsg_playersuicides" = "20" // points for suicide
    "Pointsg_playerheadshots" = "20" // points by Headshots
    "Pointsg_playerlevel" = "20" // points per level
    "Pointsg_dominando" = "20" // points for dominating a player
    "Pointsg_dominated" = "20" // points for being dominated
    "Pointsg_assist" = "20" // Points per attendance
    "PointsG_Roundwins" = "20" // Points to win a round
    "PointsG_Roundlose" = "20" // Points to lose a round
    "Backstabevent points" = "20" // points by backstab
    "PointsBurningevent" = "20" // Points for burn
    "Pointsuicidevent" = "20" // points for suicide
    "PointAnthadoukenevent" = "20" // points by Taunt Hadouken
    "PointsBurningflareevent" = "20" // Points for Flare Burn
    "PointAventhightNevent" = "20" // points by Tauunt High Noon
    "PointAuntgrandslamevent" = "20" // points per tant grand slam
    "Pointspenetratemyteamevent" = "20" // Points to penetrate a member of your team
    "PointspenetateheadShotevent" = "20" // Points to penetrate with Headshot
    "Pointlefragevent" = "20" // points by Telefrag
    "Pointflyingburnevent" = "20" // points to burn in flight
    "Pointspumpkinbomventvent" = "20" // points per pump pump
    "Decapitationvent points" = "20" // points for decapitation
    "PointshotgunrevenGecritevent" = "20" // Points for revenge with shotguns
    "PointsFishkillevent" = "20" // points per kill with fish
    "Point SoutantallClassguitarriffeven" = "20" // points per guitar tant
    "pointskartevent" = "20" // points per kart event
    "Pointsragonsfuryigniteevent" = "20" // points by Dragons Fury fire
    "Pointslapkillevent" = "20" // points by Slap Kill
    "AxtinguishBoosteVevent points" = "20" // Points to turn off with extinguisher
    "Pointsg_ObjectsDestroyed" = "20" // points for destroying objects
    "Pointsg_BuildingsDestroyed" = "20" // points for destroying buildings
    "Pointsg_eventsSSISted" = "20" // Points to attend at events
}

```
