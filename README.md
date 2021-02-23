# Mining Assistant

Mining Assistant version 1.2<br/>
Created by Kaios


REQUIREMENTS - PLEASE READ
--------------------------
**NECESSARY:** In order for this package to work, it is REQUIRED that you also have Zahan's MapDB (Map Database) reflex package as well. You can obtain this package from https://github.com/AchaeaZahan/Nexus (instructions for download are provided by his ReadMe on this page).

**OPTIONAL:** If you wish to use the Mine Collection feature, you will also need to have Voka's CharacterDB (Character Database) reflex package. This is necessary in order to get a mine owner's city with their name while prospecting. You can obtain this package from https://forums.achaea.com/discussion/6527/character-db-nexus (right click the link in the post and 'Save Link as').


List of Commands
----------------
MA : Displays this list.

MASET : Displays your current settings. These settings include; Size of the lode that prospecting stops at, status of Mine Collection, status of Wings Mode, and the Current Route.

MAPR : Begins prospecting.

MASTOP : Stops prospecting. Will continue prospecting from the stopping point when re-initialized with MAPR.

MACOLLECT : Turns ON or OFF the Mine Collection. Starts OFF by default. Does not work properly without the CharacterDB package. **(Refer to OPTIONAL requirements above)**

MAWINGS : Turns ON or OFF Wings Mode. Starts OFF by default. **(WINGS MODE MAY NOT FUNCTION CORRECTLY AT THIS TIME)**

MALODE : Reports the lode that was last prospected. **Initially disabled. Ensure that you designate a CLANTELL for this within the appropriate alias before enabling.**

MALODESIZE <size> : Sets the size of lode that prospecting will stop at. Tiny, Small, Medium, Large, Huge, or Massive.

MAROUTE <route> : Set the route by area that will be prospected. Refer to Route Keys list below for short-name definitions.
Examples: maroute gra san vashcen dun vashs mhocen mhosw sir shamte pashe pashw shamtw OR maroute dak vashs sir gra ... and so on.

Route Keys:<br/>
dak = Dakhota Hills<br/>
dun = Dun Valley<br/>
gra = Granite Hills<br/>
mhocen = Mhojave Desert Central<br/>
mhosw = Mhojave Desert Southwest<br/>
pashe = Pash Valley East<br/>
pashw = Pash Valley West<br/>
san = Sangre Plains<br/>
shamte = Shamtota Hills East<br/>
shamtw = Shamtota Hills West<br/>
sir = Sirrocian Mountains<br/>
vashcen = Vashnar Mountains Central<br/>
vashs = Vashnar Mountains South<br/>

MAMINES : Display a list of Mines and Lodes collected during prospecting (No Mines will be collected if Mine Collection is OFF).

MASEARCH <input> : Search the Mine Collection for a name or value. Returns each mine that contains a match. **Credit to Khaseem for this alias.**

MARESET : Resets the variables used in Prospecting and Data Collection (In most cases used for testing purposes). Route will be set back to the beginning and mine and lode collection will be erased.

MAVALS : Display some relevant values (In most cases used for testing purposes).


To-do List
----------
- (PARTIALLY RESOLVED) Complete blocked by wall trigger. (Need method to discern the user's capabilities, eg. can they leap? are they mounted?)
- (PARTIALLY RESOLVED) Complete allowance for Wings Mode; Ensure there are no issues with movement and destination tracking, set room orders specific for Wings Mode.
- Different types of wings to account for?
- Devise method to handle room order customization (beyond manual user modification).
- Account for wendigos in Tundra. At present, their knock-down occasionally interferes with prospecting which must then be re-initialized using MAPR.<br/>
✓  (RESOLVED): Vision loss (such as caused by blizzards) interferes with proper GMCP identification of items (eg. reading signs, identify walls).<br/>
- Travel method from main land to Tundra? Fissure of Echoes?
- Option to send Mine/Lode collection to a text file. Save to the same file each time? Create multiple files? If pushing to same, also need date/time (in-game and real) to separate. If pushing to multiple, need date/time as file name.
- Automate lode reporting.
- Alter search alias to not return partial matches.
- Need method to avoid pushing duplicate strings to mine collection and lode collection arrays.


Credits
-------
A very special thank you to **FangFang** not only in relation to this package, but also for his constant assistance and support that he has generously given to myself and many others with Nexus scripting.

**Khaseem**, for his very helpful assistance in devising a better queueing method and for the use of his Walkto package's search alias.

**Zahan**, for without his MapDB package it would be far more difficult to create such packages like this in the first place.

**Voka**, for the creation of the CharacterDB package which is an incredibly useful tool.

Thank you to the testers, **Svenson** and **Aranos**!
