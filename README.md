# Tasks QoL Pack
v1.0.0

A modpack consisting of my task related QoL mods.  
I decided to bundle together 3 of my mods because all depend on each other. If need be I can eliminate the dependency, but for now I just release it as a pack instead.

# Disclaimer
**PDA Taskboard Fix** Needs some more testing. Especially with iTheon tasks.
So far I got good results hence why I dare to share this mod(pack) with you guys.

# Contents
- **The Job Can Wait**
- **The Northern Job**
- **PDA Taskboard Fix** (Only available within this pack)

# PDA Taskboard Fix
So let's talk about this one. There is a bug with the PDA taskboard.  
Sometimes tasks can appear in the wrong place resulting in you accepting a task you didn't intend to.  
This probably has to do something with map blacklisting.   
When I tested what can cause it I basically blacklisted all maps from the map pool and the bug occured 90% of the time.  
  
**The Job Can Wait** and **The Northern Job** enhanced this bug and made it appear more frequently. I spent the last 2 days troubleshooting, thinking about the best solution.  
The original implementation relied on an array having items in the same order as a different array. This is a very brittle thing I'm surprised it doesn't break more often.  

My solution to this problem: I modified all methods (ones I could find at least) that can affect the second array and gave it the TaskId as the key. This way I can just give it a TaskId when I need additional info about a task and it will always return the correct information.  
  
Added 2 failsafes too.
1. Created a second array that is the copy of the first, but as key it has the task's title (I need this for iTheon tasks because I didn't figure out a way or didn't find where I should implement code to pass TaskId).
1. I left the original implementation as a 3rd failsafe just in case my modifications fail. So at worst you guys get back the old taskboard. At best you get a fixed one.

There are ~3 tasks that can bug out rn. I added some flavour text for these tasks and disabled the accept button. 
I'm working on actually just not even including these in the PDA Taskboard, but I need more time to properly implement that

# Installation instructions
If you have any of these enabled: **The Job Can Wait**, **The Northern Job** disable them.
Drop this mod at highest priority as it overwrites a lot of files.

# Compatibility
Manual patching needed
- New levels 0.53 (2023.07.25): Patch can be found in `gamedata\compatibility_patches\New_Levels_0.53`. There is a `README.txt` with instructions on how to apply (You just need to drag and drop 1 file no biggie).
- If you've disabled `G.A.M.M.A. Psy Fields in the North`. There is a folder in `gamedata\compatibility_patches` called `You disabled - G.A.M.M.A. Psy Fields in the North`. Check readme and install.

# MCM Options
- Standalone **The Job Can Wait** had MCM options. These can still be found under MCM -> **The Job Can Wait**.
