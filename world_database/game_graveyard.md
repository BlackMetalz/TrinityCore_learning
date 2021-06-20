# Note for not going to google over over again
- Source: https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130148/graveyard+zone


```
The `graveyard_zone` table

Contains information about zones connected to world's graveyards.

This table is used to set what factions a given graveyard will accept, and also to specify the nearest graveyard to a given zone.

For a list of all existing graveyard zones and their respective IDs, check out WorldSafeLocs.dbc

Description of the fields

ID
Graveyard's ID. See WorldSafeLocs.dbc

GhostZone
Zone's Id of ghost position before teleportation to graveyard. See AreaTable.dbc

Faction
Graveyard's team.

0 - Any team accepted

469 - Alliance team only

67 - Horde team only
```

WorldSafeLocs.dbc can get from your DBC or here: https://wow.tools/dbc/?dbc=areatable&build=5.4.7.18019#page=1&search=Tanaris
AreaTable.dbc can get from your DBC or here: https://wow.tools/dbc/?dbc=worldsafelocs&build=5.4.8.18273#page=1&search=5723

## Example:
- Bug: Die in Mount Hyjal and being teleport to Tanaris?
- Information need to collect: WorldSafeLocs and AreaTable
+ WorldSafeLocs: https://wow.tools/dbc/?dbc=worldsafelocs&build=5.4.8.18273#page=1&search=Mount%20Hyjal . All ID from 1741,1742,1743,1744,1755
+ AreaTable: https://wow.tools/dbc/?dbc=areatable&build=5.4.7.18019#page=1&search=Mount%20Hyjal. ID: 616

What is wrong here. When i do select into game_graveyard table, I see a record which is should not been there
```
id   ghost_zone
1249 616
```
What is 1249? https://wow.tools/dbc/?dbc=worldsafelocs&build=5.4.8.18273#page=1&search=Tanaris 1249 is where i get teleported to ( Tanaris - Cavern of Time Graveyard )

- Solution: Simple to remove that record then do reload ingame. Die again and see yourself teleport Mount Hyjal, not Tanaris!

https://wow.tools/ is awesome sites!
