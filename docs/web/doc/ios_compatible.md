# iOS兼容
在移动端H5开发过程中，平台级差异导致的问题屡见不鲜，为了避免后续出现同样的问题，在此记录以便查阅。
## 1.new Date()兼容问题
一般情况下，创建一个日期变量是这样的：
```
let d = new Date("2020-11-29 12:00:00");
```
在iOS平台上webview的表现差强人意，竟然报错`Invalid date`。经过一番查阅，在iOS平台上不支持`-`连接日期，因此代码需要修改成这样：
```
let d = new Date("2020/11/29 12:00:00");
或者
let d = new Date("2020-11-29 12:00:00".replace(/-/g, "/"));
```