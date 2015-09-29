JS模拟时钟
============

```html
<body onLoad="setInterval(setTimeSpan,1000);">
	<span style="font-size: 25px;" id="timeSpan"></span>
</body>
```

```js
<script type="text/javascript">
	function setTimeSpan() {
		var date = new Date();
		timeSpan.innerHTML = date.format('现在是：yyyy年MM月dd日   hh:mm:ss');
	}
	Date.prototype.format = function(format) {
		var o = {
			"M+" : this.getMonth() + 1, //month
			"d+" : this.getDate(), //day
			"h+" : this.getHours(), //hour
			"m+" : this.getMinutes(), //minute
			"s+" : this.getSeconds(), //second
			"q+" : Math.floor((this.getMonth() + 3) / 3), //quarter
			"S" : this.getMilliseconds() //millisecond
		}
		if (/(y+)/.test(format))
			format = format.replace(RegExp.$1, (this.getFullYear() + "")
					.substr(4 - RegExp.$1.length));
		for ( var k in o)
			if (new RegExp("(" + k + ")").test(format))
				format = format.replace(RegExp.$1, RegExp.$1.length == 1 ? o[k]
						: ("00" + o[k]).substr(("" + o[k]).length));
		return format;
	}
</script>
```

效果演示: <a href="http://blog.itmyhome.com/js_imitate_clock/" target="_blank">点击</a>