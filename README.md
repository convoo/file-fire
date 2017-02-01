# file-fire

<p align="center">
  <img alt="file-fire" src="FileFire400.png" width="300">
</p>

<p align="center">
Simple way to upload and download files from Firebase Storage.
</p>

<p align="center">
  <a href="https://webcomponents.org/element/convoo/file-fire"><img src="https://img.shields.io/badge/webcomponents.org-published-blue.svg"></a>
  <a href="https://gitter.im/convoo/general"><img src="https://img.shields.io/badge/gitter-join%20chat-brightgreen.svg"></a>
</p>

---

## Install

```
bower install file-fire --save
```

# \<file-fire\>

An element that uploads files and provides download url from Firebase Storage. For images, it can resize and provide a placeholder as well.

After resizing, it can also generate 2x 3x image sizes. This is determined by the `max-scale` and `scale-step` properties. Some examples:

1. `max-scale` of 3 and `scale-step` of 1 will generate 1x, 2x and 3x images.
1. `max-scale` of 2 and `scale-step` of 0.5 will generate 1x, 1.5x and 2x images.

It can also fetch images from elsewhere (such as a twitter profile image) and upload that to your Firebase Storage.

<!--
```
<custom-element-demo>
  <template>
    <link rel="import" href="file-fire.html">
    <link rel="import" href="../polymerfire/firebase-app.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<firebase-app
  name="demo"
  api-key="AIzaSyACU-9dEBSmlEq8iwfuDCPCWU81UNDytuQ"
  auth-domain="convoofire.firebaseapp.com"
  database-url="https://convoofire.firebaseio.com"
  storage-bucket="convoofire.appspot.com"
  >
</firebase-app>
<file-fire
  app-name="demo"
  path="/remote/file"
  src-url="https://pbs.twimg.com/profile_images/741290730170122240/abfazODg_400x400.jpg"
  progress="{{remoteProgress}}"
  download-url="{{downloadRemoteUrl}}"
  max-scale="3"
  resize-height="50"
  resize-width="50"
  placeholder="{{remotePlaceholder}}"
></file-fire>
```


# \<file-fire-drop\>

An enhanced version of \<file-fire\> that allows dragging and dropping a file. This element can have contents that are displayed unless a file is dragged over it.
<!--
```
<custom-element-demo>
  <template>
    <link rel="import" href="file-fire-drop.html">
    <link rel="import" href="../polymerfire/firebase-app.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<file-fire-drop
  app-name="demo"
  path="/u/test.png"
  over-write
  progress="{{progress}}"
  placeholder="{{base64}}"
  files="{{images}}"
>
This text will be visible unless you hover over it while dragging a file</br>
This text will be visible unless you hover over it while dragging a file</br>
This text will be visible unless you hover over it while dragging a file</br>
</file-fire-drop>
```

# \<file-fire-fetch\>

An element that retrieves the download url from the file storage path in Firebase Storage.
<!--
```
<custom-element-demo>
  <template>
    <link rel="import" href="file-fire-fetch.html">
    <link rel="import" href="../polymerfire/firebase-app.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<firebase-app
  name="demo"
  api-key="AIzaSyACU-9dEBSmlEq8iwfuDCPCWU81UNDytuQ"
  auth-domain="convoofire.firebaseapp.com"
  database-url="https://convoofire.firebaseio.com"
  storage-bucket="convoofire.appspot.com"
  >
</firebase-app>
<file-fire-fetch
  app-name="demo"
  path="/my/path/to/file.jpg"
  file="{{myFile}}"
  file-url="{{myFileURL}}"
></file-fire-fetch>
```

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install


## Playing With Your Element

If you wish to work on your element in isolation, we recommend that you use
[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's
bower dependencies in line. You can install it via:

    npm install -g polyserve

And you can run it via:

    polyserve

Once running, you can preview your element at
`http://localhost:8080/components/image-fire/`, where `image-fire` is the name of the directory containing it.


## Testing Your Element

Simply navigate to the `/test` directory of your element to run its tests. If
you are using Polyserve: `http://localhost:8080/components/image-fire/test/`

### web-component-tester

The tests are compatible with [web-component-tester](https://github.com/Polymer/web-component-tester).
Install it via:

    npm install -g web-component-tester

Then, you can run your tests on _all_ of your local browsers via:

    wct

#### WCT Tips

`wct -l chrome` will only run tests in chrome.

`wct -p` will keep the browsers alive after test runs (refresh to re-run).

`wct test/some-file.html` will test only the files you specify.


## Yeoman support

If you'd like to use Yeoman to scaffold your element that's possible. The official [`generator-polymer`](https://github.com/yeoman/generator-polymer) generator has a [`seed`](https://github.com/yeoman/generator-polymer#seed) subgenerator.