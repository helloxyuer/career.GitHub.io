# BFC(Block Formatting Context) 块格式化上下文  
## 如何产生BFC
* float的值不是none。
* position的值不是static或者relative。
* display的值是inline-block、table-cell、flex、table-caption或者inline-flex
* overflow的值不是visible

## BFC特性
* 两个BFC之间margin不重叠
* 不遮盖float元素（可以清楚内部塌陷）
* 不被float元素遮盖（可以配合float元素实现左右布局）


# 各种长宽高
