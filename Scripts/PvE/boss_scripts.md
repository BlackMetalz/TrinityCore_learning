1. Combat reach and bounding radius
```
                me->SetFloatValue(UNIT_FIELD_BOUNDING_RADIUS, 10);
                me->SetFloatValue(UNIT_FIELD_COMBAT_REACH, 10);
```

This prevent player pull boss too far away from Boss fight location. There is some exploit if we don't set this value

Arty said: 
```
nope cause that is hack xd
u use sniff values for that, and in boss script u check distance in update
latest TC has bossbounderies to auto reset if out of room
```
