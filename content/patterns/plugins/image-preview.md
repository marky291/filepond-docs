+++
title = "Image preview"
+++

The Image Preview plugin renders a downscaled preview for dropped images.

Combined with the [Image EXIF orientation](../image-exif-orientation) plugin it automatically corrects any mobile rotation information to ensure the image is alway shown correctly.

{{% note %}}
Dropping really big images might impact performance. Browsers that support [`createImageBitmap`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/createImageBitmap) have an advantage as they can render the Bitmap data on a separate thread. Use the `imagePreviewMaxFileSize` setting to prevent previewing of very large images.
{{% /note %}}

## Installation

### Using npm

{{<cmd>}}npm i filepond-plugin-image-preview --save{{</cmd>}}

Now we can add the Image Preview plugin to our project like this.

```js
// Import FilePond
import * as FilePond from 'filepond';

// Import the plugin code
import FilePondPluginImagePreview from 'filepond-plugin-image-preview';

// Import the plugin styles
import 'filepond-plugin-image-preview/dist/filepond-plugin-image-preview.css';

// Register the plugin
FilePond.registerPlugin(FilePondPluginImagePreview);
```

{{% note %}}
If a module bundler ( like Webpack ) is not available, the plugin CSS file will have to be embedded manually.
{{% /note %}}


### Using a CDN

```html
<!-- add to document <head> -->
<link href="https://unpkg.com/filepond/dist/filepond.css" rel="stylesheet">
<link href="https://unpkg.com/filepond-plugin-image-preview/dist/filepond-plugin-image-preview.css" rel="stylesheet">

<!-- add before </body> -->
<script src="https://unpkg.com/filepond-plugin-image-preview/dist/filepond-plugin-image-preview.js"></script>
<script src="https://unpkg.com/filepond/dist/filepond.js"></script>

<script>
// Register the plugin
FilePond.registerPlugin(FilePondPluginImagePreview);

// ... FilePond initialisation code here
</script>
```

### Manual installation

```html
<!-- add to document <head> -->
<link href="filepond.css" rel="stylesheet">
<link href="filepond-plugin-image-preview.css" rel="stylesheet">

<!-- add before </body> -->
<script src="filepond-plugin-image-preview.js"></script>
<script src="filepond.js"></script>

<script>
// Register the plugin
FilePond.registerPlugin(FilePondPluginImagePreview);

// ... FilePond initialisation code here
</script>
```



## Properties

| Property                | Default | Description                                                                                                                                                                    |
| ----------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| allowImagePreview       | `true`  | Enable or disable preview mode                                                                                                                                                 |
| imagePreviewMinHeight   | `44`    | Minimum image preview height                                                                                                                                                   |
| imagePreviewMaxHeight   | `256`   | Maximum image preview height                                                                                                                                                   |
| imagePreviewHeight      | `null`  | Fixed image preview height, overrides min and max preview height                                                                                                               |
| imagePreviewMaxFileSize | `null`  | Can be used to prevent loading of large images when `createImageBitmap` is not supported. By default no maximum file size is defined, expects a string, like `2MB` or `500KB`. |
| imagePreviewTransparencyIndicator | `null` | Set to `'grid'` to render a transparency grid behind the image, set to a color value (for example `'#f00'`) to set transparent image background color. Please note that this is only for preview purposes, the background color or grid is not embedded in the output image. |
| imagePreviewMaxInstantPreviewFileSize | `1000000` | Maximum file size for images to preview immediately, for files that are larger and unsupported by the browser `createImageBitmap`. The preview is queued till FilePond is in rest state. |
