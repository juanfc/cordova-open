cordova-open
====

[![Build Status](https://travis-ci.org/disusered/cordova-open.svg)](https://travis-ci.org/disusered/cordova-open) [![Code Climate](https://codeclimate.com/github/disusered/cordova-open/badges/gpa.svg)](https://codeclimate.com/github/disusered/cordova-open) 

Forked https://github.com/disusered/cordova-open

I implemented file share to: <app>


> Open & Share audio, video, images and more with applications installed on the user's device.

<img src="https://raw.githubusercontent.com/disusered/cordova-open/docs/open.png" width="300px" />
<img src="https://github.com/juanfc/cordova-open/blob/develop/shareFile.png" width="300px" />

## Install

```bash
$git clone https://github.com/juanfc/cordova-open.git
$cordova plugin add  cordova-open --link

or

$cordova plugin add https://github.com/juanfc/cordova-open.git
```

## Usage open

```javascript
var open = cordova.plugins.disusered.open;

function success() {
  console.log('Success');
}

function error(code) {
  if (code === 1) {
    console.log('No file handler found');
  } else {
    console.log('Undefined error');
  }
}

function progress(progressEvent) {
  if (progressEvent.lengthComputable) {
    var perc = Math.floor(progressEvent.loaded / progressEvent.total * 100);
    // update UI with status, for example:
    // statusDom.innerHTML = perc + "% loaded...";
  } else {
    // download does not offer a length... just show dots
    /*
       if(statusDom.innerHTML == "") {
       statusDom.innerHTML = "Loading";
       } else {
       statusDom.innerHTML += ".";
       }
     */
  }
};

open('file:/storage/sdcard/DCIM/Camera/1404177327783.jpg', success, error, progress);
```

## Usage shareFile

```javascript
var open = cordova.plugins.disusered.shareFile;

function success() {
  console.log('Success');
}

function error(code) {
  if (code === 1) {
    console.log('No file handler found');
  } else {
    console.log('Undefined error');
  }
}

function progress(progressEvent) {
  if (progressEvent.lengthComputable) {
    var perc = Math.floor(progressEvent.loaded / progressEvent.total * 100);
    // update UI with status, for example:
    // statusDom.innerHTML = perc + "% loaded...";
  } else {
    // download does not offer a length... just show dots
    /*
       if(statusDom.innerHTML == "") {
       statusDom.innerHTML = "Loading";
       } else {
       statusDom.innerHTML += ".";
       }
     */
  }
};

open(cordova.file.externalCacheDirectory +fileName, success, error, progress);
```

## API
The plugin exposes the following methods:
*shareFile (Only for Android Api >=22)

```javascript
cordova.plugins.disusered.open(file, success, error, progress, trustAllCertificates)
```
```javascript
cordova.plugins.disusered.shareFile(file, success, error, progress, trustAllCertificates)
```

#### Parameters:
* __file:__ A string representing a URI
* __success:__ Optional success callback
* __error:__ Optional error callback
* __progress:__ Optional progress callback
* __trustAllCertificates:__ Optional, trusts any certificate when the connection is done over HTTPS.

#### Events:
* __pause:__ Opening files emits Cordova's pause event (Android only)
* __resume:__ Closing the file emits Cordova's resume event
* __open.success:__ File is found and can be opened
* __open.error:__ File not found, or no file handler is installed

## License



MIT © [Carlos Rosquillas](http://carlosanton.io)
