# Consolidated Monk Combos (Modified) for Nexus
# Changelog

## March 30, 2021 \- Consolidated Monk Combos (Modified) version 1.1
### Changes

- Removed `2: swk @tar` from the combo table client.limbTable (Punch Table) from alias **'ComboTables'** and from the **onLoad** function.
- Fixed an error in the alias text for alias **'Punch'** (Removed '2' from the first and second args capture, as `2: swk @tar` is no longer included in client.limbTable by default)
- Fixed an error in the alias text for alias **'Kick'** (Removed '2' from the second args capture, same reason as above)
- Adjusted the default order of some of the hotkeys in the combo tables both in alias 'ComboTables' and the onLoad function.
- Adjust some of the logic in alias **'PunchKick Enable/Disable'**
- Adjusted some of the logic for the combo functions declared in the **onLoad**, added the designation of 'true' to each setalias in hopes that this resolves an issue in relation to hitting the opposite limb that was targeted (eg. Alias "mcombo" will now execute: "stand/deaf/blind/insomnia/toughness/weathering/resistance/combo @tar swk hfp left hfp left", queue addclear eqbal mcombo is sent, the sweepkick happens, the first punch hits the left leg, but then the second punch hits the right leg).

### Issues

- Experiencing an issue that involves the wrong limb getting hit (for example the right leg) despite having targeted the left leg. I am not sure why this occurs and it appears the alias and everything else is getting set properly, and queue addclear eqbal is being utilized when sending the command. I will have to do some further testing/investigation in to why this occurs if the problem is indeed somewhere on my end. It could be in my code, it could with the use of setalias itself, it could be some issue similar to curing queue recieving random inputs from other queues, or it could be something else entirely.
