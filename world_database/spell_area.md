### Source Ref: https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130105/spell+area

```
This table is used to apply a specific spell aura to the player within an area in the game. When any player enters this area or somehow interacts with a quest, this aura will be handled accordingly.

Some examples:

An area could pacify all players (spell 39331)
Another area could full heal every 1 second (spell 48591)
Teleport player out of an area (spell 53141)
Factions-specific buffs, e.g. in Icecrown Citadel:
"Hellscream's Warsong" (spell 73822) for horde 
"Strength of Wrynn" (spell 73828) for alliance
Even region-based buffs, such as area 440 - Tanaris.

```

Example for fix quest: https://www.wowhead.com/quest=31708/serpents-scale#comments

While sniff work perfectly for NPC quest ender: https://www.wowhead.com/npc=65672/your-cloud-serpent ( which add aura to this NPC `ID - 94223 Generic Quest Invisibility 25` )
You won't able to see it unless GM On. So spell 94223 require aura `ID - 103059 Generic Quest Invisibility Detection 25` to able see the NPC.
Also quest 31708 require quest 30142 complete before take that quest. 
Complete fix will be:
```
INSERT INTO spell_area(spell, `area`, quest_start, quest_end, aura_spell, racemask, gender, autocast, quest_start_status, quest_end_status) VALUES 
(103059, 5931, 30142, 0, 0, 0, 2, 1, 64, 11);
```

While quest_start_status = 64 ( QUEST_STATUS_REWARDED = 6, 64, Player handed quest in and this is sort of a post-quest interaction )
``` 
From Link:
"quest_start_status" means that the quest has to be in the state you put in that field in order to add the spell from the first field. 
This table is not only used for phasing.
```

Other example from TC:
```
Area 257 is a cavern on Teldrassil. What we want is simple : When the player take the 28725 quest, he have the aura in the cavern. When he finish the 28727 quest, the aura disappear.

You should have the spell 92237 when entering the cavern IF :

    The start quest 28725 is incomplete, complete or rewarded (2 | 8 | 64 = 74)

    The end quest 28727 is not taked (none), incomplete or complete BUT not rewarded (1 | 2 | 8 = 11)

Here is the SQL for this example : 

INSERT INTO spell_area (spell, area, quest_start, quest_end, autocast, quest_start_status, quest_end_status) VALUES (92237, 257, 28725, 28727, 1, 74, 11);

```
