# Zeppelin Web Application
This is a Zeppelin web frontend project.

## About this fork

This fork enables the integration of custom elements (aka Polymer elements).

The general procedure is:

- include the necessary components in `bower.json` (see the example below)
- include the required import statements in `app\elements.html`
- run `grunt build`
- refresh the notebook

Using the components is actually pretty straight-forward:

```html
%angular
<div id="mydiv" style="height:400px; width:100">
    <google-map></google-map>
</div>
```

Or, for the _polimero_ components:

```html
%angular

<div id="mydiv" style="height:400; width:600">
<template is="auto-binding">
    <polimero-data url="bower_components/polimero/data/data.csv" data="{{data}}"></polimero-data>
    <polimero-parcoords
        dimensions='["sepalLength","sepalWidth","petalLength","petalWidth"]'
        options='{"width": 600, "height": 300}'
        data="{{data}}"
        selected="{{selected}}"></polimero-parcoords>
</template>
</div>
```

In other words, the only difference is the additional `<div>` tag, the rest is just taken from the examples provided with the components. That's it!

The examples that are provided are made possible using the following configuration:

`bower.json`:

```json
{
  "name": "zeppelin-web",
  "version": "0.0.0",
  "dependencies": {
    "angular": "1.3.8",
    . . .
    "google-map": "~0.4.2",
    "polimero": "file:///Users/toni/Hadoop/polimero/.git"
  },
```

`elements.html`:

```html
<link rel="import" href="bower_components/polimero/polimero.html">
<link rel="import" href="bower_components/google-map/google-map.html">
```



## Compile Zeppelin web
If you want to compile the WebApplication, you will have to simply run `mvn package`.
This will Download all the dependencies including node js and npm (you will find the binaries in the folder `zeppelin-web/node`).

We also provide some **helper script** for bower and grunt (you dont need to install them).

In case of the error `ECMDERR Failed to execute "git ls-remote --tags --heads git://xxxxx", exit code of #128`

change your git config with `git config --global url."https://".insteadOf git://`

**OR**

Try to add to the `.bowerrc` file the following content:
```
  "proxy" : "http://<host>:<port>",
  "https-proxy" : "http://<host>:<port>"
```


and retry to build again.

## Contribute on Zeppelin Web
If you wish to help us to contribute on Zeppelin Web, you will need to install some deps.
Here this is a good start to understand how zeppelin web is architectured.
http://www.sitepoint.com/kickstart-your-angularjs-development-with-yeoman-grunt-and-bower/

### Run the application in dev mode
``./grunt serve``

### Build the application
`./grunt build`

### Add composents to Zeppelin Webapp
 * New controller : `yo angular:controller <controlerName>`
 * New directive : `yo angular:directive <directiveName>`
 * New service : `yo angular:service <serviceName>`

 ### Add plugin
 
 `./bower install <plugin> -save`
 update the file index.html with the new bower_components 
 
 ex: `./bower install angular-nvd3` 
 ```
 <script src="bower_components/angular-nvd3/dist/angular-nvd3.js"></script>
 ````




