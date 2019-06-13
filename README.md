# DeleteAllWeibo
批量删除微博、批量设置微博仅自己可见，其实就是手动操作在浏览器自动化，找到删除按钮，模拟点击，然后滚动加载，重复之前步骤。

- 需要工具
  - Chrome 浏览器

## 批量设置微博仅自己可见
1. 打开Chrome浏览器，登陆微博；
2. 按F12打开开发者工具；
3. 复制如下代码到console中
```javascript
window.ff=$;window.addPage=function() {ori=document.location.href;if ("page=".search(ori)==-1) ori=ori+"&page=1";newloc = ori.replace(/(page=)([0-9]+)/g,function($0,$1,$2){var num=parseInt($2)+1;return $1+num;});window.location.href=newloc;};var inter=setInterval(function(){var orix = window.scrollTop;console.log(orix);scroll(0,orix+500);if(window.scrollTop==orix) {clearInterval(inter);window.addPage();};window.ff("[title='转换为仅自己可见']").click();window.ff("div > p.btn > a.W_btn_a > span").click();},1000);
```
4. 处理一个页面的微博后，再次复制上面代码到console中执行，直到所有页都处理完。

## 批量删除微博（！！!谨慎操作）
1. 打开Chrome浏览器，登陆微博；
2. 按F12打开开发者工具；
3. 复制如下代码到console中
```javascript
window.ff=$;window.addPage=function() {ori=document.location.href;if ("page=".search(ori)==-1) ori=ori+"&page=1";newloc = ori.replace(/(page=)([0-9]+)/g,function($0,$1,$2){var num=parseInt($2)+1;return $1+num;});window.location.href=newloc;};var inter=setInterval(function(){var orix = window.scrollTop;console.log(orix);scroll(0,orix+500);if(window.scrollTop==orix) {clearInterval(inter);window.addPage();};window.ff("[title='删除此条微博']").click();window.ff("div > p.btn > a.W_btn_a > span").click();},1000);
```
4. 处理一个页面的微博后，再次复制上面代码到console中执行，直到所有页都处理完。
