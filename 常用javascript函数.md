# 常用javascript函数


```javascript
//截取url参数
let getUrlParam = function(name) {
		var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
		var r = window.location.search.substr(1).match(reg);
		if(r != null) {
			return unescape(r[2]);
		} else {
			return null;
		}
	}
```


```javascript
    /** 
	 * param 将要转为URL参数字符串的对象 
	 * key URL参数字符串的前缀 
	 * encode true/false 是否进行URL编码,默认为true 
	 * return URL参数字符串 
	 */
	w.urlEncode = function(param, key, encode) {
		if(param == null) return '';
		var paramStr = '';
		var t = typeof(param);
		if(t == 'string' || t == 'number' || t == 'boolean') {
			paramStr += '&' + key + '=' + ((encode == null || encode) ? encodeURIComponent(param) : param);
		} else {
			for(var i in param) {
				var k = key == null ? i : key + (param instanceof Array ? '[' + i + ']' : '.' + i);
				paramStr += urlEncode(param[i], k, encode);
			}
		}
		return paramStr;
	};

```