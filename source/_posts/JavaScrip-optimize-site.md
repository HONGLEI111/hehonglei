---
date: 2024-11-18 11:30:50
title: 使用Javascript技巧优化网站加载速度
cover: https://img.hehonglei.cn/img/0003.avif
tags: 
  - Javascript
categories: 
  - 前端
  - 优化
  - documents
---
# 使用 JavaScript 技巧优化网站加载速度

## DOM 操作：减少重绘，提升效率

频繁的 DOM 操作会触发浏览器重新渲染页面，导致页面卡顿，影响用户体验。
**如何优化：**
**使用 `DocumentFragment` 批量更新 DOM：**

* `DocumentFragment` 是一个轻量级的 DOM 节点，可以用来暂时存储多个 DOM 元素，然后一次性添加到页面中。  这样可以有效减少页面重绘次数，提升性能。
* 例如，在循环添加多个元素时，可以使用 `DocumentFragment` 将所有元素构建好，最后再添加到页面中。

```js
// 使用 DocumentFragment 批量添加元素
const fragment = document.createDocumentFragment();
const data = ['Item 1', 'Item 2', 'Item 3'];
data.forEach(item => {
	const element = document.createElement('div');
	element.textContent = item;
	fragment.appendChild(element);
});
document.body.appendChild(fragment);
```

* **构建 UI 结构后再插入 DOM：**
  
  * 尽量将 DOM 操作放在函数内部，先构建好完整的 UI 结构，然后一次性插入到 DOM 中，而不是逐个添加元素。
  
  ## 事件监听器：防抖与节流，巧妙控制
  
  频繁的事件触发会让浏览器不堪重负，导致页面卡顿。
  **如何优化：**
* **防抖 (Debounce)：** 在一定时间内，只执行一次函数。 例如，用户输入时，只在用户停止输入一段时间后才执行查询操作，避免频繁的网络请求。

```
function debounce(func, delay) {
  let timeout;
  return function(...args) {
  clearTimeout(timeout);
  timeout = setTimeout(() => {
  func.apply(this, args);
  }, delay);
  };
  }
// 使用防抖函数监听输入事件
const input = document.getElementById('search-input');
input.addEventListener('input', debounce(search, 500)); // 500ms 延迟
```

* **节流 (Throttle)：** 在一定时间内，只允许函数执行一次。 例如，滚动事件，只在滚动一段时间后才触发回调函数，避免频繁的 DOM 操作。

```
function throttle(func, delay) {
  let lastTime = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastTime >= delay) {
      func.apply(this, args);
      lastTime = now;
    }
  };
}

// 使用节流函数监听滚动事件
window.addEventListener('scroll', throttle(handleScroll, 100)); // 100ms 间隔
```

## 延迟加载：优化用户体验，加速首屏

对于一些用户暂时不需要的资源，例如图片或脚本，我们可以采用延迟加载的方式，等到用户需要的时候再加载。 这样可以减少页面初始加载时间，提高用户体验。

**如何优化：**

* **图片延迟加载：**
  * 使用 `loading="lazy"` 属性对图片进行延迟加载，只有当图片出现在视窗内时才加载。
  * 浏览器会自动判断图片是否在视窗内，如果在，则自动加载图片。

```
<img src="image.jpg" loading="lazy" alt="延迟加载的图片">
```

* **脚本延迟加载：**
  * 使用 `defer` 或 `async` 属性来延迟加载脚本。
  * `defer` 属性会等到 HTML 解析完成后再执行脚本，而 `async` 属性则会并行下载和执行脚本。

```
<script src="script.js" defer></script>
```

## Web Workers：解放主线程，提升性能

JavaScript 通常在主线程上运行，如果遇到一些性能密集型任务，例如复杂的计算或数据处理，就会导致页面卡顿。  为了避免这种情况，我们可以使用 Web Workers 将这些任务转移到独立的线程中执行，从而释放主线程的压力，提升用户体验。

**如何优化：**

* 创建一个 `Worker` 对象，指定要执行的脚本文件。
* 向 worker 发送消息，告诉它开始执行任务。
* 监听 worker 的消息，当 worker 完成任务后会发送消息到主线程，主线程收到消息后进行相应的处理。

```
// 在 worker.js 中定义要执行的任务
// 创建 Web Worker 对象
const worker = new Worker('worker.js');

// 向 worker 发送消息
worker.postMessage('start');

// 监听 worker 的消息
worker.onmessage = (e) => {
console.log(`Worker said: ${e.data}`);
};
```

## 原生 JavaScript：精简代码，提高效率

虽然一些 JavaScript 库，例如 jQuery，可以简化开发流程，但它们也会带来额外的负担，例如增加文件大小和加载时间。  现代的原生 JavaScript 已经拥有了丰富的功能，能够满足大多数开发需求。 因此，我们应该尽可能使用原生 JavaScript，减少对库的依赖。

**示例：**

```
// 使用原生 JavaScript 获取元素，然后使用 classList.add 添加类名
const element = document.getElementById('myElement');
element.classList.add('active');

// 使用 jQuery 获取元素，然后使用 addClass 添加类名
$('#myElement').addClass('active');
```

## 异步加载：并行下载，提高速度

如果页面上有多个 JavaScript 文件，而且它们都在主线程上执行，那么它们可能会阻塞页面渲染，导致页面加载速度变慢。 为了解决这个问题，我们可以使用 `async` 和 `defer` 属性来控制脚本的加载和执行顺序。

* `defer` 属性会等到 HTML 解析完成后再执行脚本，不会阻塞页面渲染。
* `async` 属性会异步下载和执行脚本，不会阻塞页面渲染，但执行顺序不确定。

**示例：**

```
<script src="script1.js" defer></script>
<script src="script2.js" async></script>
```

## 代码分割：按需加载，减轻负担

当网站越来越庞大时，JavaScript 代码也会越来越多，这会导致页面加载时间变长。  为了解决这个问题，我们可以使用代码分割将 JavaScript 代码分成多个模块，只加载用户需要的模块。

**如何优化：**

* **使用动态导入：** `import()` 函数可以动态加载模块，只在需要的时候才加载。

```
// 仅在需要的时候加载模块
if (condition) {
  import('./module.js').then(module => {
    module.someFunction();
  });
}
```

## 全局变量：减少依赖，避免冲突

全局变量就像共享的玩具，如果大家都不注意，很容易发生冲突，导致程序出现错误。 为了避免这种情况，我们应该尽可能减少对全局变量的依赖，尽量使用局部变量或函数闭包来管理变量。

**示例：**

```
// 使用局部变量
function myFunction() {
  let localVariable = 'This is a local variable';
  console.log(localVariable);
}

// 使用函数闭包
function outerFunction() {
  let outerVariable = 'This is an outer variable';
  function innerFunction() {
    console.log(outerVariable);
  }
  innerFunction();
}
```

## 循环优化：提高效率，节省时间

循环和迭代是程序中常见的操作，但如果处理不当，也会成为性能瓶颈。 为了提升性能，我们可以采取一些优化措施。

**如何优化：**

* **缓存循环次数：** 在循环中，尽量不要反复访问数组的长度，可以先将长度缓存到一个变量中，避免重复计算。
* **避免不必要的 DOM 操作：** 在循环中，尽量不要进行 DOM 操作，可以先将所有 DOM 操作收集起来，最后一次性执行。

**示例：**

```
// 缓存循环次数
const array = [1, 2, 3, 4];
for (let i = 0, len = array.length; i < len; i++) {
  console.log(array[i]);
}

// 避免不必要的 DOM 操作
const items = [];
for (let i = 0; i < 10; i++) {
  items.push(`<div>${i}</div>`);
}
const container = document.getElementById('container');
container.innerHTML = items.join('');
```

## 浏览器缓存：加速访问，提升体验

浏览器自带缓存机制，可以将用户访问过的网页内容存储在本地，下次用户访问时，可以直接从本地加载内容，而不需要重新向服务器请求。

**如何优化：**

* **设置 HTTP 头部：** 可以通过设置 HTTP 头部，控制浏览器缓存的内容。

**示例：**

```
// 设置缓存时间为一年
Cache-Control: public, max-age=31536000

```







