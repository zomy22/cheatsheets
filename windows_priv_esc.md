### Windows Privilege Escalation CheatSheet

Gather system information:

```systeminfo```

Use output with wes-NG: https://github.com/bitsadmin/wesng


Check the OS version: 

```systeminfo | findstr /B /C:"OS Name" /C:"OS Version" ```

Check active network connections: 

```netstat -ano ```

To check for firewall settings: 

```
netsh firewall show state 
netsh firewall show config 
```

To check the scheduled tasks: 

``` schtasks /query /fo LIST /v ```

To check running processes linked to services: 

```tasklist /SVC ```

To check for running services: 

``` net start ```

To check for installed drivers: 

``` DRIVERQUERY ```

With the following command you can check for installed patches: 

``` wmic qfe get Caption,Description,HotFixID,InstalledOn ```
Search for interesting file names. 

The following command searches the system for files that contain ‘password’ in the filename: 

``` dir /s *password* ```

You can also search the content of files for specific keywords, such as the password. The following command searches for the keyword ‘password’ in files with the .txt extension: 

``` findstr /si password *.txt ```

Unquoted Service Paths 

```
wmic service get name,displayname,pathname,startmode |findstr /i "Auto" |findstr /i /v "C:\Windows\\" |findstr /i /v """ 
( icacls "C:\Program Files\Program" ) 
```

Modifying the binary service path 

To display services that can be modified by an authenticated user type: 

``` accesschk.exe -uwcqv "Authenticated Users" * /accepteula ```

AlwaysInstallElevated setting 

```
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated 

reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated  
```

Windows Exploit Suggester https://github.com/GDSSecurity/Windows-Exploit-Suggester.git