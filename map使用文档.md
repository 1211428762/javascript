## 百度地图使用文档(Version2.0.56)

#### 引入百度地图包

其中common.js需要自己手动配置

```js
	<script src="http://api.map.baidu.com/api?v=1.0&type=webgl&ak=1XjLLEhZhQNUzd93EjU5nOGQ"></script>
	<script src="https://mapv.baidu.com/build/mapv.min.js"></script>
	<script src="./js/common.js"></script>
	<script src="https://code.bdstatic.com/npm/mapvgl@1.0.0-beta.62/dist/mapvgl.min.js"></script>
```

#### DOM结构

需要一个DOM容器

```html
<style>
    	#map_container {
				width: 100%;
				height: 100%;
				margin: 0;
			}
</style>
<div id="map_container"></div>
```

具体代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
	<head>
		<meta charset="utf-8">
		<title>MapVGL</title>
		<meta http-equiv="X-UA-Compatible" content="IE=Edge">
		<meta name="viewport" content="initial-scale=1.0, user-scalable=no">
		<style>
			html,
			body {
				width: 100%;
				height: 100%;
				margin: 0;
				padding: 0;
			}
			#map_container {
				width: 100%;
				height: 100%;
				margin: 0;
			}
		</style>
        //引入百度地图包
		<script src="http://api.map.baidu.com/api?v=1.0&type=webgl&ak=1XjLLEhZhQNUzd93EjU5nOGQ"></script>
		<script src="https://mapv.baidu.com/build/mapv.min.js"></script>
		<script src="./js/common.js"></script>
		<script src="https://code.bdstatic.com/npm/mapvgl@1.0.0-beta.62/dist/mapvgl.min.js"></script>
	</head>
	<body>
		<div id="map_container"></div>
		<script>
			/* global BMapGL */

			/* global Stats */

			/* global mapv */

			/* global mapvgl */

			/* global initMap */

			/* global purpleStyle */
			var map = initMap({
				tilt: 60,
				heading: 0,
				center: [116.201607, 39.90807],  //实际呈现的经纬度
				zoom: 14,
				style: purpleStyle //地图样式
			});
//初始化地图
			var view = new mapvgl.View({
				map: map
			});
//挂载地图实例
			view.startAnimation();

			var lineLayer = new mapvgl.LineLayer({
				width: 10,
				// isFlat: false,
				color: 'rgba(55, 71, 226, 0.9)',
				style: 'road'
			});
//地图线路格式
			var layer = new mapvgl.IconLayer({
				width: 100 / 4,
				height: 153 / 4,
				// offset: [0, 0],
				icon: 'img/location.png',
				enablePicked: true, // 是否可以拾取
				selectedIndex: -1, // 选中项
				selectedColor: 'deepskyblue', // 选中项颜色
				autoSelect: true, // 根据鼠标位置来自动设置选中项
				onClick: (e) => { // 点击事件
					console.log('click', e);
				},
				onDblClick: e => {
					console.log('double click', e);
				},
				onRightClick: e => {
					console.log('right click', e);
				}
			});

			var data = [];

			var citys = [
				'北京', '天津', '上海', '重庆', '石家庄', '太原', '呼和浩特', '哈尔滨',
				// '长春', '沈阳', '济南', '南京', '合肥', '杭州', '南昌', '福州', '郑州',
				// '武汉', '长沙', '广州', '南宁', '西安', '银川', '兰州', '西宁', '乌鲁木齐',
				// '成都', '贵阳', '昆明', '拉萨', '海口'
			];
            //标记落点
			var markers = [
				'img/location.png',
				// 'img/icons/icon-accident.png',
				// 'img/icons/icon-airplane.png',
				// 'img/icons/icon-location.png',
				// 'img/icons/label-accident.png',
				// 'img/icons/label-jam.png',
				// 'img/icons/label-warning.png',
			];
//图标族
			var randomCount = 100;

			// 构造数据
			while (randomCount--) {
				var cityCenter = mapv.utilCityCenter.getCenterByCityName(citys[parseInt(Math.random() * citys.length, 10)]);
				data.push({
					geometry: {
						type: 'Point',
						coordinates: [cityCenter.lng - 2 + Math.random() * 4, cityCenter.lat - 2 + Math.random() * 4]
					},
				
				});
			}
            
            
			fetch('./js/car.csv').then(function(rs) {
				return rs.text();
			}).then(function(csvstr) {
				var dataSet = mapv.csv.getDataSet(csvstr);
				var data = dataSet.get();
				data = data.slice(5, 6);
				view.addLayer(lineLayer);
				lineLayer.setData(data);
                //获取本地坐标数据,选择地区渲染路线
			});
            

			view.addLayer(layer);
			layer.setData(data);
			map.setDefaultCursor('default');
            //将图标渲染进地图层
		</script>
	</body>
</html>
```

#### vue使用百度地图

安装

`npm i mapv`

在index页引入如下包

```html
<script src="http://api.map.baidu.com/api?v=1.0&type=webgl&ak=rQxHPQX1ua21rWnXzTbUh5KSSUbnefxR"></script>
    <script src="https://code.bdstatic.com/npm/mapvgl@1.0.0-beta.51/dist/mapvgl.min.js"></script>
    <script src="https://mapv.baidu.com/gl/examples/static/common.js"></script>
    <script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=rQxHPQX1ua21rWnXzTbUh5KSSUbnefxR"></script>
    <script src="http://mapv.baidu.com/build/mapv.min.js"></script>
```

