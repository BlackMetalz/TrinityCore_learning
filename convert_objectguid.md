- Something to remember while convert trinitycore with ObjectGuid support


```
uint64 -> ObjectGuid
testinitvarGUID = 0 ->  testinitvarGUID = ObjectGuid::Empty or testinitvarGUID.clear()
GetData64 -> GetObjectGuid
GetUint64Value -> GetGuidValue
```
