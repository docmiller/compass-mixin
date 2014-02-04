#A collection of handy compass mixins

## SVG background image with modernizr .no-svg fallback

based on http://forrst.com/posts/Sass_Compass_Mixin_for_SVG_Background_Image_Fall-dWn
```
//
// SVG with Fallback images
//
// modernizr class
@mixin no-svg {
  .no-svg & { @content }
}
// mixin that requires filename and background position, with optional use of CSS inline-images
@mixin svg-bg($filename, $left, $top, $inline: false,  $extension: '.png') {
  @if $inline == true {
    background: inline-image($filename + '.svg') $left $top no-repeat;
  }
  @else {
    background: image-url($filename + '.svg') $left $top no-repeat;
  }
  @include no-svg {
    @if $inline == true {
      background: inline-image($filename + $extension) $left $top no-repeat;
    }
    @else {
      background: image-url($filename + $extension) $left $top no-repeat;
    }
  }
}
```
### Usage

@include svg-bg(imagename, left, top);

#### with inline images
  
@include svg-bg(imagename, left, top, $inline: true);
