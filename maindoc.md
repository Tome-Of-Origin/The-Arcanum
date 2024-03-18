# ⚔️ Overture Modding Introduction Doc ⚔️
  

🔗 Useful Drive Links: [GDrive from General Overture Discord](https://drive.google.com/drive/folders/1-6OE99_xrxty2DbdzXmK8mLyiBLtEfzo) | [GDrive from Private Overture Discord](https://drive.google.com/drive/folders/1oMdNPBkCTfFy2X3Eqjhs9Tc4X9nATI7i) | [GSheet with PKM Assets Breakdowns](https://docs.google.com/spreadsheets/d/17fVBGmIsLk_mxfGZ4LKKn_oE7Cpbfnmj0H5-MSsbe60/edit#gid=0) | [GDoc Version + To-Do List for Upscaling Project ](https://docs.google.com/document/d/1d7seimMkDWb9Cgr2VpIOJsEoj4mFA66W5IF6kntZ6Rs/edit?usp=sharing) 

Other links: [Reshade Presets](https://drive.google.com/drive/folders/194URm9VqBdZVKP6Hw7IQfPLINnWpIG7r?usp=drive_link) | [Overture Discord Invite](https://discord.gg/KpRAaW76ug)

  
______________


# 📋 Programs Needed

- [Python](https://www.python.org/downloads/): Needed to run Backyard Tools scripts. 
    
- [Backyard Tools](https://gitlab.com/backyardtools/overture/prototypes) + [Documentation](https://gitlab.com/backyardtools/overture/documentation/-/blob/master/formats/MFT.md?ref_type=heads) : Extract files, repackage them into the game.  
    

  

##### Optional: 

- [Visual Studio Code](https://code.visualstudio.com/docs/?dv=win64user): View code and structure in an organized manner
    
- [GIMP](https://www.gimp.org/downloads/devel/): Textures DDS Editing. Can export to any format. (Make sure to use development downloads!!!)
    
- [Waifux2:](https://github.com/lltcggie/waifu2x-caffe) To upscale textures.
    
- [Noesis](https://richwhitehouse.com/index.php?content=inc_projects.php): For Model Viewing, Export Textures from PKM. 

- [ImageMagick](http://www.imagemagick.org/): Batch image format conversion.    

  

______________

# 🔎 Upscaling Efforts

[Exported Textures (DDS, PNG)](https://drive.google.com/drive/folders/1IjHPkrBYuG6IcFgg4F_-0lD0JjEPuXCj?usp=drive_link) - [Upscaled Textures (DDS, PNG)](https://drive.google.com/drive/folders/1ijvuBLgude3Vx9zI38Ei6w50Yc4cDoYo) - [Final Files (PKM)](https://drive.google.com/drive/folders/13md3IVPYrbxsNWCAESPmMdxJEc2gkjhk?usp=drive_link) - [GDoc To-Do List](https://docs.google.com/document/d/1d7seimMkDWb9Cgr2VpIOJsEoj4mFA66W5IF6kntZ6Rs/edit?usp=sharing)

Original texture size: 1024x1024 - Upscaled: 2048x2048
To see current progress, check the To-Do Google Doc. It gets updated regularly.
     

______________

  

# 📝 Modding Files: Step by Step Guide

The files are packed into .PKM packages. To access the files you want to modify, you must unpack the original .PKM with Backyard Tools. We call this process dumping the files. Now we could replace them with anything we want. For the game to read the new files, we need to repackage them with the Backyard Tools, then place them within the game’s original folder.  

Here is a step by step guide:
# Windows Usage
1. Install python, and Backyard Tools. Links provided on [Programs Needed.](https://docs.google.com/document#heading=h.t9ckv9ke374r) 

2. Run this line of code from Visual Studio or the Windows Terminal.
   ```python .\unpkm.py "[Insert here your Overture pathing]\[.PKM file you want to dump]"```
   or
   ```py .\unpkm.py "[Insert here your Overture pathing]\[.PKM file you want to dump]```

   If one line of code doesn’t work, try the other, it depends on your python version. You can check by just typing “python” or “py” on your Windows Terminal, and it will send a line of command back for whichever of them works. [1]
  
   You can check where your Overture is installed from your Steam Library, just right click on the game > Manage > Open file location, and copy the path from the Windows Explorer. Usually, this path looks something like `C:\Program Files (x86)\Steam\steamapps\common\GG2\data\`. You must point to the data folder! 

   Known lists of assets by filename, and if they’re already dumped or not, is [here](https://docs.google.com/document#heading=h.wfgf8e7ibsq8).

   It will create a folder with the name of the dumped PKM file with the contents inside, in the same place as the Backyard Tools folder. (Or more specifically, wherever unpkm.py is located.) 

   If you experience an error code, it will tell you where it’s looking for the script, so try moving Backyard Tools there. If the error persists, move unpkm.py out of the folder. 

3. Modify files at will. Ex. Master textures are DDS files which you can edit/export with GIMP.

4. Replace files in the folder dumped with step 2. Ex. Backyard Tools made folder X, so you should replace the file in this folder before repackaging. 

5. Repack with Backyard Tools. 

   ```python .\unpkm.py -o "[Directory you want the file output to]\[Desired name for .PKM file]" "[Directory of dumped PKM file on step 2]" -t 3 -vf```
   or
   ```py .\unpkm.py -o "[Directory you want the file output to]\[Desired name for .PKM file]" "[Directory of dumped PKM file on step 2]" -t 3 -vf```

   Note about TDxxx.PKMs:
   The textures in these PKMs seem to use a dds texture flag named “DDSCAPS2_VOLUME” (they are not volume textures, so they seem to hijack that flag internally for something?), when repacking TDxxx PKMs, use the command(s) from the above section, but also add -vf at the end of the command when repacking them. (Not needed for dumping, only repacking)

6. Replace new PKM on your game folder. Usually `C:\Program Files (x86)\Steam\steamapps\common\GG2\data\`. We recommend backing up the original files somewhere else before any modification, to keep them safe. If something breaks and you don’t have a backup, you will have to clean install via Steam to revert back the changes. (You can also use the validate files option, but it’s not guaranteed to work, so keep backups anyway.)

7. *Hope it doesn't explode, and pray to your preferred deity.* If anything went wrong (game won't open, textures didn't change, textures went, etc), close Overture, go back into the files, and replace the "new" PKM you made with the original PKM backup, then launch the game. If whatever issue you had is solved, that means something went wrong when you made/repacked the new PKM. If you’re still getting issues, that means it's a problem with Overture itself, and might require a clean install. Either replace the folder with your backup, or right click on your Steam Library > Manage > Uninstall, then Install again from scratch. You can also try Steam Library > Manage > Validate Files to restore  the game to initial state, but it’s not guaranteed to work.

  
  
   [1] Example of how to check if your version of python runs with either command. ![](https://lh7-us.googleusercontent.com/QTtIDTby4Rn2d7aC4Agm1ke5ywjOOah7Hv76q1zjKCBQUKriVtgQpomBk12fgGC-x-N9WZ9LmaGUSxx6nYWTvpv56cOyZLE1c29oEsT_0tjKuaccJ0oZabMA7bg0w1MlywnIWhWRqomkK7IxFgvberQ)

# Linux
This is the Linux usage section for packing/repacking PKMs.

1. Install Python, GIMP and Git
   You can use your preferred package manager, for example with pacman + yay (you'll want to use the git build of GIMP, as normal crashes from textures in the TDxxx PKMs).
   Run:
   `sudo pacman -S python git`
   `yay -S gimp-git`
   in your preferred terminal program.

2. Clone BackyardTools
   I recommend creating a folder for Overture modding work such as `~/overturedumps` , and also symlinking the overture game folder to something like `~/overture` for easy access.
   You'll also need to clone the prototypes BackyardTools repo:  ```
   cd ~/ && git clone https://gitlab.com/backyardtools/overture/prototypes

3. Using BackyardTools to dump a PKM
   If you're using this guide, you likely want to dump and possibly edit files in PKMs.
   This can be done by running
   `python ~/prototypes/unpkm.py Path/To/PKM.PKM`
   with path changed accordingly, preferrably in your working folder, e.g. `~/overturedumps`.
   It will create a folder with a bunch of .DUMMY files and the actual files (you'll recognize them by extension, likely).
   If they're DDS files, you can use GIMP, then use overwrite.
   
4. Repacking with BackyardTools
   Now, to save your edits:
   `python -t 3 ~/prototypes/unpkm.py path/to/dumped/pkm/ path/to/output/pkm.PKM`
   Make sure to use -vf flag when packing TDxxx.PKMs!!!!!

5. Copy output PKM to overture
   Run `cp path/to/outputted/pkm.PKM path/to/overture/data/`

6. Run the game.
   6.1. Optional step: Pray to your deity of choice
   If you encounter any issues, you can ask in the Overture discord.
______________

  

### 📝 Misc notes

- We’ve tried upscaling textures, and doubling the pixels of them for it, and the game recognizes them and runs them flawlessly. x2 is enough, you can’t really tell the difference with x4 upscaling. (x4 upscaling also makes the files as big as the Entire Game, so…
    
- If you dump folders, zipping them and uploading them to the drive is highly appreciated. Please keep files organized! The game does not have anything labeled otherwise, so finding things is hard. 
    
- If the instructions are unclear, please mention so! We’ll do our best to keep it easy to understand :)

  
______________

# 🗂️ PKM Dumping List

If you want to know what assets are inside each PKM, [refer to this Excel](https://docs.google.com/spreadsheets/d/17fVBGmIsLk_mxfGZ4LKKn_oE7Cpbfnmj0H5-MSsbe60/edit#gid=0). If you’re dumping files, please help us fill the documentation! It’d be great help.

##  📝 List of Known PKM Assets


AF00 = Mix of items, normals. These have a lot of .AFB files idk how to open them 

AF10 = Stage normals?

AF11 = Servant normal…?

AF12 = A sword’s normal…?

AF13 = One (1) normal idk

AF14 = It has 2 textures idk theyre. red


AF20 = Izuna Normals

AF21 = Dr.Paradigm Normals

AF22 = Sol Badguy Normals

AF23 = EX Sol Normals

AF24 = Sin Kiske Normals

AF25 = Valentine Normals

AF26 = Raven Normals

AF27 = Ky Kiske Normals

AF40 = Dizzy

AF41 = That Man

AF42 = Mecha Valentine

AF43 = FINAL BOSS


OUTGAMERESULT, OUTGAMEBATTLEINTRO, OUTGAME, OUTGAMETITLE, COCKPIT = UI. Most UI is in COCKPIT and OUTGAME, which are in data\cockpit and data\outgame respectively



______________

## 📝 Credits

### Jill - Backyard Tools Creator
Backyard Tools allows us to mod anything at all into the game, so if it weren’t for Jill, we wouldn’t be here. Big props; if you want to support them, here’s their [Ko-Fi](http://ko-fi.com/jillcrungus)! Here’s [their site](https://jillcrungus.com/) as well, with other socmed links inside.

### Hisami
The pink sol mod guy. Creator of GitHub organization “TomeOfOrigin”. Very active member of the community. [GitHub](https://github.com/youmukonpaku1337) - [YT Channel](https://www.youtube.com/channel/UCOHGrQf_8o57I9hg0G1DSrA). 

### S
Ky lover Artist who wanted to see him in HD so much he kickstarted the upscaling project + this doc. [Guilty Gear Twitter](https://twitter.com/SparksRoar - [Twitch](https://www.twitch.tv/milkywaybnuuy) - [Ko-Fi](https://ko-fi.com/midoriyaizuhugs).

### Elk
Self-proclaimed Patron Saint of Guilty Gear Overture, and Ky Enthusiast. Keeps up documentation and is working on guides for the game. [Twitter](https://twitter.com/wolfadoodle). 

### Fel
Currently working on GUI for Backyard Tools. [Twitter](https://twitter.com/oathinfel).

…And obviously, [Overture Discord](https://discord.gg/KpRAaW76ug), and all of the people who have paved the way and keep the community alive. Thank you!
