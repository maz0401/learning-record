## 循环相关操作方法

### 1、forEach 和 $.each

> forEach方法中的function回调有三个参数：第一个参数是遍历的数组内容，第二个参数是对应的数组索引，第三个参数是数组本身。

```
[].forEach(function(value,index,array){
　　//code something
});
```

**转换为$.each写法如下：**

```
$.each([],function(index,value,array){
　　//code something
});
```

