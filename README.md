# LazyLoad

## 介绍

原生 JavaScript 懒加载库，兼容到 IE8+。

效果演示：[https://mqyqingfeng.github.io/LazyLoad/](https://mqyqingfeng.github.io/LazyLoad/)

## 兼容性

IE8+ 

## 依赖

原生 JavaScript 实现，无依赖。

## 大小

压缩后 3KB，gzip 压缩后更小。

## 下载

```js
git clone git@github.com:mqyqingfeng/LazyLoad.git
```

## 使用

```html
<script src="path/lazyload.js"></script>
```

或者

```js
import LazyLoad from 'path/lazyload.js'
```

## 示例

HTML 文件：

```html
<img src="img/loading.gif" data-lazy-src="img/1.jpg">
```

JavaScript 文件：

```js
new LazyLoad();
```

## API

### HTML

通过 `data-lazy-src` 设置图片的地址，当加载时，将该值赋值给 src 属性。

```html
<img src="img/loading.gif" alt="" data-lazy-src="img/1.jpg">
```

也可以通过 `data-lazy-background` 设置背景图片的地址，当加载时，将该值赋值给 `background-image` 属性。

```html
<div data-lazy-background="img/1.jpg"></div>
```

### 初始化

```js
new LazyLoad(options);
```

### options

**1.onload**

当通过懒加载加载完一张图片时触发，每张图片都会触发一次：

```js
new Lazy({
    onload: function(elem){
        // elem 表示该图片元素
        console.log(elem)
        // 你可以通过 elem 操作图片元素
        elem.className = 'loaded';
    }
})
```

**2.useDebounce**

是否使用 debounce 模式，默认值为 `false`，使用 throttle 模式处理滚动事件，当设置为 true 是，使用 debounce 模式处理滚动事件

**3.delay**

默认值为 `250`

当 useDebounce 为 false 的时候，delay 表示滚动时每隔 delay 毫秒时检查一次是否有图片要加载。

当 useDebounce 为 true 的时候，delay 表示停止滚动后 delay 毫秒检查一次是否有图片要加载。

**4.top**

距离顶部视口还有多少 px 的时候就开始加载，默认为 0

**5.bottom**

距离视口底部还有多少 px 的时候就开始加载，默认为 0，当从上往下滚动时，应该使用的是 bottom。

**6.left**

距离视口左边还有多少 px 的时候就开始加载，默认为 0

**7.right**

距离视口右边还有多少 px 的时候就开始加载，默认为 0