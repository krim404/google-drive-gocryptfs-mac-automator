# google-drive + gocryptfs + mac-automator
This workflow is for improving stability of a gocryptfs mount stored on a google drive (file-stream) on a mac.  
  
## What is this workflow doing?
It will search for all `gocryptfs.diriv` files in the selected target and will set them to "make available offline" using the finder menu.  
  
## Why?
Especially when doing big directory operations (like scanning all folders for a file) gocryptfs will - at some point - time out when google drive does not deliver the diriv file in a short amount of time. This is especially prolematic when its an automated task, as the fuse mount will simply stop working till remounted. By setting the diriv files to "available offline" this will happen a lot less.  
  
## How does it work?
As Google Drive does not offer a command line tool to set a file to "available offline" and needs to be set using the mac gui - this tool will have to walk through all sub-directorys and take over the Finder by selecting the diriv file, issuing a context menu command and press a few buttons to select "available offline". It will also create a file in `~/scripts` called `gc.done` used as a cache file to remember, which files are already set - this prevents a second run to start from scratch. 

## Optimization / Customization
Based on your internet and computer speed, you may have to change the delay commands. Also this script is configured with english google drive in mind. In case your local languages context menu to make the file available does not start with the text `Offline` you have to edit `keystroke "Offline"` in this script to your localization. 

