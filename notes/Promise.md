## 异步编程核心
程序中现在运行的部分和将来运行的部分之间的关系

## 异步的几种情况


## 宿主来调度事件
js引擎本身没有时间的概念，

## 回调函数的主要问题
* 嵌套和缩进
* 顺序堵塞的大脑无法很好的映射到面向回调异步的代码
* 控制反转，导致信任链的完全断裂


## promise
* 本身没有完全摆脱回调，只是改了回调的位置
* 规范了异步，并且封装了时间相关值的状态