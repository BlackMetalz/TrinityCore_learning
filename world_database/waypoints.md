- I'm lazy to write for specific core. But here it is.

```
SET @GUID := NPC_GUID;
SET @PATH := @GUID * 10;
UPDATE `creature` SET `MovementType`=2 WHERE `guid`=@GUID;
DELETE FROM `creature_addon` WHERE `guid`=@GUID;
INSERT INTO `creature_addon` (`guid`,`path_id`,`mount`,`bytes1`,`bytes2`,`emote`,`auras`) VALUES (@GUID,@PATH,0,0,1,0, '');
DELETE FROM `waypoint_data` WHERE `id`=@PATH;
INSERT INTO `waypoint_data` (`id`,`point`,`position_x`,`position_y`,`position_z`,`orientation`,`delay`,`move_type`,`action`,`action_chance`,`wpguid`) VALUES
(@PATH, 1, X, Y, Z, 0, 0, 0 ,0, 100, 0),
(@PATH, 2, X, Y, Z, 0, 0, 0, 0, 100, 0),
(@PATH, 3, X, Y, Z, 0, 0, 0, 0, 100, 0);
```

Note:
For some core ( example cataclysm ). path_id in creature_addon doesn't exists. But waypoint auto handle in waypoint_data by `guid*10`

# Source:
- https://truewow.org/forum/viewtopic.php?t=37081
