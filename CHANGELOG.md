### Changelog

#### Version - 2.4.4.5 - 6/12/2021
* HOTFIX: Fix a game location detection error caused by `\\` in game paths

#### Version - 2.4.4.4 - 6/9/2021
* Use Erri's Game finder library so we can centralize game detection
* Fix to a compilation error mis-detecting Skyrim folders
* Several other dependency updates

#### Version - 2.4.4.3 - 5/28/2021
* Several quality of life fixes with install paths, logging and null pointer errors 

#### Version - 2.4.4.2 - 5/17/2021
* Modlists are now exported as X.wabbajack where X is the name chosen in the Compiler UI
* Added a new `Network Workaround` mode to the WJ settings panel. Enabling this will bypass Cloudflare and
a lot of caching/DNS layers. Give this a try if you're getting strange SSL errors instead of using a VPN
Should also help get around problems with Telekom and their interaction with Cloudflare.  

#### Version - 2.4.4.1 - 5/1/2021
* HOTFIX: downgrade cefsharp to fix the in-app browser (fixes Nexus login issue)

#### Version - 2.4.4.0 - 4/30/2021
* Search by tags in the gallery view
* Moved tags to a place where they won't break the UI so much if we have a lot of them
* Added a modlist contents viewer (does not require downloading the modlist)

#### Version - 2.4.3.3 - 4/13/2021
* Default to a "Wabbajack" user agent when making HTTP calls
* Some niceties for Mod authors uploading to our CDN
* upgrade several external dependencies

#### Version - 2.4.3.2 - 4/1/2021
* Fix for crashing when WJ is installed in the root drive
* Vortex is now the only option for WJ modlists, down with MO2, purge the xenos, praise to the Emperor
* Slightly more stable GoogleDrive link verification
* Updated several dependency libraries


#### Version - 2.4.3.1 - 3/24/2021
* HOTFIX : Go back to the non-core version of CEF, .NET Core version was crashing
* Folders prefixed with `[NoDelete]` in the name will be ignored when WJ cleans a installed modlist
* Resolution detection and setting is now supported for `SSEDisplayTweaks.ini` and `Oblivion.ini`

#### Version - 2.4.3.0 - 3/20/2021
* CDN part uploads are now retried
* New compiler options for including saves/splashscreens
* Save the location of modlists when installing
* Update several deps that were still based on .NET Framework

#### Version - 2.4.2.7 - 3/11/2021
* Several fixes for working off the new CDN
* Better detect failures in the launcher
* The app now cleans up older versions (leaving a total of 2 previous versions)
* The app now updates the launcher

#### Version - 2.4.2.6 - 2/26/2021
* Cache Modlist images (based on the URL)
* Load Gallery images off the GUI thread improving UI performance

#### Version - 2.4.2.5 - 2/24/2021
* HOTFIX: Fix a O(n*m) performance bug in compilation
* Add support for Enderal SSE

#### Version - 2.4.2.4 - 2/23/2021
* Reworked GDrive downloader for better compatability
* Ignore .cache files for realz
* Add support for folder tagging in Native Compiler mode (thanks Luca!)
* Fixed a "file in use" bug with .BA2s during installation
* Several fixes for Origin game detection

#### Version - 2.4.2.3 - 2/9/2021
* Remove unused file watcher from ManualDownloader
* Lower minimum number of threads to 1
* Added support for Kerbal Space Program
* Add Origin support for DA:O
* Stop vaccuming the patch cache (resulting in overuse of resources on some system)
* Fix reading flags in comments for DeconstructBSAs
* Update the "Overwrite folder" text to explain that saves are *not* deleted
* .cache files are now ignored by the compiler

#### Version - 2.4.2.2 - 2/6/2021
* Better Origin game detection
* Don't check the download whitelist for files that are already downloaded

#### Version - 2.4.2.1 - 2/4/2021
* HOTFIX - fix for the download path sometimes being empty
* HOTFIX - fix for some drive types not being detected (e.g. RAID drives)

#### Version - 2.4.2.0 - 2/3/2021
* Rework the Nexus Manual Downloading process now with less jank
* Manual Nexus Downloading now explains why it's so painful, and how to fix it (get Premium)
* Manual Nexus Downloading no longer opens a ton of CEF processes
* Manual Nexus Downloading no longer prompts users to download files that don't exist
* Disabled CloudFlare DDOS mitigation for LoversLab downloading, the site is back to normal now

#### Version - 2.4.1.2 - 1/30/2021
* Don't install .meta files for files sourced from the game folder
* Fix bug MO2 archive name detection in .meta files (rare bug with FO4VR and other like games)
* Catch exceptions when ECS downloads manifest data
* Don't double-index game files in some situations (duplicate game names in config files)
* Update all deps
* Reduce memory usage of open files (may help with memory errors during BSA creation)

#### Version - 2.4.1.1 - 1/13/2021
* HOTFIX: Fix game file sources that don't have MO2 specific names

#### Version - 2.4.1.0 - 1/12/2021
* Fix errors with broken SQL DBs crashing the system
* Fix errors with bad SQL clean commands
* Warn when the user doesn't have enough swap space
* Better OS version detection
* Use case-insensitive comparisons in Game File Downloader's PrimaryKeyString

#### Version - 2.4.0.0 - 1/9/2021
* Wabbajack is now based on .NET 5.0 (does not require a runtime download by users)
* Origin is now supported as a game source
* Basic (mostly untested) support for Dragon Age : Origins, Dragon Age 2, and Dragon Age: Inquisition 
* Replace RocksDB with SQLite should result in less process contention when running the UI and the CLI at the same time
* Fixed Regression with CloudFront IPS4 sites not requesting logins before installation
* Fixed regression that caused us to spam the Nexus with verify calls
* Further fixes for IPS4 sites
* Optimized download folder hashing by only hashing files that match a specific size (thanks Unnoen!)

#### Version - 2.3.6.2 - 12/31/2020
* HOTFIX: Also apply the IPS4 changes to LL Meta lookups

#### Version - 2.3.6.1 - 12/31/2020
* When IPS4 (e.g. LL) sites based on CEF fail to validate, they no longer hang the app
* If a IPS4 CEF site throws a 503, or 400 error, retry
* Clean out the cookies during IPS4 CEF downloads so that they don't cause 400 errors
* Limit the number of connections to IPS4 sites to 20 per minute (one per 6 seconds)
* If a site *does* timeout, throw a log of the CEF state into `CEFStates` for easier debugging by the WJ team
* Wrote a new CLI utility to stress test the Verification routines.
* Ignore files that have `\Edit Scripts\Export\` in their path
* Added info/support for GoG's version of Kingdom Come : Deliverance

#### Version - 2.3.6.0 - 12/29/2020
* Move the LoversLab downloader to a CEF based backed making it interact with CloudFlare a bit better
* Add support for No Man's Sky

#### Version - 2.3.5.1 - 12/23/2020
* HOTFIX : Recover from errors in the EGS location detector

#### Version - 2.3.5.0 - 12/16/2020
* Fix tesall.ru download support
* Implement MechWarrior 5 support as a native compiler game
* Make the title in the WJ gallery (in app) optional for games that want the title to be in the splash screen
* Worked a few kinks out of the native game compiler

#### Version - 2.3.4.3 - 12/6/2020
* Disable the back button during install/compilation

#### Version - 2.3.4.2 - 11/24/2020
* Add Support for Kingdom Come : Deliverance (via MO2)
* Several other small bug fixes and deps updates

#### Version - 2.3.4.1 - 11/15/2020
* Tell the mod updater to use the existing Nexus Client instead of creating a new one

#### Version - 2.3.4.0 - 11/15/2020
* Removed the internal Manifest Viewer, you can still view the Manifest of any Modlist on the website
* Improved Nexus warnings about being low on API calls
* Added marker for "utility modlists" we will expand on this feature further in later releases

#### Version - 2.3.3.0 - 11/5/2020
* Game file hashes are now stored on Github instead of on the build server
* Added CLI Verb to produce these hash files for the Github repo
* When a user runs out of Nexus API calls we no longer bombard the Nexus with download attempts
* Check API limits before attempting a modlist download
* Logger is less chatty about recoverable download errors
* Display integer progress values during install so users know how far along in the process they are #issue-1156

#### Version - 2.3.2.0 - 11/2/2020
* 7Zip errors now re-hash the extracted file to check for file corruption issues. Should provide
better feedback in cases that a file is modified after being downloaded (perhaps by a disk failure)
* Fixed a file extraction issue with nested archives, most often seen whith the `Lucian` mod
* Fixed several small bugs and typeos with how open permission mirrored files are handled by Wabbajack
* Fixed a bug in the `download-url` cli command. It can now download from any Wabbajack CDN domain.

#### Version - 2.3.1.0 - 10/24/2020
* Fixed a long standing issue with path remapping, lots of edge cases were resolved here
* Implemented a basic compiler for non MO2 games, will expand as we get feedback
* Removed unused CPU percentage slider, we now have two settings, so please use the settings panel instead

#### Version - 2.3.0.4 - 10/13/2020
* Fix FOMOD extraction (for FNV)

#### Version - 2.3.0.3 - 10/12/2020
* Revert some 7zip changes due to 7zip crashing the app

#### Version - 2.3.0.2 - 10/5/2020
* Fixed a situation where 7zip would refuse to extract very large archives

#### Version - 2.3.0.1 - 10/4/2020
* Rewrote the file extraction routines. New code uses less memory, less disk space, and performs less thrashing on HDDs
* Reworked IPS4 integration to reduce download failures
* Profiles can now contain an (optional) file `compiler_settings.json` that includes options for other games to be used during install.
This is now the only way to include extra games in the install process, implicit inclusion has been removed. 
* Number of download/install threads is now manually set (defaults to CPU cores) and is independently configurable
* Includes a "Favor performance over RAM" optional mode (defaults to off) that will use excessive amounts of RAM in exchange
for almost 1GB/sec install speed on the correct hardware. Don't enable this unless you have a fast SSD and at least 2.5GB of RAM for every
install thread.
* Fixed Extraction so that zip files no longer cause WJ to CTD
* Better path logging during install and compilation
* Fix the "this was created with a newer version of Wabbajack" issue
* If a downloaded file doesn't match the expected hash, try alternative download locations, if allowed


#### Version - 2.2.2.0 - 8/31/2020
* Route CDN requests through a reverse proxy to improve reliability

#### Version - 2.2.1.7 - 8/25/2020
* HOTFIX - Fix 404 errors with mirrors

#### Version - 2.2.1.6 - 8/24/2020
* HOTFIX - Make LoversLab auto-update work again
* HOTFIX - Fix for "End of Stream before End of Limit" symptom on BSA extraction

#### Version - 2.2.1.5 - 8/21/2020
* HOTFIX - Fix for broken patching in RGE and other lists

#### Version - 2.2.1.4 - 8/21/2020
* HOTFIX - No really...stop doing that

#### Version - 2.2.1.3 - 8/20/2020
* HOTFIX - We broke installation of existing lists...let's stop doing that

#### Version - 2.2.1.2 - 8/20/2020
* Added `WABBAJACK_ALWAYS_DISABLE` flag (see Readme for more info)
* Modlist can't be installed if the current Wabbajack Version is smaller than the Version used during Compilation of the Modlist
* Updates to use the latest version of the Wabbajack Common libs
* Don't require more than one game to be installed, unless absolutely required (this was a compiler bug)

#### Version - 2.2.0.0 - 8/7/2020
* Can now use NTFS XPRESS16 compression to reduce install sizes (optional in the settings panel)
* Better valid directory detection during install
* Prime the Hash cache during install so that we don't have to re-hash during a modlist update
* Better detection and handling of midden files
* Reworked the installer to use less temporary storage during install, keeps fewer archives open at once
* Launcher now passes arguments to the main Wabbajack.exe application

#### Version - 2.1.3.4 - 7/28/2020
* Fixes for Tar Files (for realz this time)
* Watch disk usage, throw an error if disk usage gets too high
* Added error icon triangle under install play button if there are blocking problems.
* Added tooltip styling to limit width to 500.
* Adjusted error text for MO2Installer unexpected files.
* Added filepicker error glow
* Disable WASM in the in-app browser so we can log into the Nexus again

#### Version - 2.1.3.3 - 7/22/2020
* Relax the RAR signature so it works with RAR 5 and RAR 4 formats

#### Version - 2.1.3.2 - 7/21/2020
* Fixed regression with 7zip and bad archive files (.tar files with Nemesis)

#### Version - 2.1.3.1 - 7/20/2020
* Fixed Mediafire Downloader not handling direct links
* Support for backup mirrors when a given CDN edge node isn't available
* Several help message improvements
* List ingestion now supports compression and processes on a background threaded
* Support for validation of unlisted modlists
* Abort installation/compilation on 7zip read errors

#### Version - 2.1.3.0 - 7/16/2020
* Filters from the FilePicker are now being used
* Wabbajack will continue working even if the build server is down
* Fixed an issue where the main window does not appear after the splash screen
* Patched executable files (dlls, exes, etc.) are now virus scanned both during compilation and install
* Fixed a VFS cache load issue with compilation

#### Version - 2.1.2.0 - 7/13/2020
* Can heal hand selected MEGA files
* Several backend fixes
* Reworked the ChangeDownload CLI command
* Fix for a VFS cache error when compiling lists that extract BSAs.

#### Version - 2.1.1.0 - 7/10/2020
* New CLI option for clearing nexus cache entries (authors only)
* Retry failed Move commands
* Don't re-hash files during compilation
* Can extract BSAs via wabbajack-cli.exe

#### Version - 2.1.0.2 - 7/7/2020
* Don't scan the game folder during compilation. If you are compiling and want `Game Folder Files` create it in your MO2 folder and manually place files into it
* Don't throw a hard error on a post-patch hash failure.
* Don't save the VFS cache to disk or load it during compilation. We have other caches that make this mostly worthless

#### Version - 2.1.0.1 - 7/6/2020
* Don't include saves in .wabbajack files
* Don't delete saves from any MO2 profile during installation
* Don't try to hash .wabbajack files *in the middle of downloading them*
* Print the PrimaryKeyString in logs when an archive is missing (in case the archive name is blank)

#### Version - 2.1.0.0 - 7/2/2020
* Game files are available as downloads automatically during compilation/installation
* Game files are patched/copied/used in BSA creation automatically 
* CleanedESM support removed from the compiler stack (still usable during installation for backwards compatibility)
* VR games automatically pull from base games if they are required and are installed during compilation 
* New `wabbajack-cli.exe` command `inlined-file-report` which will print statistics on the patches/included files in a `.wabbajack` file

#### Version - 2.0.9.4 - 6/16/2020
* Improve interactions between server and client code

#### Version - 2.0.9.3 - 6/14/2020
* Retry 503s not all 500s

#### Version - 2.0.9.2 - 6/13/2020
* Several bug fixes
* Added Darkest Dungeon as a game to alpha test non Bethesda MO2 game integration

#### Version - 2.0.9.1 - 6/8/2020
* Add crash handling and crash logging to the application startup
* Use string distance comparisons to find Nexus mod upgrades

#### Version - 2.0.9.0 - 6/5/2020
* Added support for Fallout 4 VR

#### Version - 2.0.8.0 - 6/2/2020
* Make sure the MEGA client is logged out before logging in (#881)
* Removed final references to `nexus_link_cache` (#865)
* Run disk benchmarks for 10 seconds and use a tiered approach to disk queue size calculation of disks
* Move the patch cache into RocksDB to get rid of the occasional race conditions while creating patches
* Added downloader support for tesall.ru
* Added downloader support for Yandex Disk
* Numerous bug fixes

#### Version - 2.0.7.0 - 5/28/2020
* Code is now robust when dealing with invasive Anti-virus software. We'll retry deletes/opens if the file is in use
* Rework HTTP retries for all sites to reduce the amount of 503 errors we get from LL
* Temp files now use more robust deletion code 

#### Version - 2.0.6.1 - 5/22/2020
* Fix regression with manual archive downloading

#### Version - 2.0.6.0 - 5/21/2020
* Add auto-healing features back into the client/server code
* Put in the code about "Hashing Archives" that somehow missed the last release

#### Version - 2.0.5.1 - 5/16/2020
* Close Wabbajack when opening the CLI, resolves the "RocksDB is in use" errors
* Print some helpful messages about "Hashing Archives" to let users know the app isn't dead

#### Version - 2.0.5.0 - 5/14/2020
* Make the CDN downloads multi-threaded
* Optimize installation of included files 
* Reinstate a broken feature with disabled mods
* Fix how JSON serializers handle dates (UTC all the things!)
* Fix for Absolute Paths in Steam files

#### Version - 2.0.4.4 - 5/11/2020
* BA2s store file names as UTF8 instead of UTF7
* Check for a BSA file by header magic not by extension (allows .bsa.bak files to be extracted)
* Exclude the game `Data` directory from compilation

#### Version - 2.0.4.3 - 5/10/2020
* Hotfix: tell the WJ CDN downloader to create the parent folder if it doesn't exist

#### Version - 2.0.4.2 - 5/10/2020
* Hotfix: allow the WJ CDN to be used for gallery modlists
* Fix a bug with the CDN downloader and modlist compilation

#### Version - 2.0.4.1 - 5/10/2020
* Hotfix: don't throw a compilation exceptions when metas can't be inferred

#### Version - 2.0.4.0 - 5/9/2020
* Several visual improvements to the gallery thanks to the hard work of Khamûl
* Rewrote most of the server-side code for better stability and performance
* Wabbajack CDN uploads/downloads now use a much more stable segmented interface
* Fixed support for Fallout 3
* Added support for Fallout 3 via GoG
* Several fixes to MEGA support
* Mediafire no longer uses Cef should stop popups (since we no longer run the JS)
* Fallback to the normal Nexus APIs if the WJ cache server is dead

#### Version - 2.0.3.0 - 4/29/2020
* Updated the MEGA Credentials Login form with more UI elements
* Switch LZ4 compression to L8 (vs L12) for much faster SSE BSA creation
* Several other internal code tweaks to improve performance and code quality
* Fixed Mediafire pop-up ads, they are no longer shown
* Updated 3rd party libraries to latest versions

#### Version - 2.0.2.0 - 4/27/2020
* Fixed mediafire links not getting resolved
* Fixed new mega links not being accepted
* Fixed cannot delete readonly file issue
* Fixed WABBAJACK_NOMATCH_INCLUDE with files inside BSAs
* Removed software rendering mode in the GUI...that should never had made it into master

#### Version - 2.0.1.0 - 4/27/2020
* Fixed "FileNotFound" and "File is open by another process" bugs during installation
* Raised the BSA limit from 2,000,000,000 bytes to 2 ^ 31 bytes
* Added NSFW flags for modlists/gallery
* Fixed zEdit settings integration

#### Version - 2.0.0.0 - 4/25/2020
* Reworked all internal routines to use Relative/Absolute path values instead of strings
* Reworked all internal routines to use Hash values instead of strings
* Reworked all internal routines to use Game values instead of strings
* Vortex support has been removed, it wasn't well tested, and wasn't used by enough people to justify further support
* Modlists are no longer saved in a binary format, everything uses Json
* Json type names are now a bit more human friendly
* All server-side code that used MongoDB now uses SQL (unifying the database)
* All Nexus validation code has been reworked to leverage RSS feeds for faster response times to updates
* All non-Nexus validation code has been reworked for better performance
* Feeds are now validated on demand, this is possible due to having a SQL backend and improved Nexus support
* Jobs in the job queue no long clobber each other so much
* BSA routines are now mostly async
* During installation, only the bare minimum number of files are extracted from a 7zip
* During indexing/extraction BSA files are not extracted, instead they are opened and files are read on-demand
* File extraction is now mostly async
* Modlists now only support website readmes (file readmes weren't used much and were a pain to read)
* Modlists now require a machine-readable version field 
* Added support for games installed via the Bethesda Launcher
* Cache disk benchmarking results to save startup time of compilation/install
* Added VectorPlexus mods to the slideshow

#### Version - 1.1.5.0 - 4/6/2020
* Included LOOT configs are no longer Base64 encoded
* Reworked Wabbajack-cli
* Can use a MEGA login (if you have it, not required)
* Don't use the buggy Nexus SSO server, instead use the in-browser API key generator
* Several fixes for zEdit merge integration, handles several side-cases of improper configuration

#### Version - 1.1.4.0 - 3/30/2020
* Added support for Morrowind on GOG
* Fix a bug in the Author file uploader (Sync Error)
* Include symbols in the launcher
* Fix a small race condition/deadlock in the worker queue code

#### Version - 1.1.3.0 - 3/23/2020
* Fix for a lack of VC++ Redist dlls on newly installed Windows machines.

#### Version - 1.1.2.0 - 3/20/2020
* We now set VRAM settings for Skyrim LE ENBs
* Fixes for Morrowind Game metadata
* We now provide suggestions for users who try to install modlists for games they don't have installed
* We now warn users if they aren't running a modern version of Windows

#### Version - 1.1.1.0 - 3/9/2020
* Hotfix for Virtual Memory errors while creating BSAs

#### Version - 1.1.0.0 - 3/5/2020
* Binary Patching stores temporary and patch data on disk instead of memory (reducing memory usage)
* Fix a memory leak with diffing progress reporting
* Fix a bug with bad data in inferred game INI files. 
* Added download support for YouTube
* Slideshow can now display mods from non-Nexus sites
* Building BSAs now leverage Virtual Memory resulting in a 32x reduction in memory usage during installation (#609)

#### Verison - 1.0.0.0 - 2/29/2020
* 1.0, first non-beta release

#### Version - 0.9.23.0 - 2/27/2020
* Several bugfixes and tweaks
* This is most likely the last version before the  1.0 release

#### Version - 0.9.22.1 - 2/25/2020
* Fix NaN error during installation 

#### Version - 0.9.22.0 - 2/24/2020
* Server side fixes for CORS support and FTP uploads
* Print the assembly version in the log (#565)
* Don't thrash the VFS cache name quite so much
* Use OctoDiff instead of BSDiff for better performance during diff generation 

#### Version - 0.9.21.0 - 2/23/2020
* Fix never ending hash issue

#### Version - 0.9.20.0 - 2/21/2020
* Don't reuse HTTP request objects (#532)
* Block popups in the in-app browser (#535)
* Don't print API keys in logs (#533)
* Store xxHash caches in binary format (#530)
* Added support for Morrowind BSA creation/unpacking
* Calculate screen size using DPI aware routines (#545)
* Only retain the most recent 50 log files


#### Version - 0.9.19.0 - 2/14/2020
* Disable server-side indexing of all mods from the Nexus
* Accept download states from clients and index the mods we haven't seen
* Fixes for Skyrin VR USSEP patch
* Remember the download states that we index on the server
* Only print remaining nexus quotas when they change
* Reworked the HTTP backend for Nexus/Http downloads performance and stability is much improved
* Fixed key errors with compilation and installation
* Improvements to the new manifest report

#### Version - 0.9.18.0 - 2/11/2020
* Auto update functionality added client-side.
* Slideshow now moves to next slide when users clicks, even if paused
* Installer now prints to log what modlist it is installing
* Adding `matchAll=<archive-name>` to a *mods's* `meta.ini` file will result in unconditional patching for all unmatching files or BSAs in
that mod (issue #465)
* Added support for non-premium Nexus downloads via manual downloading through the in-app browser.
* Downloads from Bethesda.NET are now supported. Can login via SkyrimSE or Fallout 4.
* Manual URL downloads are streamlined
* AFKMods.com download support is improved

#### Version - 1.0 beta 17 - 1/22/2020
* Build server now indexes CDN files after they are uploaded
* Build server actively looks for DynDOLOD updates
* Fix for the null key exception during compilation
* Added support for tesalliance, and afkmods
* Fix for queue size recommendation of 0GB RAM on low-end machines
* Fix for website readme compilation
* Fix for compiler downloads folder specification (was always standard path)

#### Version - 1.0 beta 16 - 1/19/2020
* Progress ring displays when downloading modlist images
* GUI releases memory of download modlists better when navigating around
* Fixed phrasing after failed installations to say "failed".
* Fixed download bug that was marking some modlists as corrupted if they were replacing older versions.
* While compiling Wabbajack will attempt to download VFS and .meta data from the build server

#### Version - 1.0 beta 15 - 1/6/2020
* Don't delete the download folder when deleting empty folders during an update
* If `Game Folder Files` exists in the MO2 folder during compilation the Game folder will be ignored as a file source

#### Version - 1.0 beta 14 - 1/6/2020
* Updating a list twice without starting WJ no longer deletes your modlist
* .mohidden files will now be correctly detected during binary patching
* Added support for MO2's new path format
* Added support for MO2 2.2.2's `portable.txt` feature
* Added support for VectorPlexus downloads
* Added a new CLI interface for providing Nexus API key overrides
* Several UI backend improvements

#### Version - 1.0 beta 13 - 1/4/22020
* Several fixes for steam game handling
* Fixes for metrics reporting

#### Version - 1.0 beta 12 - 1/3/22020
* Breaking change: the internal serialization format has changed, this will make existing lists inoperable on the latest version of WJ
* Added a change to serialization to make it backwards-compatible in the future
* Added an anonymous key to the metrics
* Fixed INI errors (again)

#### Version - 1.0 beta 11 - 1/3/2020
* Rewrote the ModDB downloader to retry with other mirrors after failure
* INI parse errors are now soft errors
* Fixed several backend stability bugs
* Changed application version scheme to better match the actual app version

#### Version - 1.0 beta 10 - 12/23/2019
* Many internal bug fixes releated to deadlocking
* Take the system RAM into account when configuring queue sizes
* Fixed the "This shouldn't happen" bug during patching. Thanks Noggog for spending countless hours on tracking down the problems.

#### Version - 1.0 beta 9 - 12/18/2019
* Create output folders before trying to download a file

#### Version - 1.0 beta 8 - 12/17/2019
* Fixed parsing of buggy ini files (Bethesda supports them so we must as well)
* Disable invalid modlists instead of hiding them
* Several Vortex improvements
* Implemented HTTP resuming for file downloads

#### Version - 1.0 beta 7 - 12/15/2019
* Fixed a regression with HTTP downloading introduced in beta 5
* No longer show broken modlists in the gallery
* Add Stardew Valley support
* Add support for .dat extraction 
* Several UI fixes

#### Version - 1.0 beta 6 - 12/14/2019
* Fixes for some strange steam library setups
* Implemented download/install counts

#### Version - 1.0 beta 5 - 12/14/2019
* Added LoversLab download support
* Nexus and LL logins now happen via a in-ap browser
* Several UI enhancements

#### Version - 1.0 beta 4 - 12/3/2019
* Several crash and bug fixes

#### Version - 1.0 beta 3 - 11/30/2019
* Reworked much of the UI into a single window
* Can download modlists directly through the single-window UI
* Removed hard error on lack of disk space. We need to think about how we calculate required space


#### Version - 1.0 beta 2 - 11/23/2019
* Optimized install process, if you install on a directory that already contains an install
  the minimal amount of work will be done to update the install, instead of doing a complete
  from-scratch install
* Vortex Support for some non-Bethesda games.
* Reworked several internal systems (VFS and workqueues) for better reliability and stability
* Patches are cached during compilation, and source files are no longer extracted every compile 

#### Version 1.0 beta 1 - 11/6/2019
* New Installation GUI
* Files are now moved during installation instead of copied
* Many other internal/non-user-facing improvements and optimizations

#### Version 1.0 alpha 5 - 11/2/2019
* Fix a NPE exception with game ESM verification

#### Version 1.0 alpha 4 - 11/2/2019
* Reorganize steps so that we run zEdit merges before NOMATCH_INCLUDE
* Look for hidden/optional ESMs when building zEdit plugins
* Check for modified ESMs before starting the long install process

#### Version 1.0 alpha 3 - 11/2/2019
* Slideshow more responsive on pressing next
* Slideshow timer resets when next is pressed
* Changed modlist extension to `.wabbajack`
* You can now open modlists directly (after initial launch)
* Wabbajack will exit if MO2 is running
* Added support for zEdit merges. We detect the zEdit install location by scanning the tool list in 
Mod Organizer's .ini files, then we use the merges.json file to figure out the contents of each merge. 

#### Version 1.0 alpha 2 - 10/15/2019
* Fix installer running in wrong mode

#### Version 1.0 alpha 1 - 10/14/2019
* Several internal bug fixes

#### Version 0.9.5 - 10/12/2019
* New Property system for chaning Modlist Name, Author, Description, Website, custom Banner and custom Readme
* Slideshow can now be disabled
* NSFW mods can be toggled to not appear in the Slideshow
* Set Oblivion's MO2 names to `Oblivion` not `oblivion`
* Fix validation tests to run in CI
* Add `check for broken archives` batch functionality
* Remove nexus timeout for login, it's pointless.
* Force slides to load before displaying
* Supress slide load failures
* UI is now resizeable
* Setup Crash handling at the very start of the app
* Add BA2 support
* Fix Downloads folder being incorrectly detected in some cases
* Fix validation error on selecting an installation directory in Install mode
* Reworked download code to be more extensible and stable

#### Version 0.9.4 - 10/2/2019
* Point github icon to https://github.com/wabbajack-tools/wabbajack
* Add game registry entry for Skyrim VR
* Modlists are now .zip files. 
* Modlists now end with `.modlist_v1` to enable better version control
* If `readme.md` is found in the profile directory, inline it into the install report.
* Fix bug with null uri in slideshow images
* Fix bug in CleanedESM generation 

#### Version 0.9.3 - 9/30/2019
* Add WABBAJACK_NOMATCH_INCLUDE works like WABBAJACK_INCLUDE but only includes files that are found to be missing at the end of compilation
* Add a list of all inlined data blobs to the install report, useful for reducing installer sizes
* Increased dummy EPS detection size to 250 bytes and added .esm files to the filter logic
* Only sync the VFS cache when it changes.
* Fix a crash in GroupedByArchive()
* Detect and zEdit Merges and include binary patches for merges (no install support yet)
* Add unit/integration tests. 
* Don't assume *everyone* has LOOT
* Added support for `.exe` installers
* Rework UI to support a slideshow of used mods during installation and compilation
* Remove support for extracting `.exe` installers
* Added support for `.omod` files
* Stop emitting `.exe` modlist installers
* Reworked Nexus HTTP API - Thanks Cyclonit
* Added permissions system 
* Auto detect game folders

#### Version 0.9.2 - 9/18/2013
* Fixed a bug with BSA string encoding
* Fixed another profile issue confirmed that they are properly included now
* Log when the executable is being generated
* Fixed a integer overflow resulting in a crash in very large BSA reading
* Fix a bug in BSA string encoding
* Add human friendly filesizes to the download header and file info sections in the Install Report
* Improve compilation times by caching BSDiff patches
* Detect when VFS root folders don't exist
* Only reauth against the Nexus every 3 days (instead of 12 hours)
* Optimize executable patching by switching to .NET serialization and LZ4 compression
* Ignore some files Wabbajack creates
* Improve compilation times by reworking file indexing algorithm
* Store patch files in byte format instead of base64 strings
* Verify SHA of patched files after install
* Treat .fomod files as archives
* Include WABBAJACK_INCLUDE files before including patches
* Ignore .bin and .refcache files (DynDOLOD temp files)
* Shell out to cmd.exe for VFS cleaning should fix "ReadOnlyFile" errors once and for all
* Switch out folder selection routines for Win32 APIs, should fix issue #27
* Disable the UI while working on things, so users don't accidentally mis-click during installation/loading
* Disabled "ignore missing files", it didn't work anyways
* Properly delete BSA temp folder after install
* Include size and hash for installed files
 
#### Version 0.9.1 - 9/5/2019
* Fixed a bug where having only one profile selected would result in no profiles being selected


#### Version 0.9 - 9/5/2019
* Added log information for when modlists start parsing during installation
* Check all links during mod list creation
* Generate a installation report during compilation
* Show the report after compiling
* Added a button to view the report before installing
* Added support for non-archive files in downloads and installation. You can now provide a link directly to a file
that is copied directly into a modfile (commonly used for `SSE Terrain Tamriel.esm`)
* Fix crash caused by multiple downloads with the same SHA256
* Putting `WABBAJACK_ALWAYS_ENABLE` on a mod's notes/comments will cause it to always be included in the modlist, even if disabled
* All `.json`, `.ini`, and `.yaml` files that contain remappable paths are now inlined and remapped.
* If Wabbajack finds a file called `otherprofiles.txt` inside the compiled profile's folder. Then that file is assumed
to be a list of other profiles to be included in the install. This list should be the name of a profile, one name per line. 
* Can now set the download folder both during compilation and installation.
* Any config files pointing to the download folder are remapped.
* Refuse to run inside `downloads` folders (anti-virus watches these files too closely and it can cause VFS issues)
* Refuse to run if MO2 is on the system installed in non-portable mode (otherwise broken installs may result) 
* Config files that don't otherwise match a rule are inlined into the modlist
* Warn users before installing into an existing MO2 install folder (prevents unintentional data loss from overwriting existing data #24)
* Fix for read only folder deletion bug (#23)
* Include version numbers and SHAs in the install report
* Removed option to endorse mods, Nexus devs mentioned it was of questionable worth, I (halgari) agree

#### Version 0.8.1 - 8/29/2019
* Fixed a bug that was causing VFS temp folders not to be cleaned
* 7zip Extraction code now shows a progress bar
* Told 7zip not to ask for permission before overwriting a file (should fix the hanging installer problem)
* Fixed several places where we were using long-path incompatible file routines
* Changed the work queue from FIFO to LIFO which results in depth-first work instead of breadth-first
TLDR: We now fully analyze a single archive before moving on to the next.

  

#### Version 0.8 - 8/26/2019
* Mod folders that contain ESMs with names matching the Skyrim core ESMs are assumed to be cleaned versions of the core
game mods, and will be patched from the ESMs found in the game folder. **Note:** if you have also cleaned the files in the Skyrim
folder, this will result in a broken install. The ESMs in the game folder should be the original ESMs, the cleaned
ESMs should go into their own mod. These files currently only include:
    * `Update.esm`
    * `Dragonborn.esm`
    * `HearthFires.esm`
    * `Dawnguard.esm`
* `ModOrganizer.ini` is now interpreted and included as part of the install. As part of the install users will be asked
to point to their game folder, and then all the references to the MO2 folder or Game folder in `ModOrganizer.ini` will
be remapped to the new locations.
* Progress bars were added to several install/hashing and compilation instructions
* 7zip routines were rewritten to use subprocesses instead of a C# library. This will result in slower indexing and installation
but should have full compatability with all usable archive formats. It should also reduce total memory usage during extraction.
* Added the ability to endorse all used mods at the completion of an install
* Custom LOOT rules are now included in a special folder in MO2 after install. Users can use this to quickly import new LOOT rules.
* Moved the VFS cache from using BSON to a custom binary encoding. Much faster read/write times and greatly reduced memory usage.
**Note:** This means that modlist authors will have to re-index their archives with this version. This is automatic but the first 
compilation will take quite some time while the cache reindexes.
