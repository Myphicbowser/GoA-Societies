####################################
### WAY OF KINGS  SOCIETY MODULE ###
###          README              ###
###       by Caden335            ###
####################################

## NOTES FOR PLAYTESTING
 You can use the console to select or join societies with 'effect join_society = {SOCIETY=<whatever_society>}' or 'effect select_society = {SOCIETY=<whatever_society>}'
 You can add 2000 society currency by running 'effect gain_a_bunch_of_society_currency' in the console

## HOW TO ADD A SOCIETY (This is moderately long, but they are societies)
 0. Decide on the name for your new society. It should be something like "society_mib" or "society_templars"
 1. Add lines for the society in common/scripted_effects/society_main.txt wherever you see lines for other societies
 2. Add artwork for the society in gfx/societies. If you need a base use the society_blank bases
 3. Add texticons to gui/society_icons
 4. Add a unique join_<societyname> in common/scripted_effects/unique_societies_effects.txt effect for your society (such as triggering an event chain). If you just want to join instantly just add this line and that's all: join_society = {SOCIETY = <society>} Whenever you finally want them to join the society, such as at the end of the event chain add the same effect
 5. Add to 00_society_recruitment_values in script_values for your society
 6. In script_values add a currency_income value in 00_society_values and add a line for said (new society)_currency_income in 00_base_society_values
 7. Add society requirements in common/scripted_triggers/society_specific_triggers.txt for your society
 8. Add in a scripted gui for the society in common/scripted_guis/specific_societies_gui.txt that references the above requirement in the is_shown block
 9. Add in the common/scripted_guis/societies_gui.txt a hidden society gui
 10. Add the society to the ability decisions/interactions and mission events you want it to be valid for.
 11. Localize society
 12. Add lines to society_on_actions for the on_start_society_members_gen (so that your society starts with members) and to society_member_death (just copy an existing one and change it your society)
 13. In society_yearly_on_actions add lines for whatever conditions you need for someone to join it. I suggest just copying your on_start_society_members_gen and change it from every_living_character to every_character_not_in_society as well as massively decreasing the chances of people joining the society.
 13a. Furthermore add to the rank_up part of said on action

## OPTIONAL STUFF
 Add your society to hidden_member_societies in society_specific_triggers so that people not in the society can't see the members of your society

## HOW TO ADD A MISSION
 0. Decide on a name (This is always going to be in 0.)
 1. In common/on_actions/society_yearly_on_actions.txt add to the random list with a chance that triggers the mission giving event
 2. Localize your mission
 3. Add an event that gives the mission in society_mission_events, I suggest copying society_mission.1001
 4. Localize said event
 5. Add a way to fulfill the mission, like tying it to demand conversion or something similar. I can't tell anyone how to do this because of the many different possibilities

## HOW TO ADD AN ABILITY
 0. Decide on the ability
 1. Add a decision or interaction or whatever you want for it.
 2. In the trigger for said ability add a check for if you are in said society: "has_variable = society_prowess_member" and a trigger for your rank in the society "is_at_least_rank_three_in_society = yes", "is_rank_four_in_society = yes", etc
 3. In the society loc for the rank options add the ability to the rank at which you unlock it

## NOTE
 This does use the GUI Framework and is compatible with all mods that use it
