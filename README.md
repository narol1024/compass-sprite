##compass制作雪碧图示例代码


* * *
####compass缩放雪碧图，自动生成background-size和background-position
```sass
$icons-sprite-dimensions: true;
@import "compass/css3";
@import "compass/utilities/sprites";
@import "icons/*.png";
@mixin resize-sprite($map, $sprite, $percent) {
  $spritePath:    sprite-path($map);
  $spriteWidth:   image-width($spritePath);
  $spriteHeight:  image-height($spritePath);
  $width: image-width(sprite-file($map, $sprite));
  $height: image-height(sprite-file($map, $sprite));
 
  @include background-size(ceil($spriteWidth * ($percent/100)) ceil($spriteHeight * ($percent/100)));
  width: ceil($width*($percent/100));
  height: ceil($height*($percent/100));
  background-position: 0 floor(nth(sprite-position($map, $sprite), 2)  * ($percent/100) );
}

.icon-car {
    $spriteName: car;
    $percent:50;
    @include resize-sprite($icons-sprites, $spriteName,$percent);
}
.icon-share{
    $spriteName: share;
    $percent:50;
    @include resize-sprite($icons-sprites, $spriteName,$percent);
}
```