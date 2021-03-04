# Mining Assistant for Nexus
# Changelog

## March 4, 2021 \- Mining Assistant version 1.5
### Changes

- Added a GMCP Request for 'Char.Skills.Get' to the onLoad.
- Implemented a check in the onGMCP that checks character Riding rank and enables the mountjump trigger if at Expert or greater, or ensures the trigger is disabled otherwise.
- Added 'Blocked' group within the 'ProspectReflex' group and moved the trigger 'BlockedByWall' inside of it.
- Adjusted some of the logic in trigger 'BlockedByWall' and separated in to other triggers.
- Created trigger 'MountJumping' in 'Blocked' group.
- Created trigger 'JumpComplete' in 'Blocked' group.
- Removed a section of code in the trigger 'ArrivedDestination' that appeared to be redundant. May somewhat improve the rate at which the code is executed during prospecting.
- Adjusted some of the logic in trigger 'KnockedDownTundra'
- Adjusted some of the logic in alias 'SetLodeDetection'
- Adjusted some of the logic in alias 'On/Off Alias'
- Adjusted some of the logic in trigger 'DestinationTrack'
- Adjusted some of the logic in trigger 'ProspectReflex2'
- Removed the 'Incomplete' group since there is nothing in it at this time.

### Issues

- Opted to remove the parameter in the onGMCP that requires prospecting to be occuring before some things are set as it was causing a few issues. For example with Mine Collection's sign reading when first entering the Tundra, since you are not prospecting on initial entry and due to that change I made in the onGMCP to prevent Char.Items.List from setting anything while prospecting is not occurring, the item id of the sign was not being collected and would not be read properly. Or also, when entering the Tundra in to a blizzard. I do not believe that anything I have going on in the GMCP is doing anything intensive but I will think about how I could implement a better solution for this, such as only requiring the item id of a sign to be necessary in the case there are other signs in the room.
- Still need to include Stone Wall identification for the 'BlockedByWall' trigger.

## February 26, 2021 \- Mining Assistant version 1.4
### Changes

- Adjusted how the global variables are set in the alias **'SetRoute'**
- Switched from `var` to `let` for the variable setting in alias **'SetLodeDetection'**
- Slight adjustment to a display notice in alias **'SetLodeDetection'**
- Changed the highlighting for many of the display notices to something more pleasant, but retained original highlighting for onLoad, stopping at lodes, errors, and other important notices.
	
  #### Wings Mode
	- Changed trigger **'CloudsMovement'** to a regular expression to include 'on the clouds', 'high above the clouds', and 'far above the clouds' in capture.
	- Added a 100ms timeout before the code in trigger **'CloudsMovement'** is executed to help ensure you have actually arrived at the Skies before the check and movement occur. The time could be changed to suit your needs or removed entirely if you feel it's unnecessary.
	- Modified trigger **'DestinationTrack'** to queue an alias which uses 'SAY Duanathar' instead of the sending the say command directly. Included custom alias setting and clearing when Wings Mode is turned ON or OFF.
	- Increased number of rooms away from destination to use Wings from greater than or equal to 20, to greater than or equal to 21. (Trigger **'DestinationTrack'**)
	- Changed `send_command("SAY Duanathar", true);` to `send_command("queue addclear eqbal wingsmove");` in trigger **'DestinationTrack'**
	- Added a display notice in the trigger **'DestinationTrack'**
	- Modified **'On/Off Alias'** to include setting and clearing an alias for 'SAY Duanathar' when Wings Mode is turned ON or OFF.

	#### Mine Collection
	- Changed the way Mine Collection is handled to help account for latency. Instead of the read sign command occuring in the **'MineCollection'** trigger and then including a Wait For action, I have separated this in to two triggers (**MineCollection1** and **MineCollection2**); one for the mine and one for the sign reading, which is now read at the same time prospecting occurs in the trigger **'ProspectReflex2'** if Mine Collection is ON. This also makes it easier to modify if you want to push the string without getting the city or including the sign reading step, in the case one does not have or want to use Voka's CharacterDB package.
	- Changed **'On/Off Alias'** to enable or disable both Mine Collection triggers when turned ON or OFF.

### Issues

- Issue reported in relation to Wings Mode; It seems the line `send_command("SAY Duanathar", true);` in the trigger **'DestinationTrack'** does not always use your wings when the command is sent in this way. I'm uncertain if this happens occasionally or all the time or what the reason could be, but I suspect if it works some of the time then it's related to having or not having balance when used. What I have done instead is change the command in **'DestinationTrack'** to `send_command("queue addclear eqbal wingsmove");` and the alias 'wingsmove' is being set when Wings Mode is turned ON and cleared when Wings Mode is turned OFF. Please let me know if there are still issues with this change.
- Trigger **'DestinationTrack'** occasionally fires twice. This might be due to the STOP command in the trigger being sent when no movement is occuring and then it tries again after movement continues (thus firing for both rooms), or it may just be related to latency and the fast movement rate. Since you cannot say things consecutively in such a quick manner it doesn't appear to cause much issue with going to the Skies itself but I will try to figure out why this is happening and come up with a solution for it.

## February 24, 2021 \- Mining Assistant version 1.3
### Changes
- Included MARESET and MAVALS in the command list displayed with MA for the time being. Ideally, these will eventually not be necessary to include.
- Added the **'KnockedDownTundra'** trigger in the **'ProspectReflex'** group. This should account for being stopped by the prone that the wendigos in the Tundra use and during my testing it was successful. There may be some weirdness with that still however so I have marked it as partially resolved for now.
- Added a group for Highlights. Removed the highlighting from triggers **'ProspectReflex3'** and **'ProspectReflex4'** and added them to triggers in the Highlights group.
- Moved 'Tracking' group to inside **'ProspectTriggers'** group
- Moved 'RoomCollect' group to inside **'ProspectTriggers'** group
- Fixed a display notice error in alias **'SetRoute'**
- Fixed a display notice error in trigger **'ProspectReflex4'**
- Variable set added in **'TooFarAway'** trigger
- Adjusted some of the logic in trigger **'ArrivedDestination'**
- Adjusted some of the logic in alias **'SettingsDisplay'**
- Modified some parts of the onGMCP to set/change values only when prospecting is happening.

### Issues
- Noticed an issue with the Mine Collection caused by high latency, in which movement will occur before the sign gets read, and due to how the trigger works this also leads to the mine not getting pushed to the mine collection array. Uncertain what the best solution for this might be but I've added it to the To-do list in any case.
- For those who prospect with a mount and have something in place to mount again should they get knocked off, this could also interfere with prospecting such as with the wendigos in the Tundra as there is nothing currently in place at this time that deals with mounting.
