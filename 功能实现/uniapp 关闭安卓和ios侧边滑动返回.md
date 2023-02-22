- 安卓
	利用页面生命周期`onBackPress`
``` js
	// 监听侧边返回
	onBackPress(e) {
		// console.log(e)
		return true;
	}
```
- ios
	在page.json中对需要关闭边滑动返回的页面进行设置`popGesture`属性
``` json
	{
		"path": "pages/game/gameTest",
		"style": {
			"app-plus": {
				"titleNView": false,
				"popGesture": "none"
			}
		}
	}
```