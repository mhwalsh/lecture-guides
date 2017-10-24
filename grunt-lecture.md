## Grunt Lecture Notes

## Why you need a build system?
**From the [Grunt Site](https://gruntjs.com/):** 

*In one word: automation. The less work you have to do when performing repetitive tasks like minification, compilation, unit testing, linting, etc, the easier your job becomes. After you've configured it through a Gruntfile, a task runner can do most of that mundane work for you—and your team—with basically zero effort.*

*The Grunt ecosystem is huge and it's growing every day. With literally hundreds of plugins to choose from, you can use Grunt to automate just about anything with a minimum of effort.*

### TL;DR

- Grunt to do repetitive tasks.
- Run utilities
- Run live reloads
- Speed, of loading your non minified files is expensive. 

#### How to Install
[http://gruntjs.com/getting-started]()

[http://gruntjs.com/project-scaffolding]()

#### Project specific
```
$: npm install grunt --save-dev
```
and any plugins:

```
$: npm install grunt-contrib-<name> --save-dev
```

## Lecture Plugins

1. `uglify` - minification 
	- should mangle false or need for []
2. `watch` - watch files for changes and run tasks on them
	- watch our client file and run uglify
3. show default and named tasks
4. `copy` - copy or vendor files
5. `jshint` - lints files for us. We can make this part of our build process.

### Other Plugins to look into:
`concat` and `cssmin`

## References:

- [http://gruntjs.com/](http://gruntjs.com/)
- [http://gruntjs.com/plugins](http://gruntjs.com/plugins)
- [https://www.youtube.com/watch?v=XJ5F-Auhato&list=PLoYCgNOIyGAB0_YBfdNP5oqAD98HtAQqL&index=7](https://www.youtube.com/watch?v=XJ5F-Auhato&list=PLoYCgNOIyGAB0_YBfdNP5oqAD98HtAQqL&index=7)
- [https://www.youtube.com/watch?v=TMKj0BxzVgw&list=PLoYCgNOIyGAB0_YBfdNP5oqAD98HtAQqL&index=8](https://www.youtube.com/watch?v=TMKj0BxzVgw&list=PLoYCgNOIyGAB0_YBfdNP5oqAD98HtAQqL&index=8)

#### Joel's tool
This will copy a template to start out with into every project you run it in. So you don't have to start from scratch with your grunt file.

[https://github.com/joeltmiller/grunt-init-gruntfile](https://github.com/joeltmiller/grunt-init-gruntfile)
