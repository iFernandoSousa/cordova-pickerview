# Cordova PickerView Plugin #
by [Olivier Louvignes](http://olouv.com)

## DESCRIPTION ##

* This plugin provides a simple way to use the `UIPickerView` native component from iOS.

* This plugin is built for Cordova >= v2.1.0 with ARC.

* There is a `Sencha Touch 2.0` plugin to easily leverage this plugin [here](https://github.com/mgcrea/sencha-touch-plugins/blob/master/CordovaPicker.js)

## SAMPLE PROJECT GENERATION ##

You can generate a sample XCode project by running `samples/ios/create.sh` from the root of the repository. You will have to manually add the `ActionSheet` folder to Xcode (see step 2).

## PLUGIN SETUP FOR IOS ##

Using this plugin requires [Cordova iOS](https://github.com/apache/incubator-cordova-ios).

1. Make sure your Xcode project has been [updated for Cordova](https://github.com/apache/incubator-cordova-ios/blob/master/guides/Cordova%20Upgrade%20Guide.md)
2. Rename the `src/ios` folder to `PickerView`, drag and drop it from Finder to your Plugins folder in XCode, using "Create groups for any added folders"
3. Add the .js files to your `www` folder on disk, and add reference(s) to the .js files using `<script>` tags in your html file(s)


    `<script type="text/javascript" src="/js/plugins/PickerView.js"></script>`


4. Add new entry with key `PickerView` and value `PickerView` to `Plugins` in `Cordova.plist/Cordova.plist`

## JAVASCRIPT INTERFACE (IOS/ANDROID) ##

    // After device ready, create a local alias
    var pickerView = window.plugins.pickerView;

    // Basic with title & defaultValue selected
    var slots = [
        {name: 'foo', value: 'baz', data: [
            {value: 'foo', text: 'Displayed Foo'},
            {value: 'bar', text: 'Displayed Bar'},
            {value: 'baz', text: 'Displayed Baz'}
        ]}
    ];
    /*pickerView.create('Title', slots, function(selectedValues, buttonIndex) {
        console.warn('create(), arguments=' + Array.prototype.slice.call(arguments).join(', '));
    });*/

    // Complex example with 2 slots
    var slots = [
        {name : 'limit_speed', title: 'Speed', width: 140, data : [
            {text: '50 KB/s', value: 50},
            {text: '100 KB/s', value: 100},
            {text: '200 KB/s', value: 200},
            {text: '300 KB/s', value: 300}
        ]},
        {name : 'road_type', title: 'Road', width: 160, data : [
            {text: 'Highway', value: 50},
            {text: 'Town', value: 100},
            {text: 'City', value: 200}
        ]}
    ];
    pickerView.create('', slots, function(selectedValues, buttonIndex) {
        console.warn('create(), arguments=' + Array.prototype.slice.call(arguments).join(', '));
    }, {style: 'black-opaque', doneButtonLabel: 'OK', cancelButtonLabel: 'Annuler', sourceRect: [100.0, 100.0, 20.0, 20.0], arrowDirection: 'up'});

    // Set values after create
    setTimeout(function() {
        pickerView.setValue({limit_speed: 100, road_type: 200}, {animated: true});
    }, 1000);

* Check [source](https://github.com/mgcrea/cordova-pickerview/tree/master/www/PickerView.js) for additional configuration.

## BUGS AND CONTRIBUTIONS ##

Patches welcome! Send a pull request. Since this is not a part of Cordova Core (which requires a CLA), this should be easier.

Post issues on [Github](https://github.com/mgcrea/cordova-pickerview/issues)

The latest code (my fork) will always be [here](https://github.com/mgcrea/cordova-pickerview/tree/master)

## LICENSE ##

    The MIT License

    Copyright (c) 2012 Olivier Louvignes

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.

## CREDITS ##

Contributors :

* [Olivier Louvignes](http://olouv.com), author.

Inspired by :

* [Ext.picker.Picker Sencha Touch 2.0 class](http://docs.sencha.com/touch/2-0/#!/api/Ext.picker.Picker)
