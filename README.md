# Riot-Tag

[Riot.js](http://riotjs.com/) tag syntax highlighting for [Visual Studio Code](https://code.visualstudio.com)

This is a conversion of my sublime-tag extension to do syntax highlighting 
for Riot js tag files. This extension supports HTML, Jade and Coffeescript within
script tags.

With this plugin you can use

```
<yourtag>
  <script type="test/coffee">
    # your coffee script here
  </script>
</yourtag>
```
This will then have correct syntax highlighting.


### Jade Support

I've been messing a little with the jade support in riot, again having syntax
issues when combining with coffeescript. Jade can compile the coffeescript itself
but I had a few issues with this. To use the jade support follow the same
instructions below, but selet Riot(Jade) as the syntax.

```jade
yourtag
  p hello world

  script(type="text/coffee").
    # your coffee script here

```

### Installation

Inside visual studio code
```
cmd+shift+p
type: ext install riot-tag
```