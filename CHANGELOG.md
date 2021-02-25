# Mining Assistant for Nexus
# Changelog

## February 24, 2021 \- Mining Assistant version 1.3
### Changes
- Included MARESET and MAVALS in the command list displayed with MA for the time being. Ideally, these will eventually not be necessary to include.
- Added the 'KnockedDownTundra' trigger in the 'ProspectReflex' group. This should account for being stopped by the prone that the wendigos in the Tundra use and during my testing it was successful. There may be some weirdness with that still however so I have marked it as partially resolved for now.
- Added a group for Highlights. Removed the highlighting from triggers 'ProspectReflex3' and 'ProspectReflex4' and added them to triggers in the Highlights group.
- Moved 'Tracking' group to inside 'ProspectTriggers' group
- Moved 'RoomCollect' group to inside 'ProspectTriggers' group
- Fixed a display notice error in alias 'SetRoute'
- Fixed a display notice error in trigger 'ProspectReflex4'
- Variable set added in 'TooFarAway' trigger
- Adjusted some of the logic in trigger 'ArrivedDestination'
- Adjusted some of the logic in trigger 'SettingsDisplay'
- Modified some parts of the onGMCP to set/change values only when prospecting is happening.

### Issues
- Noticed an issue with the Mine Collection caused by high latency, in which movement will occur before the sign gets read, and due to how the trigger works this also leads to the mine not getting pushed to the mine collection array. Uncertain what the best solution for this might be but I've added it to the To-do list in any case.
- For those who prospect with a mount and have something in place to mount again should they get knocked off, this could also interfere with prospecting such as with the wendigos in the Tundra as there is nothing currently in place at this time that deals with mounting.
