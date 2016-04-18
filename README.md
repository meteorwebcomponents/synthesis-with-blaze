> UNMAINTAINED

# Synthesis-Blaze is Meteor + Polymer + Blaze


## Installation

`meteor add mwc:synthesis-blaze`

synthesis is a meteor 1.3+ package. for 1.2 support use [mwc:compiler](https://github.com/meteorwebcomponents/compiler)

You can optionally use these packages from meteorwebcomponents

* [mwc:mixin](https://github.com/meteorwebcomponents/mixin) -  Polymer data package.
* [mwc:router](https://github.com/meteorwebcomponents/router) - Flowrouter with polymer.
* [mwc:layout](https://github.com/meteorwebcomponents/layout) - Polymer layout renderer.


## Usage

Define your elements in the client folder.

you can add js in separate file or you can add it inside the element html file using script tag.

### Use .sy.html extension for synthesis components.

```html
<!-- imports/test-element.sy.html -->
<dom-module id="test-element">
  <template>
  <link rel="stylesheet" href="test-element.css"> <!--converted to style tag-->
    <paper-button on-click="showNickName">
      Show nickname
    </paper-button>
    <p>
      Name : {{name}}
    </p>
    <div id="nnDiv" hidden="{{nndHidden}}">
      Nickname: {{ nickname }}
    </div>
  </template>
</dom-module>
```
```css
/*imports/test-element.css*/
paper-button{
color:red;
}
```
```js
// imports/test-element.js
import './test-element.sy.html';

Polymer({
  is:"test-element",
  properties:{
    name:{
      type:String,
      value:"Arun Kumar"
    },
    nickname:{
      type:String,
      value:"tkay"
    },
    nndHidden:{
      type:Boolean,
      value:true
    }
  },
  showNickName: function () {
    this.nndHidden = false;
  }
})


```

```html
<!-- client/index.html (you can use any filename) -->
<head>
  <title>Synthesis</title>
  <!-- include the webcomponents js file -->
  <script src="/bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
  
  <!-- import web components -->
  <link rel="import" href="/bower_components/polymer/polymer.html"/>
  <link rel="import" href="/bower_components/paper-button/paper-button.html"/>
</head>

<body class="fullbleed">
  <h1>Synthesis is Meteor + Polymer!</h1>
  <test-element></test-element>
</body>
```
```js
// client/index.js
import '../imports/test-element.js';

```

Add your bower_components inside public folder.

A sample bower.json (public/bower.json)

```json
{
  "dependencies": {
    "iron-elements": "PolymerElements/iron-elements#^1.0.0",
    "neon-elements": "PolymerElements/neon-elements#^1.0.0",
    "paper-elements": "PolymerElements/paper-elements#^1.0.5",
    "polymer": "Polymer/polymer#^1.0.0"
  },
  "name": "mwc-synthesis",
  "version": "0.0.1"
}
```


### Demo
Check out the [Synthesis Demo](https://github.com/meteorwebcomponents/synthesis-demo)

### Kickstart Your Meteor Polymer projects
[Kickstart a Meteor/Polymer project](https://github.com/aruntk/kickstart-meteor-polymer) with Synthesis.

![synthesis1](https://cloud.githubusercontent.com/assets/6007432/14216652/9da7131a-f867-11e5-9f84-6dd75d60dd45.gif)

### TODO
- [x] Work in cordova.Solve Polymer is not defined error.(wait for link imports to complete)
- [ ] Ability to use remote scripts inside. Scripts inside link imports are automatically added currently.
- [x] Add scripts inside html tags to app.js . (currenlty only scripts outside html tags is added(unless the tag is a body tag))
- [x] html link imports inside html files should be vulcanized. `<link rel="import"`
- [x] Css inside html inlined.
- [x] `<link rel="stylesheet" href="component.css"` support. gets converted to `<style>contents</style>`
- [x] Client side renderer for html files added.
- [x] import 'my-components.html'; support.


### Social

Gitter - [meteorwebcomponents](https://gitter.im/aruntk/meteorwebcomponents?utm_source=share-link&utm_medium=link&utm_campaign=share-link)

Meteor forum - https://forums.meteor.com/t/polymer-meteor-support-with-meteor-webcomponents-packages/20536


### Note

You can use [differential:vulcanize](https://atmospherejs.com/differential/vulcanize) to vulcanize polymer elements instead of adding them in the head directly.


