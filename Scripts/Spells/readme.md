## 1. On proc hook --> trigger spell
/// Mastery: Shadowy Recall - 77486
```
class spell_mastery_shadowy_recall : public SpellScriptLoader
{
public:
    spell_mastery_shadowy_recall() : SpellScriptLoader("spell_mastery_shadowy_recall") { }

    class spell_mastery_shadowy_recall_AuraScript : public AuraScript
    {
        PrepareAuraScript(spell_mastery_shadowy_recall_AuraScript);

        bool Load() override
        {
            return GetCaster() && GetCaster()->IsPlayer();
        }

        void OnProc(AuraEffect const* /*p_AurEff*/, ProcEventInfo& p_EventInfo)
        {
            Unit* l_Caster = GetCaster();
            if (l_Caster == nullptr)
                return;

            Unit* l_Target = p_EventInfo.GetActionTarget();
            if (l_Target == nullptr)
                return;

            if (!p_EventInfo.GetDamageInfo()->GetSpellInfo())
                return;

            if (roll_chance_f(l_Caster->GetFloatValue(PLAYER_MASTERY) * 1.8f))
                l_Caster->CastSpell(l_Target, GetTriggerSpell(p_EventInfo.GetDamageInfo()->GetSpellInfo()->Id), true);
        }

        uint32 GetTriggerSpell(uint32 p_ProcSpell)
        {
            switch (p_ProcSpell)
            {
              case 589:   ///< Shadow Word : Pain
                  return 124464;
              case 2944:  ///< Devouring Plague
                  return 124467;
              case 34914: ///< Vampiric Touch
                  return 124465;
              case 48045: // Mind Sear
                  return 124469;
                  break;
              default:     ///< Mind Flay
                  return 124468;
            }
        }

        void Register() override
        {
            OnEffectProc += AuraEffectProcFn(spell_mastery_shadowy_recall_AuraScript::OnProc, EFFECT_0, SPELL_AURA_DUMMY);
        }
    };

    AuraScript* GetAuraScript() const
    {
        return new spell_mastery_shadowy_recall_AuraScript();
    }
};
```
