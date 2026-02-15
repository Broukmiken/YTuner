
**********************************************************
HOW TO COMPILE Ytuner 1.2.6 in x86_64-win64

**********************************************************

coffeegreg decided to remove his windows version of his tool, because of issues with windows defender and antivirus from many customers

it took me many hours and help from this forum to finally compile it by myself

https://forum.lazarus.freepascal.org/index.php/topic,73458.0.html

so... here we go :)



**********************************************************

*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-

Download and install: 7zip

https://www.7-zip.org/download.html

https://www.7-zip.org/a/7z2600-x64.exe



*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-

Download and install: fpcupdeluxe


https://github.com/LongDirtyAnimAlf/fpcupdeluxe/releases/tag/v2.4.0h

fpcupdeluxe-x86_64-win64.exe

choose:
FPC version 3.3.1

Lazarus stable

click install/update FPC+Lazarus
i take some time, be patient
read carefully at the end of the installation:
"Fpcupdeluxe has created a desktop shortcut to start Lazarus."
so, launch this shortcut


*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-

download indylaz source code:

https://github.com/IndySockets/Indy/releases/tag/Indy-10.6.3.13

unzip somewhere.

in Lazarus previously launched, go to Package/open package file (.lpk)
browse to the "lib" directory of indylaz directory

in the new tab opened, go to "use" and then select "install"
choose 'yes" when prompted to rebuild Lazarus

many messages in the console (green,yellow) but Don't care

Lazarus will relaunch



*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-


download ytuner 1.2.6 source code:

https://github.com/coffeegreg/YTuner/releases/tag/1.2.6

and unzip

1/
go into "script" directory and run zip-sql.bat
you should get many zip files in "res" directory and a sql.rc file

if not ,it's because 7z.exe isn't in your 
folder to the path environment variable in Windows 11
you can search google, How to set a folder to the path environment variable in Windows 11

by example:

https://www.wikihow.com/Change-the-PATH-Environment-Variable-on-Windows

OR:

edit with Notepad or notepad++ the bat file,and

replace 7z.exe by the path of 7z.exe

and notice to add " before and after the path

my 7.exe is here:

C:\Program Files\7-Zip\7zip.exe

so,

FOR %%i IN (..\src\sql\*.sql) DO "C:\Program Files\7-Zip\7z.exe" a "..\res\%%~ni.zip" "%%i"

then run the bat file

*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-

in Lazarus :

1/
go to file, open, and browse to "common.pas" located in YTuner-1.2.6\src

line #356, replace:

Read(Buffer,Size);

by

Read(Buffer[0],Size);

=>then save the file (file then save)

2/
go to file, open, and browse to "translator.pas" located in YTuner-1.2.6\src

line #83 , replace:

case Integer(LUnicode.Words[0]) of

by

case WOrd(LUnicode {.Words[0]}) of

=>then save the file (file then save)


3/

go to file, open, and browse ytuner direcdtory and select : ytuner.lpi

then choose " open project"

**********************************************************


now, go to Run, compile many modes and just get "Release win64.."

and get your compiled file ytuner.exe in \bin\Release\x86_64-win64

you can directly download my compiled file in release if you don't want to waste your time and just use this great Ytuner :)

thanks Coffeegreg for your tool


tip :

if you closed Lazarus, you can found it and run it from this shortcut:

Lazarus_fpcupdeluxe.bat

located in C:\fpcupdeluxe

