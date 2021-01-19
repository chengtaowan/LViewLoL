# LViewLoL

### What is this
LView is a python based scripting platform for League of Legends. The engine is external that means it is not injected into leagues process. The engine is running in a separate process and reads the games state using ReadProcessMemory.

Key features of LView:
  1. Ability to create overlays and automatize gameplay using python scripts
  2. Performant ingame overlays/menus using a combination of directx, direct composition and dear imgui 
  3. Static game data available at runtime. Data is unpacked directly from the game files. Taken from https://www.communitydragon.org/ .
  4. Undetectability. Since LView reads the game state externally the ban probability is close to 0. Currently since the start of the development there is no recorded case of a ban.
  5. A rich set of premade scripts. There are a lot of already implemented and tested gameplay scripts by default in LView and more are to come. Some of these scripts: orbwalker, spell tracker, champion tracker, map awareness, minimap drawings, skillshot drawings... etc 
 

### Building

You need Visual Studio 2017 to compile this. Compile the app on Release x32 (you need to compile boost::python on debug to compile on debug, which I didn't).
Dependencies:
  1. python39: dlls and includes are already in project. You may have to install python39 and make sure you add it to PATH
  3. aws-lambda: dlls and includes are already in project (was used for authentication)
  3. directx 11: Must install directx runtime: https://www.microsoft.com/en-us/download/details.aspx?id=35
  4. boost::python. Due to the size of the boost libraries you must compile boost::python yourself:
      1. Download boost 1.75.0 
      2. Unarchive it in LView/boost
      3. Go into LView/boost
      4. Run `bootstrap.bat`
      5. Run `b2 --with-python link=shared toolset=msvc-14.1 address-model=32 variant=release`
  
 ### Setup
 All LView & LView python scripts configurations reside in config.ini file. First you must set the path to the scripts folder with the following config:
 
  `::scriptsFolder=\<folder\>`
