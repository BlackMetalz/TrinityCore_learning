- Something to remember while convert trinitycore with ObjectGuid support


```
uint64 -> ObjectGuid
ObjectGuid::Empty
OBJECT_FIELD_SCALE_X -> OBJECT_FIELD_SCALE
GetData64 -> GetObjectGuid
SetData64 ->SetGuidData
UNIT_NPC_FLAGS -> UNIT_FIELD_NPC_FLAGS
GAMEOBJECT_FLAGS-> GAMEOBJECT_FIELD_FLAGS
UNIT_FIELD_FLAGS_2 -> UNIT_FIELD_FLAGS2
GAMEOBJECT_LEVEL -> GAMEOBJECT_FIELD_LEVEL
UNIT_DYNAMIC_FLAGS ->  OBJECT_FIELD_DYNAMIC_FLAGS
UNIT_NPC_EMOTESTATE -> UNIT_FIELD_EMOTE_STATE
UNIT_FIELD_BYTES_1 ->  UNIT_FIELD_ANIM_TIER
MAN25_DIFFICULTY -> DIFFICULTY_25MAN_NORMAL
MAN10_DIFFICULTY -> DIFFICULTY_10MAN_NORMAL
GetDifficulty() -> GetDifficultyID()
GetSpawnMode -> GetDifficultyID
UNIT_FIELD_MINRANGEDDAMAGE -> UNIT_FIELD_MIN_RANGED_DAMAGE
UNIT_FIELD_MAXRANGEDDAMAGE -> UNIT_FIELD_MAX_RANGED_DAMAGE
RegisterCreatureAI(npc_skyfall_star);
PLAYER_VISIBLE_ITEM_16_ENTRYID -> PLAYER_FIELD_VISIBLE_ITEMS + 16
if it was throwing error in scripts project
it shd be using GetGuidValue
like for example PLAYER_FIELD_FARSIGHT
or UNIT_FIELD_TARGET

those are now guid fields

GetUInt64Value -> GetGuidValue
IS_VEHICLE_GUID(guid) -> guid.IsVehicle()
RegisterCreatureAI ->    BossAI / ScriptedAI

RegisterSpellScript -> SpellScript
RegisterAuraScript -> AuraScript

GetPhaseMask() -> GetPhaseShift()

SMSG_CLIENT_CONTROL_UPDATE -> CHARM_TYPE_VEHICLE??

JadeCore::Containers::RandomResizeList<Player*>(targets, targetCount);

-> JadeCore::Containers::RandomResizeList(targets, targetCount);

GUID_LOPART(_chaseGUID) -> _chaseGUID.GetCounter()

```
