<div align="center">

## Ellis verson of Jasosn´s apid\.pas


</div>

### Description

ist a colection of jason´s apis and some more added by me =)
 
### More Info
 
Just add the pas to ur project and add apis.pas dir to ur envirement for extra help and add apis to uses... like apis.<command>();....... copy the code and past it in a unit named apis.pas

all sorts of stuff


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Erik Ellis](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/erik-ellis.md)
**Level**          |Intermediate
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |Delphi 7, Delphi 6, Delphi 5
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__7-42.md)
**World**          |[Delphi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/delphi.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/erik-ellis-ellis-verson-of-jasosn-s-apid-pas__7-948/archive/master.zip)

### API Declarations

Well... jason is the auther of this pas file so most of the credits are going to him


### Source Code

```
{
 * unit coded by J, Remake by Ellis
 * executes aload of win API calls
 *
 *  Version 1 of unit has folowing working functions
 * OpenCD
 * OpenBrowser
 * Hide Start Button
 * Show Start Button
 * Hide Start Bar
 * Show Start Bar
 * Disable Desktop
 * Enable Desktop
 *
 *  Version 1.1 updates
 * Hide Shortcuts that are on desktop
 * Disable Start bar
 * Enable Start bar
 * Set monitor on Standby
 * Log Users Off
 * Start screenSaver
 * Send Messages
 *
 *  Added by Ellis
 * Run a program with params (function)
 * Remade OpenBrowser to function
 * Added CloseCD
 * Added FileName (converting dir+ext to only file name c:/test.txt = test) (function)
 * Added Google (function)
 * Added Astalavista (function)
}
unit apis;
interface
uses
    Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
    Dialogs, ScktComp, StdCtrls, ShellAPI, MMSystem;
procedure OpenCD;
procedure CloseCD;
function OpenBrowser(website: string): string;
procedure HideStart;
procedure ShowStart;
procedure HideBar;
procedure ShowBar;
procedure DisableDesk;
procedure EnableDesk;
procedure HideShort;
procedure ShowShort;
procedure Monitor;
procedure Saver;
procedure DisableBar;
procedure EnableBar;
procedure LogOff;
procedure Reboot;
function Runapp(prog, params: string): string;
function FileName(Value: String): String;
function Google(find: string): string;
function altavista(find: string): string;
implementation
function altavista(find: string): string;
begin
 ShellExecute(application.handle, 'Open', PChar('http://www.altavista.com/web/results?q=' + find), nil, nil, SW_SHOW);
end;
function Google(find: string): string;
begin
 ShellExecute(application.handle, 'Open', PChar('http://www.google.com/search?q=' + find), nil, nil, SW_SHOW);
end;
function FileName(Value: String): String;
begin
 Result := ExtractFileName(Value);
 if ExtractFileExt(Value) <> '' then
   Result := Copy(ExtractFileName(Value), 1,
        Pos(ExtractFileExt(Value), ExtractFileName(Value))-1);
end;
procedure OpenCD;
begin
    MciSendString('Set CDAudio Door Open', nil, 0, application.Handle ); //gotta add MMSystem to uses
end;{procedure}
procedure CloseCD;
begin
    MciSendString('Set CDAudio Door Closed', nil, 0, application.Handle ); //gotta add MMSystem to uses
end;{procedure}
function Runapp(prog, params: string): string;
begin
    ShellExecute(0,'open',PChar(prog),pchar(params),'',SW_SHOWNORMAL);
end; {procedure}
function OpenBrowser(website: string): string;
begin
    ShellExecute(application.handle, 'Open', PChar(website), nil, nil, SW_SHOW); //gotta add ShellAPI to uses
end;{procedure}
procedure HideStart;
begin
    ShowWindow( FindWindowEx(FindWindow('Shell_TrayWnd', nil), 0, 'Button', nil), SW_HIDE);
end;{prcedure}
procedure ShowStart;
begin
    ShowWindow( FindWindowEx(FindWindow('Shell_TrayWnd', nil), 0, 'Button', nil), SW_SHOW);
end;{prcedure}
procedure HideBar;
begin
    ShowWindow( FindWindow('Shell_TrayWnd', nil), SW_HIDE);
end;{procedure}
procedure ShowBar;
begin
    ShowWindow( FindWindow('Shell_TrayWnd', nil), SW_Show);
end;{procedure}
procedure DisableDesk;
begin
    EnableWindow( FindWindowEX( FindWindow('Progman', nil), 0, 'ShellDll_DefView', nil), False);
end;{procedure}
procedure EnableDesk;
begin
    EnableWindow( FindWindowEX( FindWindow('Progman', nil), 0, 'ShellDll_DefView', nil), True);
end;{procedure}
procedure HideShort;
begin
    ShowWindow( FindWindowEx( FindWindow('Progman', nil), 0, 'ShellDll_DefView', nil), SW_HIDE);
end;{procedure}
procedure ShowShort;
begin
    ShowWindow( FindWindowEx( FindWindow('Progman', nil), 0, 'ShellDll_DefView', nil), SW_SHOW);
end;
procedure Monitor;
begin
    SendMessage(application.Handle, WM_SYSCOMMAND, SC_MONITORPOWER, 0);
end;{procedure}
procedure Saver;
begin
    SendMessage(application.Handle, WM_SYSCOMMAND, SC_SCREENSAVE, 1);
end;{procedure}
procedure DisableBar;
begin
    EnableWindow( FindWindow('Shell_TrayWnd', nil), FALSE);
end;{procedure}
procedure EnableBar;
begin
    EnableWindow( FindWindow('Shell_TrayWnd', nil), TRUE);
end;{procedure}
procedure LogOff;
begin
    ExitWindowsEx(EWX_LOGOFF, 0);
end;{procedure}
procedure Reboot;
begin
    ExitWindowsEX(EWX_REBOOT, 0);
end;{procedure}
end.
```

