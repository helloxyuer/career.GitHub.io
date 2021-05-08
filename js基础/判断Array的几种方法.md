### 方法一:

```javaScript
function isArray(val){
    return a instanceof Array
}
```
缺:其它frame的Array创建的数组会判断为false

### 方法二:

```javaScript
function isArray(val){
    return val.constructor === Array;
}
```
缺:同上

### 方法三:

```javaScript
function isArray(val){
    return return Object.prototype.toString.call(val) === '[object Array]';
}
```

### 方法四:

```javaScript
function isArray(val){
    return Array.isArray(val)
}
```
