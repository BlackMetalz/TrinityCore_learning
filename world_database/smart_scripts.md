### Basic Hook on Gossip Hello ( remember to set npcflag +=1 for gossip flag )
```
DELETE FROM `smart_scripts` WHERE (`entryorguid`=68370 AND `source_type`=0);
INSERT INTO `smart_scripts` (`entryorguid`, `source_type`, `id`, `link`, `event_type`, `event_phase_mask`, `event_chance`, `event_flags`, `event_param1`, `event_param2`, `event_param3`, `event_param4`, `action_type`, `action_param1`, `action_param2`, `action_param3`, `action_param4`, `action_param5`, `action_param6`, `target_type`, `target_param1`, `target_param2`, `target_param3`, `target_x`, `target_y`, `target_z`, `target_o`, `comment`) VALUES 
(68370, 0, 0, 0, 64, 0, 100, 1, 0, 0, 0, 0, 33, 68722, 0, 0, 0, 0, 0, 7, 0, 0, 0, 0, 0, 0, 0, "On Gossip Hello, Give Quest Credit");
```
![image](https://user-images.githubusercontent.com/3434274/123000661-0e3ad500-d3da-11eb-9de7-dc1709fdae46.png)
