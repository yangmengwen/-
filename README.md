# 前端知识点总结
## 内存泄露：
> 指的是内存不能被浏览器正常回收的现象
## 事件委托
> 事件委托就是利用事件冒泡为元素指定一个事件处理函数(把事件加到父元素或祖先元素上),事件冒泡就是事件从最内层开始一层层往上执行
```html
<ul id="ull">
  <li value="1"></li>
  <li value="2"></li>
  <li value="3"></li>
  <li value="4"></li>
</ul>
window.onload = function (){
  var ull = document.getElementById('ull');
  ull.addEventLister('click',function(e){
    console.log(li.value);
  }) 
}
```
>IE8以下支持attchEvent（'on'+type,fn），IE8以上支持addEventListener(type,fn) 
## Ajax
> ajax即异步的javaScript和Xml，是一种异步刷新技术
### XMLHttpRequest
> XMLHttpRequest是ajax的基础，用于后台与服务器之间交换数据
## Ajax请求过程
> 创建XMLHttpRequest对象
```html
  var xmlhttp;
  if (window.XMLHttpRequest){
    var xmlhttp = new XMLHttpRequest();
  }
  else {
    var xmlhttp = new ActiveObjext("Microsoft.XMLHTTP"); // IE5/6使用ActiveObject对象
  }
  
```
> 向浏览器发送请求,利用XMLHttpRequest的open()和send()方法
```html
  xmlhttp.open(method,url,async); //method:请求类型，url:请求路径，aysnc:是否支持异步
  xmlhttp.send(); //将请求发到服务器，仅仅用于post请求
```
> 当async=true时，需要规定在响应状态onreadystatechange事件时执行的函数,否则不需要编写onreadystatechange函数
```html
  xmlhttp.onreadystatechange = function (){
    if(xmlhttp.readystate == 4 && xmlhttp.readystate == 200){
      document.getElementById('myDiv').innerHTML = xmlhtttp.responseText;
    }
  }
  xmlhttp.open('GET','a.php',true);
  xmlhttp.send();
## 浏览器渲染
