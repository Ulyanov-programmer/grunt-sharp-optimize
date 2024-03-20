# grunt-sharp-optimize

> Compression and conversion of images for grunt using [sharp](https://www.npmjs.com/package/sharp).

## What is this

### With this thing you can: <br>

- Optimize your images.
- Convert your images to other formats (including, but not limited to `.webp` and `.avif`).

### Features

- Using the [sharp](https://www.npmjs.com/package/sharp) plugin.
- A beautiful log system.
- Flexible API.
- Supported formats: `.png .jpg/jpeg .webp .avif .tiff .heif .gif`

## How to use this

### Installation

If you haven't used [Grunt](https://gruntjs.com/) before, be sure to check out the [Getting Started](https://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](https://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm i grunt-sharp-optimize
```

_OR_

```shell
yarn add grunt-sharp-optimize
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-sharp-optimize');
```

Or use [the load-grunt-tasks plugin](https://www.npmjs.com/package/load-grunt-tasks).

---

### Example of usage

```js
grunt.initConfig({
  sharp: {
    files: {
      src: 'your_src_images/**/*.{gif,webp,avif,png,jpg,jpeg,svg}',
      dest: 'your_dest_images/',
    },
    options: {
      logLevel: 'small',

      webp: {
        quality: 80,
        lossless: false,
        alsoProcessOriginal: true,
      },

      avif: {
        quality: 100,
        lossless: true,
        effort: 4,
      },

      gif_to_webp: {
        quality: 90,
      },

      png_to_avif: {},

      jpg_to_jpg: {
        quality: 80,
        mozjpeg: true,
      },
    },
  },
});
```

## ⚠ Pay attention

Using this plugin together with the [grunt-newer plugin](https://www.npmjs.com/package/grunt-newer) and the like may not allow it to work correctly. This plugin **has a built-in system that replaces the functionality of similar plugins**.

## API

```js
sharp: {
  ...,
  options: {
    sharpOptions: {},
    logLevel: 'codename',

    extname: {
      param: value,
    },
    extname_to_extname: {
      param: value,
    },
  },
}
```

### extname

Type: `object`<br>
An object that allows you to convert `all` images into images of a `specific type`.
<br>

```js
// example, all images will be converted to .avif
avif: {
  param: value,
},
```

#### param

Type: `any` (depends on the parameter)<br>
Option for an output image. <br>
To familiarize yourself with the available options, refer to the plugin documentation (for example, this [section for `.jpeg`](https://sharp.pixelplumbing.com/api-output#jpeg)):

#### alsoProcessOriginal

Type: `boolean`<br>
Default value: `false`<br>
It also allows you to optimize and move the original files. It only works for the type `extname: {}` parameter. <br>

```js
avif: {
  // If true, the originals will also be optimized and transferred.
  alsoProcessOriginal: true,
},
```

### extname_to_extname

Type: `object`<br>
An object that allows you to convert images of a `specific type` into images of a `specific type`. <br>
_Does not transmit originals._ <br>

```js
// example, all images in the format .jpg will be converted to .avif
jpg_to_avif: {
  param: value,
},
// you can also optimize images without changing the extension
jpg_to_jpg: {
  param: value,
},
```

### logLevel

Type: `string`<br>
Default value: `small`<br>
Can get the value: `small | full | ''`<br>
Allows you to change the logging.

```js
// usage example
options: {
  logLevel: 'full',
  ...,
}
```

```bash
// Log if the value of logLevel is equal to 'small' (default value):
yourImage.jpg => webp

// Log if the value of logLevel is equal to 'full':
The file the_absolute_path_to_your/image.jpg was processed to image.webp

// Log if the value of logLevel is equal to '' (or other value):

(the log is disabled)
```

### sharpOptions

Type: `object`<br>
If you need to pass certain [parameters](https://sharp.pixelplumbing.com/api-constructor#new) directly to the sharp plugin, use this parameter.

```js
// usage example
options: {
  sharpOptions: {
    animated: true,
    limitInputPixels: false,
  },
  ...,
}
```

### Supported format names:

- `png`
- `jpg` | `jpeg`
- `webp`
- `avif`
- `tiff`
- `heif`
- `gif`

### If you find a bug, please create an issue [here](https://github.com/Ulyanov-programmer/grunt-sharp-optimize/issues).

### If this project was useful to you, you can give it a ★ in [repository](https://github.com/Ulyanov-programmer/grunt-sharp-optimize).
