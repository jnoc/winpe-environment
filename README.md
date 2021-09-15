# WinPE Environment

## The Brief
I was asked to build upon a WinPE that was being used to upgrade Intel ME firmware, check for a BIOS password, apply a base BIOS configuration (with password), then check for a BIOS flash upgrade on HP workstations that were being used in the company. My task was to incorporate Dell workstations into this process.

From this I logically worked through in steps what needed to be done. First I spoke to the administrator that had built the environment, written the python scripts and got a feel for what I should be doing. From this I learnt I needed to:

- Build a new WinPE arm64 environment (the previous one was ~750MB borderline too big)
- Find all the drivers used for both vendors in a WinPE image
- Find the correct Intel ME firmware versions for both vendors and models.
- Understand how I could use Dell management tools to update the models via scripts.
- Deploy the WinPE via a netboot server so machines can boot to PXE

## The product
 The outcome of this project was a working WinPE  environment that loaded on the target machine. A python script is started by the `startnet.cmd` batch script which runs a check via `wmic` to get the machine vendor. This was then processed  to determine what course of updates the machine needed to go through. As I was using the scripts previously made for the HP this was the best route to making sure the environment was finished in good time.  Thus the resulting outcome within the WinPE environment: 
 
![The WinPE process](https://i.imgur.com/32VCR0W.jpg)
