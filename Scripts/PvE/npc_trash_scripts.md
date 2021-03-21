```
class npc_siege_of_orgrimmar_korkron_blood_axe : public CreatureScript
{
	public:

		npc_siege_of_orgrimmar_korkron_blood_axe() : CreatureScript("npc_siege_of_orgrimmar_korkron_blood_axe") { }

		CreatureAI* GetAI(Creature* creature) const
		{
			return new npc_siege_of_orgrimmar_korkron_blood_axeAI(creature);
		}

		struct npc_siege_of_orgrimmar_korkron_blood_axeAI : public ScriptedAI
		{
			npc_siege_of_orgrimmar_korkron_blood_axeAI(Creature* creature) : ScriptedAI(creature)
			{
				ApplyAllImmunities(true);
				me->ApplySpellImmune(0, IMMUNITY_MECHANIC, MECHANIC_GRIP, false);
				me->ApplySpellImmune(0, IMMUNITY_MECHANIC, MECHANIC_STUN, false);
				me->ApplySpellImmune(0, IMMUNITY_MECHANIC, MECHANIC_ROOT, false);

				pInstance = creature->GetInstanceScript();
			}

			void Reset()
			{
				events.Reset();
			}

			void EnterCombat(Unit* victim)
			{
      
			}

			void UpdateAI(const uint32 diff)
			{
				if (!UpdateVictim())
					return;

				events.Update(diff);

				if (me->HasUnitState(UNIT_STATE_CASTING))
					return;

				if (uint32 eventId = events.ExecuteEvent())
				{

				}

				DoMeleeAttackIfReady();
			}

			void JustDied(Unit* killer)
			{
				events.Reset();
			}

		private:

			InstanceScript* pInstance;
		};
};
```

Define spell and event for them
