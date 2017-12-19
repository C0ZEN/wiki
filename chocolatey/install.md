# Chocolatey install

You can run the following command to install Chocolatey:

`@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`

### Goes wrong ?

You can check-out the [Chocolatey site](https://chocolatey.org/install) to ensure that the command is still the same.