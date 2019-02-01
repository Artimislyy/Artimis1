#微信小程序第二周总结  
1.App() 函数用来注册一个小程序  

2.前台、后台定义： 当用户点击右上角关闭，或者按了设备 Home 键离开微信，小程序并没有直接销毁，而是进入了后台；当再次进入微信或再次打开小程序，又会从后台进入前台。需要注意的是：只有当小程序进入后台一定时间，或者系统资源占用过高，才会被真正的销毁。  

3.onLaunch，onShow，onHide(),vonReady()  

4.全局的 getApp() 函数可以用来获取到小程序 App 实例。  

5.data 是页面第一次渲染使用的初始数据。  
```
data:{  
    id:0,
    a:1,
    b:2,
    bol:false,
    obj1:{
      name:"六筒",
      key:"hello"
    },
    arr:[1,2,3,4,5,6,7,8,9,10,5,5,4,4,4,3,4,11,1,2,1,23]
  }
  ```   
  
  6.路由  
  url:小程序内的跳转链接  
  hover-class:指定点击时的样式类
  ```
  <navigator
    url="/page/navigate/navigate?title=navigate"
    hover-class="navigator-hover"
  >
  ```  
  
  7.bool值的应用  
  ```
  <button bindtap='show'>显示隐藏</button>
<view wx:if="{{bol}}">条件渲染显示</view>

show:function(){
    this.setData({
      bol:!this.data.bol
    });
  }  
  ```
  
  8.{{}}的应用  
  a.三元运算
  b.算数运算  
  c.逻辑判断  
  d.字符串运算  
  e.数据路径运算  
  ```
  <view wx:if="{{id>1}}">我大于1</view>
<view wx:elif="{{id<=1}}">我小于等于1</view>
<block wx:if="{{true}}">
    <view>1</view>
    <view>2</view>
</block>
<text hidden='{{true}}'>你打我呀</text>
<view wx:for="{{arr}}">天数：{{item}}</view>
<view>{{object.key}}</view>  
```  
9.模板  
上述方式可以随意组合，但是如有存在变量名相同的情况，后边的会覆盖前面  
```
<!--定义模板-->
<template name="object">
  <view>{{key}}</view>
  <view>{{name}}</view>
</template>
<!--模板的使用-->
<!--你要调用哪一个模板，并且改变数据-->
<!--<template is="object" data="{{a:1,b:1}}"></template>-->  
<!--也可以用扩展运算符 ... 来将一个对象展开-->
<template is="object" data="{{...obj1}}"></template>   
 花括号和引号之间如果有空格，将最终被解析成为字符串
 <view wx:for="{{[1,2,3]}} ">
  {{item}}
</view>  
等同于  
<view wx:for="{{[1,2,3] + ' '}}">
  {{item}}
</view>  
当 wx:for 的值为字符串时，会将字符串解析成字符串数组  
<view wx:for="array">
  {{item}}
</view>  
等同于  
<view wx:for="{{['a','r','r','a','y']}}">
  {{item}}
</view>
```  
10.ctrl+/  快速注释  

11.wx:for
```
<!--一般用index表示下标名，用item表示变量名-->
<view wx:for="{{arr}}" wx:for-index="i" wx:for-item="a">
  下标变量{{i}}:变量名{{a}}
</view>
```  
12.九九乘法表的应用
```
<view wx:for="{{[1,2,3,4,5,6,7,8,9]}}" wx:for-item="i">
  <view style="display:inline-block;width:50px;"  wx:for="{{[1,2,3,4,5,6,7,8,9]}}" wx:for-item="j">
    <view wx:if ="{{j<=i}}">
      {{i}}*{{j}}={{i*j}} 
    </view>
  </view>
</view>
```    

13.如果要一次性判断多个组件标签，可以使用一个 <block/> 标签将多个组件包装起来  

14.如果需要频繁切换的情景下，用 hidden 更好，如果在运行时条件不大可能改变则 wx:if 较好  

15.模板
a.使用 is 属性，声明需要的使用的模板，然后将模板所需要的 data 传入
b.模板拥有自己的作用域，只能使用 data 传入的数据以及模板定义文件中定义的 <wxs /> 模块。







  
  
  
