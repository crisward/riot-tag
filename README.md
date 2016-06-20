# Riot-Tag

[Riot.js](http://riotjs.com/) tag syntax highlighting for [Visual Studio Code](https://code.visualstudio.com)

![screencast](https://github.com/crisward/riot-tag/raw/master/images/screen-cast.gif)

This is a conversion of my sublime-tag extension to do syntax highlighting 
for Riot js tag files. This extension supports HTML, Jade, Stylus and Coffeescript within
script tags.

With this plugin you can use

```
<yourtag>
  <script type="test/coffee">
    # your coffee script here
  </script>
  <script>
    // your javascript here
  </script>
</yourtag>
```
This will then have correct syntax highlighting.

### Jade Support

If you like white space sensitive languages, Jade can be
a very succinct way to write your tags. The compile process
converts all this to html before usage, so there are no
overheads to your packages tags. Riot-tag(Jade) supports
Jade syntax highlighting, along with embedded coffeescript,
stylus and normal JS.

Since 0.7  Riot(Jade) now highlights Css and Stylus correctly
within style tags.

```jade
yourtag
  p hello world

  script(type="coffee").
    # your coffee script here
    
  style.
    /* your css here */
    
  style(type="text/stylus")
    // your stylus here 

```

### Stylus Support

You can use stylus within your riot tags, the syntax highlighting requires you
to have the stylus syntax highlighting install too. To compile stylus you'll
also need stylus included in your compile process (see browserify tip below). 

### Installation

Inside visual studio code
```
cmd+shift+p
type: ext install riot-tag
```
The package contains 2 syntax highlighters riot(html) and riot(jade). If VSCode picks the wrong one, you can specify the correct one in your settings file.

##### HTML Settings
```json

{
     "files.associations": {
        "*.tag": "htmltag"
    }
}
```
##### Jade Settings
```
{
     "files.associations": {
        "*.tag": "jadetag"
    }
}
```


### Using with Browserify

If you like the idea of using Jade, Coffeescript, Stylus etc with your riot tags, adding the
below to your package.json file should get you most of the way. Just swap out the package names
if you'd prefer not to use any of the compile steps. Non of this is neccesary for riot, but it took
me a while to work this out when I started our with riot, once in place it can make a nice workflow.

```json
{
  "scripts":{
    "watch": "./node_modules/.bin/watchify src/app.coffee -v -o build/site.js",
    "build": "./node_modules/.bin/browserify src/app.coffee -d -p [minifyify --uglify [--mangle 0] --map build/app.map.json --output build/app.map.json] -o build/app.js"
  },
  "browserify": {
    "debug": true,
    "transform": [
      [
        "riotify",{
          "expr": false,
          "type": "coffee",
          "template": "jade"
        }
      ]
    ]
  },
  "devDependencies": {
    "riot": "^2.3.15",
    "riotify": "^0.1.2",
    "stylus": "^0.52.4",
    "browserify": "^11.2.0",
    "jade": "^1.11.0",
    "watchify": "^3.4.0",
    "minifyify": "^7.1.0"
  }
}
```
Then use `npm run watch` during development and `npm run build` prior to deployment for minified code.


### Giving Feedback

If you have any problems, feedback or just fancy staring this project
see https://github.com/crisward/riot-tag


### History

0.1.1  Can now use `script(type="coffee")` or `<script type="coffee">`
0.0.8  Fixed Stylus Bug
0.0.7  Added stylus support for Jade
0.0.6  Allows multiple script tags in jade
