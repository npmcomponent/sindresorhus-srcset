*This repository is a mirror of the [component](http://component.io) module [sindresorhus/srcset](http://github.com/sindresorhus/srcset). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/sindresorhus-srcset`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# srcset [![Build Status](https://travis-ci.org/sindresorhus/srcset.svg?branch=master)](https://travis-ci.org/sindresorhus/srcset)

> Parse and stringify the HTML `<img>` [srcset](http://mobile.smashingmagazine.com/2013/08/21/webkit-implements-srcset-and-why-its-a-good-thing/) attribute.

Useful if you're creating a polyfill, build-tool, etc.


## Install

Download the library [manually](https://github.com/sindresorhus/srcset/releases) or with a package-manager.

```bash
$ npm install --save srcset
```

```bash
$ bower install --save srcset
```

```bash
$ component install sindresorhus/srcset
```


## Usage

How an image with `srcset` might look like:

```html
<img alt="The Breakfast Combo"
     src="banner.jpg"
     srcset="banner-HD.jpg 2x, banner-phone.jpg 100w, banner-phone-HD.jpg 100w 2x">
```

Then have some fun with it:

```js
var parsed = srcset.parse('banner-HD.jpg 2x, banner-phone.jpg 100w');
console.log(parsed);
/*
[
	{ url: 'banner-HD.jpg', density: 2 },
	{ url: 'banner-phone.jpg', width: 100 }
]
*/

parsed.push({ url: 'banner-phone-HD.jpg', width: 100, density: 2 });

var stringified = srcset.stringify(parsed);
console.log(stringified);
/*
banner-HD.jpg 2x, banner-phone.jpg 100w, banner-phone-HD.jpg 100w 2x
*/
```


## API

### srcset.parse()

Accepts a srcset string and returns an array of objects with the possible properties: `url` (always), `width`, `height`, `density`.

### srcset.stringify()

Accepts an array of objects with the possible properties: `url` (required), `width`, `height`, `density` and returns a srcset string.


## License

[MIT](http://opensource.org/licenses/MIT) © [Sindre Sorhus](http://sindresorhus.com)
