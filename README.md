

A File Opener Plugin for Cordova (The Original Version)
==========================
This plugin will open a file on your device file system with its default application.

Current Version: 2.0.2
----------------

Requirements
-------------
- Android 4 or higher / iOS 6 or higher / WP8
- Cordova 3.0 or higher

Installation
-------------
    cordova plugin add https://github.com/Edc-zhang/cordova-plugin-file-opener2-android7.0
    
Usage
------
    cordova.plugins.fileOpener2.open(
        filePath, 
        fileMIMEType, 
        {
            error : function(){ }, 
            success : function(){ } 
        } 
    );

Examples
--------
Open an APK install dialog:

    cordova.plugins.fileOpener2.open(
        '/sdcard/Download/gmail.apk', 
        'application/vnd.android.package-archive'
    );
    
Open a PDF document with the default PDF reader and optional callback object:

    cordova.plugins.fileOpener2.open(
        '/sdcard/Download/starwars.pdf', // You can also use a Cordova-style file uri: cdvfile://localhost/persistent/Download/starwars.pdf
        'application/pdf', 
        { 
            error : function(e) { 
                console.log('Error status: ' + e.status + ' - Error message: ' + e.message);
            },
            success : function () {
                console.log('file opened successfully'); 				
            }
        }
    );


Additional Android Functions
-----------------------------
####The following functions are available in Android platform

###.uninstall(_packageId, callbackContext_)
Uninstall a package with its id.

    cordova.plugins.fileOpener2.uninstall('com.zynga.FarmVille2CountryEscape', {
        error : function(e) {
            console.log('Error status: ' + e.status + ' - Error message: ' + e.message);    
        },
        success : function() {
            console.log('Uninstall intent activity started.');
        }
    });

###.appIsInstalled(_packageId, callbackContext_)
Check if an app is already installed.

    cordova.plugins.fileOpener2.appIsInstalled('com.adobe.reader', {
        success : function(res) {
            if (res.status === 0) {
                console.log('Adobe Reader is not installed.');
            } else {
                console.log('Adobe Reader is installed.')
            }
        }
    });
