[![npm](https://img.shields.io/npm/v/nativescript-drawingpad.svg)](https://www.npmjs.com/package/nativescript-drawingpad)
[![npm](https://img.shields.io/npm/dt/nativescript-drawingpad.svg?label=npm%20downloads)](https://www.npmjs.com/package/nativescript-drawingpad)

# NativeScript-DrawingPad :pencil:
NativeScript plugin to provide a way to capture any drawing (signatures are a common use case) from the device.
You can use this component to capture really anything you want that can be drawn on the screen. Go crazy with it!!!

*Formally this plugin was **nativescript-signaturepad**, to improve visiblity and adoption it has been renamed.*

## Samples

Android |  iOS 
-------- | ---------
![Sample1](screens/androidDrawing.gif) | ![Sample2](screens/iosDrawing.gif)

#### Native Libraries: 
Android | iOS
---------- | -----------
[gcacace/android-signaturepad](https://github.com/gcacace/android-signaturepad) |  [SignatureView](https://cocoapods.org/pods/SignatureView)

## Installation
From your command prompt/termial go to your app's root folder and execute:

`npm install nativescript-drawingpad`

## Usage
#### XML:
```XML
<Page xmlns="http://schemas.nativescript.org/tns.xsd" xmlns:DrawingPad="nativescript-drawingpad" loaded="pageLoaded">
    <ActionBar title="NativeScript-DrawingPad" color="#fff" backgroundColor="#03A9F4" />
    <ScrollView>
        <StackLayout>
        
            <DrawingPad:DrawingPad 
            height="400" 
            id="drawingPad" 
            penColor="#ff4081" penWidth="3" />
            
        </StackLayout>
    </ScrollView>
</Page>
```

#### JS:
```JS
var frame = require("ui/frame");

// To get the drawing...
function getDrawingAsPic(args) {
    // get reference to the drawing pad
    var pad = frame.topmost().currentPage.getViewById("drawingPad");
    // then get the drawing (Bitmap on Android) of the drawingpad
    var drawingImage;
    pad.getDrawing().then(function(data) {
        console.log(data);
        drawingImage = data;
    }, function(err) {
        console.log(err);
    })
}
exports.getDrawingAsPic = getDrawingAsPic;

// If you want to clear the signature/drawing...
function clearUserDrawing(args) {
    var pad = frame.topmost().currentPage.getViewById("drawingPad");
    pad.clearDrawing();
}
exports.clearUserDrawing = clearUserDrawing;
```

## Attributes
**penColor - (color string)** - *optional*

Attribute to specify the pen (stroke) color to use.
 
**penWidth - (int)** - *optional*

Attribute to specify the pen (stroke) width to use.

## Methods

**getDrawing()** - Promise *(returns image if successful)*

**clearDrawing()** - clears the drawing from the DrawingPad view.

#### *Android Only*

- **getTransparentDrawing()** - Promise (returns a bitmap with a transparent background)
- **getDrawingSvg()** - Promise (returns a Scalable Vector Graphics document)

