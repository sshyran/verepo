# veRepo - SASS Library

## Table of Content

* [About](#about)
* [Documentation](#documentation)
	* [Live](#live)
* [Guides](#guides)
	* [How to use veRepo](#how-to-use-verepo)
	* [Usage Examples](#usage-examples)
	* [Bower](#bower)
	* [Grunt.js](#gruntjs)
	* [SCSS to SASS](#scss-to-sass)
* [Contribution Guidelines](#contribution-guidelines)
* [License](#license)
* [Credits](#credits)

## About

veRepo is a SASS library of modules and mixins for robust and maintainable front-end development using SASS. Most of the modular items/objects in this repo will work by just adding 1 class name to the html element you desire to style (although there are some exceptions).

## Documentation

### Live

Visit [this link](http://varemenos.github.io/verepo/docs/) to read the online version, or follow the next steps to get a local version:

1. To generate the docs you have to use the grunt command that generates the docs mentioned [here](https://github.com/varemenos/verepo#gruntjs).

2. To view the docs you need to serve them in an http server. One of the fastest ways to do that is via python's httpserver: `cd docs` and then `python -m http.server`

## Guides

### How to use veRepo

(It is highly recommended to use veRepo via [bower](https://github.com/varemenos/verepo#bower))

Assuming that your current file structure looks like this:

	assets
	└──css
		├── _style.scss
		└── _verepo.scss

Where `style.scss` is the main stylesheet of your project and `verepo` is the distributable verepo library file found in the root directory of this repository. Now all you have to do is to import the `_verepo.scss` file inside of `style.scss` and then use it's components by using `@include`.

### Usage Examples

__example #1:__

```scss
@import "_verepo";
@include normalize;
```

This will include the latest normalize.css version

__example #2:__

```scss
@import "_verepo";

.blue-flat-button{
	@include button(#fff, #09f, 0);
}
```

The above will be processed into the following:

```css
.blue-flat-button {
	position: relative;
	display: inline-block;
	padding: 0.5em 1em;
	color: white;
	text-decoration: none;
	background-color: #0099ff;
	border: 1px solid #007acc;
	border-radius: 0;
	background-clip: padding-box;
	transition: 150ms ease-in-out background-color, 150ms ease-in-out box-shadow;
}

.blue-flat-button:hover,
.blue-flat-button:focus {
	cursor: pointer;
	background-color: #4db8ff;
}

.blue-flat-button:active {
	cursor: pointer;
	box-shadow: 0 0 3px #0099ff, 0 0 0.5em rgba(0, 0, 0, 0.25) inset;
}
```

### Bower

veRepo is now in the bower package directory and you can install it by simply running this command:

	bower install verepo

### Grunt.js

While being in the root directory of the repository you need to run `npm install` which will allow you to use gruntjs by installing all the dependencies of the current project. After that, you can perform one of these tasks:

1. `grunt update-docs` to compile the docs
2. `grunt update-dist` to compile the distributable `_verepo.scss` file
3. `grunt update-example` to compile the sass file for the example page
4. `grunt update` or `grunt` to run the 3 tasks above.
6. `grunt connect` to initiate a simple http server at http://localhost:8000 which will server a local viewer for the example website and docs

to stop the tasks, you need to press `CTRL` + `C`

### SCSS to SASS

For the SASS syntax lovers or the SCSS syntax haters, you can use `sass-convert` to convert the scss files to sass. Later on I might write a script to automate it but currently it doesn't seem wise to develop a tool which will most probably be rewriten again due to this repository's current state (alpha phase).

## Contribution Guidelines

1. Read [CONTRIBUTE.md](CONTRIBUTE.md)
2. When creating a new verepo "object", you need to:
	1. include the `.scss` file inside the verepo library's directory
	2. name it after it's mixin but since it's a partial, prepend a `_` in the name (for example `_grid.scss`)
3. Inside the file you just created:
	1. Include the documentation declaration (for syntax and information, [read here](http://sassdoc.com/annotations/))
	2. Include any import declarations
	3. Include any `TODO:` declarations
	4. Include the code (mixins, functions etc)
	5. If the mixin you've created takes no parameters, then create an `@extend` declaration with the same name which will include the mixin you've just created (for example: `%clearfix{ @include @clearfix; }`)
	6. If you create more than 1 mixin in the file, then repeat the previous steps for each mixin
4. Finally you need to do the following to submit your changes:
	1. Re-generate the verepo documentation locally (there is a guide for this which is mentioned above)
	2. Run `grunt update` to update the documentation, example page and distributable `_verepo.scss` file
	3. Push the changes
	4. Update ghpages by running this command while in the root of the verepo repository directory: `git checkout gh-pages && git merge master && git push && git checkout master`
	5. Finally bump the project version by doing the following:
		1. Read [semver's spec](http://semver.org/) and deside whether the changes you've made are considered `patch`, `minor` or `major`
		2. Then use grunt bump to update the project verion with the following command: `grunt bump:patch` or `grunt bump:minor` or `grunt bump:major`
	6. Do a Pull-Request

## About prefix mixins

From v0.0.3 and onwards prefixes will be removed. Please Autoprefixer instead!

## License

	The MIT License (MIT)

	Copyright (c) 2013 Adonis K.

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

## Credits

* The `CONTRIBUTE.md` file of this project is a slightly modified copy `CONTRIBUTE.md` file from the normalize.css project.
* Some of the partials in this repo were inspired by [scut](https://github.com/davidtheclark/scut)
* Stubbornella for the [media object](www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code/)
* TODO add more
