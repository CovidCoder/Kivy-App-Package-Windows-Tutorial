# How To Package a Simple Kivy App on Windows (With Pictures)


* Requirements: `Latest Kivy` installed and `PyInstaller 3.1+` (pip install pyinstaller or pip install --upgrade pyinstaller)


* Step 1: Make a folder and call it whatever you want and put it anywhere except where your .py file is. I personally just called it exefolder and put it next to the folder where my .py file is     https://imgur.com/6gYstCY.jpg


* Step 2: Change the directory of your command line shell (for example I'm using vscode) to the folder you just made. For me, I would type in my shell: `cd C:\Users\Tyler\PycharmProjects\exefolder`     https://imgur.com/2WDHWQi.jpg


* Step 3: Make a folder in the directory where your .py file is. I named mine kivyapp. Copy any files you used in your project into this folder. For me, I only have to copy my .py and .kv files     https://imgur.com/u8rscg3.jpg


* Step 4a: (If you would like to add an icon to your application, skip this step.) Now in your shell, type: `python -m PyInstaller --name YourAppName -w TheDirectroyToYour.pyFile` and hit enter. For example mine would be: `python -m PyInstaller --name EbayApp -w C:\Users\Tyler\PycharmProjects\Giraffe\kivyapp\kiv.py` (If you want the command prompt to run with your exe then delete -w)     https://imgur.com/XMSm49M.jpg


  Step 4b: To add an icon to your application, add a .ico file to the folder where the files you just copied are. (You can convert a picture into a .ico file at www.convertico.com.) Then in your shell type: `python -m PyInstaller --name YourAppName -w --icon TheDirectroyToYour.icoFile TheDirectoryToYour.pyFile` and hit enter. For example mine would be: `python -m PyInstaller --name EbayApp -w --icon C:\Users\Tyler\PycharmProjects\Giraffe\kivyapp\icon.ico C:\Users\Tyler\PycharmProjects\Giraffe\kivyapp\kiv.py` (If you want the command prompt to run with your exe then delete -w)     https://imgur.com/Tosto24.jpg


* Step 5: When that's done it should say `completed successfully`. Now go to the folder you made in `step 1` and right click the `.spec` file and open it with notepad (or any other text editor)     https://imgur.com/9HSbWNr.jpg


* Step 6: When you open your .spec file, it should look something like this: https://imgur.com/GSY0GX5.jpg Now at the top in the empty space right above `block_cipher = None` add in: `from kivy_deps import sdl2, glew` https://imgur.com/35isH5h.jpg


* Step 7: Now find the `coll = COLLECT(exe,` line and add: `Tree('ThePathToTheFolderYouMadeInStep3'),` Mine looks like: `Tree('C:\\Users\\Tyler\\PycharmProjects\\Giraffe\\kivyapp\\'),`     https://imgur.com/2AL1Bjv.jpg


* Step 8: Below that, look for the `a.datas,` line and below it add: `*[Tree(p) for p in (sdl2.dep_bins + glew.dep_bins)],` so that it's in between `a.datas,` and `strip=False,`     https://imgur.com/M9K3iv3.jpg


* Step 9: Save the file and close out of it. Lastly, go back into your shell and type: `python -m PyInstaller YourAppName.spec` and hit enter. Mine looks like: `python -m PyInstaller EbayApp.spec`     https://imgur.com/w3DMGF6.jpg


* Step 10: At some point it should say: `WARNING: The output directory "YourDirectory" and ALL ITS CONTENTS will be REMOVED! Continue? (y/N)` This is totally fine. Just press y then enter     https://imgur.com/N2TIBW8.jpg


* Step 11: After it's done building, your file will be in the folder you made in `Step 1`. Mine was in: `C:\Users\Tyler\PycharmProjects\exefolder\dist\EbayApp`     https://imgur.com/UcqGH8T.jpg


* Step 12: (Optional) You can create a shortcut and move it wherever you want. I cleaned up the folder a bit so it's easier for others to use the application. Before: https://imgur.com/9ywOD7E.jpg     After: https://imgur.com/MahWtV3.jpg


* Step 13: Open it up and everything should be working fine!     https://imgur.com/skO01hv.jpg


  And that's it! Enjoy!


  Source: https://kivy.org/doc/stable/guide/packaging-windows.html#packaging-a-simple-app
