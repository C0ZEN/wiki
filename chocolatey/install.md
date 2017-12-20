# Chocolatey install

You can run the following command to install Chocolatey:

`@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`

### Check if chocolatey is already installed

Run the command below to get the current version of chocolatey.

`chocolatey -v`

If chocolatey is installed, the cmd will prompt the current version like `0.10.8`.

### Goes wrong ?

You can check-out the [Chocolatey site](https://chocolatey.org/install) to ensure that the command is still the same.
