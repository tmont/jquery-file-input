# File inputs restyled
Fancy styled file upload inputs. In a tiny jQuery plugin.

Also supports image uploads with easy previews with very little extra work.
But if you don't want that, you can rip out about half of the code to make
it even smaller.

## Demo

## Installation
Reference [`jquery.file-input.js`](./jquery.file-input.js) somewhere on your page.

## Usage
Assuming you have some HTML like this:
```html
<div id="file-input">Upload a file!</div>
```

You can simply do this:
```javascript
$('#file-input').fileInput();
```

For image previews, you can do something like this (also see [demo.html](./demo.html) for
examples):

```javascript
//All options are optional. heh.
var options = {
	resize: 10 * 1024, //resize images using a canvas element until they're under 10KB
	quality: 0.6, //JPEG compression, defaults to 0.8
	decode: true //use window.atob to base64 decode before checking size
};

$('#file-input').imagePreviewInput(options).on('change', function(e, base64Data) {
	$('<img/>').attr('src', base64Data).appendTo('body');
});
```

To get a hold of the file, do this:

```javascript
$('#file-input').fileInput().on('change', function(e, files) {
	files.forEach(console.log);
});
```

The `decode` option also accepts a base64 decode function, if you want to supply your own
because your [browser sucks](http://stackoverflow.com/a/247261).

## License
MIT. Whatever.

## Development
```
git clone git@github.com:tmont/jquery-file-input.git
cd jquery-file-input
npm install
npm start
```

And then open http://localhost:9876/demo.html in a browser.
