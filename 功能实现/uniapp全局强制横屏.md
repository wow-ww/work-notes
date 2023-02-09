landscape-primary 横屏正方向，屏幕正方向按顺时针旋转90°； landscape-secondary 横屏方向，屏幕正方向按顺时针旋转270；
landscape横屏正方向或反方向，根据设备重力感应器自动调整。

``` js
// app.vue
onLaunch: function() {
	plus.screen.lockOrientation('landscape');
}
```
###### 参考链接
1.[HTML5+ API Reference (html5plus.org)](https://www.html5plus.org/doc/zh_cn/device.html#plus.screen.lockOrientation)
2.[请问uni-App 如何控制横屏？ - DCloud问答](https://ask.dcloud.net.cn/question/58696)