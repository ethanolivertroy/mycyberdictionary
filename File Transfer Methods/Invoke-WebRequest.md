On Windows, you can download files using the "Invoke-WebRequest" PowerShell cmdlet. Here's an example of how to use it:

```
Invoke-WebRequest -Uri "http://example.com/file.zip" -OutFile "C:\Downloads\file.zip"
```

In this example, replace "http://example.com/file.zip" with the URL of the file you want to download and replace "C:\Downloads\file.zip" with the path and filename where you want to save the downloaded file.

You can also use the "curl" command in PowerShell to download files. To use "curl", you need to install it first by downloading and installing the "curl" executable for Windows. Once installed, you can use it like this:

```
curl -o "C:\Downloads\file.zip" "http://example.com/file.zip"
```

In this example, replace "C:\Downloads\file.zip" with the path and filename where you want to save the downloaded file, and replace "http://example.com/file.zip" with the URL of the file you want to download.

Another option is to use a GUI-based download manager like Internet Download Manager (IDM) or Free Download Manager (FDM) to download files on Windows. These download managers have a user-friendly interface and offer features like resuming interrupted downloads, scheduling downloads, and more.