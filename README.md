# AmosPro-Coloured-context-patch
Patch to make Amospro editor provide context aware coloured text for easier reading.

WHAT DOES IT DO?
================

This set of patches adds syntax specific colouring to the main editor window. It allows you to customize which things use which colours for an easier to read making codind and bigfixing that much easier. It also makes the editor background colour black, giving you another palette colour to use for text. One final thing it does is disable the flashing cursor in the editor and now uses colour 7 for that.

HOW DOES IT WORK?
=================

This patches the official source code and then recompiles new EXEs to replace your existing ones.
 
HOW DO I INSTALL IT?
====================

There are some replacement files in the 'Compiled EXEs' folder you can just drop in but there's also the patches themselves and the compile commands to do this manually.

Firstly, BACK UP!
Go backup your AMOSPro install folder so you can always restore things
Then go backup your amos configs in S:

Make sure you have python installed to apply the patch

Get and unpack to a folder, the amospro official source. https://github.com/AOZ-Studio/AMOS-Professional-Official

With the Amospro official source unpacked into a folder, and the contents of this zip also in there....

Patch the 3x .s files with the command "python apply_all.py"
You should see three patched responses and ok. It will have made backups of the .s files as well.

Once the patch shows ok and it has successfully patched the three files, you can compile the source to executable.

Copy the +Lequ.s out of the 'AMOSPro Sources' folder to the main folder with the other .s files, its needed there.

vasmm68k_mot.exe -devpac -nocase -w -Fbin -o Amospro_Editor_config +Editor_Config.s
You should see a byte response to how big the file is if its compiled successfully.

vasmm68k_mot.exe -devpac -nocase -w -Fhunkexe -o AMOSPro_Editor +Edit.s
You should see another byte response which tells you the file has compiled correctly

Copy AMOSPro_Editor and AMOSpro_Editor_config you just created to your Amospro APSystem folder. (you can back these two files up locally first if you wish)

Copy the Editor_Config.AMOS into your root Amospro install folder. 

HOW DO I USE IT?
================

Start Amospro in the usual way. It should all look and appear normal. Type some commands or load a program. You should see syntax specific colours in the editor window which also now has a black background. 

Now, to configure this and specify which things use which colours, right mouse hold to call up the menu, go to CONFIG, then SET EDITOR, then Colour Palette. Here you can (as before) specific which RGB values each palette entry has. New here is the PENS button (or press P). This takes you to a second screen where you can select which syntax type has which palette entry. ESC cancels, RETURN accepts, P DEFAULTS. Once back at the palette menu, click the quit button. You should now see editor refresh and your changes are active.
Importantly, before you quit Amospro, you must save config or save default config to fix these changes in place. otherwise it'll be how you started up next time.....

I would also recommend changing the default resource banks to use a less complicated interface as you will be wanting as many palette entries as you can for syntax. I have included a set of replacement resource banks but you can paint your own by editing the system IFFs in amos and running them through the resource bank maker.




