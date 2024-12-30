---
title: TypeScript解析Array.filter方法
date: 2024-12-24 10:56:42
cover: https://img.hehonglei.cn/img/0002.avif
tags:
  - TypeScript
  - VUE
  - React
categories:
  - documents
  - 前端
---
## TypeScript解析Array.filter方法


### 需求分析
给定一个整数数组 arr 和一个过滤函数 fn，并返回一个过滤后的数组 filteredArr 。

fn 函数接受一个或两个参数：

arr[i] - arr 中的数字
i - arr[i] 的索引
filteredArr 应该只包含使表达式 fn(arr[i], i) 的值为 真值 的 arr 中的元素。真值 是指 Boolean(value) 返回参数为 true 的值。

### 解析
注意！！*Array.filter 是数组原型上的方法。这个实现是一个函数，接受数组作为第一个参数。
传递给 Array.filter 的回调函数具有对原始数组的引用，作为第三个参数传递。这个实现的回调函数只接受两个参数。
Array.filter 可选地允许你传递一个 thisArg 作为第二个参数。如果提供了 thisArg，传递的回调将绑定到该上下文（假设回调不是箭头函数，因为它们不能绑定）。
Array.filter 处理稀疏数组。例如，如果你编写代码 let arr = Array(100); arr[1]= 10;，Array.filter 只会查看索引 1，并自动过滤掉空索引。*

### for迭代至新数组实现

```
function filter(arr: number[], fn: (n: number, i: number) => any): number[] {
    const newArr: number[] = [];
    for (let i = 0; i < arr.length; ++i) {
        if (fn(arr[i], i)) {
            newArr.push(arr[i]);
        }
    }
    return newArr;
};

```

** 在大多数元素被删除时是最快的。这是因为在这些情况下，昂贵的推入操作很少发生。**
### 使用 For...in 循环
这种方法的特殊之处在于，它优先稀疏数组，省略空索引，只会对单个元素应用过滤，并会自动删除所有空值。
值得注意的是，这是最接近内置 Array.filter 工作方式的方法。因为 Array.filter 需要处理稀疏数组，所以通常比一个假设数组不稀疏的最佳自定义实现更慢。另一个需要注意的是，由于 For...in 循环包括对象原型上的键，因此通常最好使用 Object.keys()。
```
function filter(arr: number[], fn: (n: number, i: number) => any): number[] {
    const newArr: number[] = [];
    for (const stringIndex in arr) {
        const i = Number(stringIndex);
        if (fn(arr[i], i)) {
            newArr.push(arr[i]);
        }
    }
    return newArr;
};
```
### 预分配内存
将元素推入数组可能是一个慢操作。这是因为数组可能没有足够的空间来存储新元素，因此需要调整大小。通过使用 new Array(size) 初始化数组，可以避免这些高代价的调整大小操作。最后，我们将通过从数组末尾弹出来删除空元素。请注意，当原始数组中移除的元素较少时，此算法的性能最佳。

```
function filter(arr: number[], fn: (n: number, i: number) => any): number[] {
    let size = 0;
    const newArr: number[] = new Array(arr.length);
    for (let i = 0; i < arr.length; ++i) {
        if (fn(arr[i], i)) {
            newArr[size] = arr[i];
            size++;
        }
    }
    // 确保新数组的长度为 size
    while (newArr.length > size) {
        newArr.pop();
    }
    return newArr
};
```
### 利用原数组进行操作
这个方法类似于方法 3 ，但利用了输入数组的内存，避免了创建新数组的成本。需要注意的是，尽管这个解决方案是有效的，但通常**不建议修改传递给函数的参数**。这是因为函数的用户可能不希望他们的数组被修改，这可能导致 bug。请注意，内置的 Array.filter 不会修改输入数组。此方法比前者预分配内存更快，因为不需要创建初始数组。

```
function filter(arr: number[], fn: (n: number, i: number) => any): number[] {
    let size = 0;
    for (let i = 0; i < arr.length; ++i) {
        if (fn(arr[i], i)) {
            arr[size] = arr[i];
            size++;
        }
    }
    // 确保新数组的长度为 size
    while (arr.length > size) {
        arr.pop();
    }
    return arr
};
```
时间复杂度：O(N)。这些算法都会迭代所有元素。</br>
空间复杂度：O(N)。这些算法都会返回一个数组，在最坏的情况下，该数组有 N 个元素。方法 4 的 额外 空间为 O(1)。



