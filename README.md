# search-select
表单Select，可搜索选中，支持Ajax搜索或初始化数据源，不依赖JQuery  
例子见 [查看示例](http://git.tuine.me/search-select)
### 功能
* 数据源搜索
* Ajax搜索
* 自定义展示名称
* 设置区分大小写
* 自定义搜索字段
* 自定义选中值
* 自定义回调函数
---

## 例1数据源
```
	var config1 = {
		targetEle:document.getElementById("search-select1"),//dom
		field:"name",//默认下拉展示数据
		dataValue:"id",//li data-value值
		filterColumn: ['key','name'],//搜索字段
		sensitive: true,//是否区分大小写
		sourceData:[{name:"search",key:'I',id:123},{name:"select",key:'He',id:456},{name:"search-select",key:'You',id:789}],//数据源
	}
	var searchSelect1 = new SearchSelect(config1);
	searchSelect1.selectCallBack = function (data) {
		alert(JSON.stringify(data));
	}
```

## 例2AJAX
```
var config = {
		targetEle:document.getElementById("search-select"),
		field:"name",//默认展示字段、搜索字段
		dataValue:"id",//下拉选项data-value值,默认data-array-num=顺序
		//eg:<li data-array-num="0" data-value="123">search</li>
		getData:getData,//AJAX搜索函数
		isAjax: true//默认false 非AJAX
	}
	var searchSelect = new SearchSelect(config);//初始化对象
	searchSelect.selectCallBack = function (data) {//选中回调函数
		alert(JSON.stringify(data));
	}
	function getData(keyword) {
		//jquery方法
		var url = '',data={keyword:keyword};
		$.post(url, data, function(data){
			searchSelecti.pushData(data);//添加数据结果
		}, 'json');
	}
```
---
# Other
简简单单临时项目需求,没太优化
