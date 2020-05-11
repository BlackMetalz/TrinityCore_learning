- Something to remember while convert trinitycore with ObjectGuid support


```
uint64 -> ObjectGuid
ObjectGuid::Empty

GetData64 -> GetObjectGuid

UNIT_NPC_FLAGS -> UNIT_FIELD_NPC_FLAGS

UNIT_FIELD_FLAGS_2 -> UNIT_FIELD_FLAGS2

UNIT_DYNAMIC_FLAGS ->  OBJECT_FIELD_DYNAMIC_FLAGS
UNIT_NPC_EMOTESTATE -> UNIT_FIELD_EMOTE_STATE
UNIT_FIELD_BYTES_1 ->  UNIT_FIELD_ANIM_TIER

RegisterCreatureAI(npc_skyfall_star);

if it was throwing error in scripts project
it shd be using GetGuidValue
like for example PLAYER_FIELD_FARSIGHT
or UNIT_FIELD_TARGET

those are now guid fields

GetUInt64Value -> GetGuidValue

RegisterCreatureAI ->    BossAI / ScriptedAI

RegisterSpellScript -> SpellScript
RegisterAuraScript -> AuraScript

GetPhaseMask() -> GetPhaseShift()


```
