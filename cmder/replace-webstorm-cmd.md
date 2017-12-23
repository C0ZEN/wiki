# You can use cmder instead of cmd in Webstorm

This is far better option that the actual cmd.

**Notes :** 

There is a problem when the cmd is opened.  
Occurs only when the project is on another disk.  
The path is not the one of your current project.  
You should always `cd` to set the correct path.  

**To shortcut the process :**

- Open the `npm cli` 
- Right-click on the first line (which is the path of your package.json)
- Left-click on `copy path`
- Open the cmd
- Go to your project disk like `g:`
- `cd ` + `CTRL + V` to set the new path
- `CTRL + Z` to remove `package.json` end string
- `Enter` and you are good to go

### Set the environment variable

Set an environment variable called `CMDER_ROOT` to your root Cmder folder (in my case D:\Program Files (x86)\cmder).  
It seems to be important that this does not have quotes around it because they mess with concatenation in the init script.

### Change the cmd path in Webstorm

In your Webstorm terminal settings, use `"cmd.exe" /k ""%CMDER_ROOT%\vendor\init.bat""` as the Shell path.  
The double-double-quotes are intentional, as they counteract the missing double quotes in the environment variable.

**To shortcut the process :**

- `CTRL + ALT + S`
- Enter the word "terminal" in the search field
- Select the entry "Tools/Terminal"
- Paste `"cmd.exe" /k ""%CMDER_ROOT%\vendor\init.bat""` in the Shell path
