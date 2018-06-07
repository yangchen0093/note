# JQuery 
### 【2018-04-xx】
## @#￥1.清除form的数据(blog.csdn.net/u012246342/article/details/47167659)
`$("#signinContainer")[0].reset(); `

<br>


## @#￥2.鼠标悬停在a上时打开b，鼠标离开a且不在b上时则关闭b（https://jsfiddle.net/hsfzxjy/rs776m3r/7/ ）
`html`:
```
<div ondrop='drop(event,this)' ondragover='allowDrop(event)' draggable='true' ondragstart='drag(event, this)'></div>
```
`js`:
```
function allowDrop(ev) {
    ev.preventDefault();    //prevent default behavior
}

var srcdiv = null;

function drag(ev, divdom) {   //store dom and data
    srcdiv = divdom;
    ev.dataTransfer.setData("text/html", divdom.innerHTML);
}

function drop(ev, divdom) {   //exchange data
    ev.preventDefault();    //prevent default behavior
    if (srcdiv != divdom) {
        srcdiv.innerHTML = divdom.innerHTML;
        divdom.innerHTML = ev.dataTransfer.getData("text/html");
    }
}

```

<br>

## @#￥3.获取table的html并包含table标签本身
`$("table").prop("outerHTML")`

<br>

## @#￥4.将路径中的''变成'/'
`str.replaceAll("\\", "/");`

<br>

### 【2018-05-29】
## @#￥5.页面初始化时调用list方法并入传参，list方法执行了两遍
#### *解决方法：
本来的写法：
`$(".catalog").click(list(1));`  

修改后的写法：
```
$(".catalog").click(function(){
    list(1);
});
```

<br>

### 【2018-06-07】
## @#￥6.input的change事件
```
$('#search_input').change(function(){
    ......
});
```
如上的代码在input失去焦点以后才会触发，进行修改如下
```
$('#search_input').on('input propertychange', function(){
    ......
});
```