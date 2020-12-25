# React版的自动聚集下一个输入框有兴趣了解一下吗？
## 可用于验证码输入，身份证号输入等场景，写的React版本，提供的更多，效果也更好
[Demo](https://yangdepp.gitee.io/ark/build/index.html#/autofocus)
[源码](https://github.com/yangdepp/ark/tree/master/src/lib/components/AutoFocusNext)


# 0.0.1 更新记录
## v-code 基于vue的验证码输入方案，自动聚焦下一个输入框



本组件是一个PC端的基于vue特性的验证码输入框组件实现

## 思路
1. 用label模拟一个输入框，将真正的输入框隐藏
2. 用户点击输入框，用动画模拟光标闪烁，实则选中了隐藏的输入框
3. watch用户输入的内容，将无效输入(非字母、数字及空格过滤)
4. 将字符串split成数组，放入label中显示
5. 根据数组长度，判断用户有效输入的次数，将光标动画移至下一个输入框，删除同上

## 注意
本组件不合适直接移植到移动端，但是经验证，本组件思路在移动端可以完美实现
若您要移植到移动端，请做相应修改以适配您的需求

## 缺点
不适用于移动光标更改输入的某一个验证码，只能一次输入完或者一次删除完再做修改

## 优点
基于缺点，应禁用方向键，否则会有严重bug，本组件已禁用（大部分这个思路的组件没有实现），见下面代码
```js
// 禁用方向键
forbidMoveCursor(event) {
  if (event.keyCode === 37 || event.keyCode === 39 || event.keyCode === 38 || event.keyCode === 40) {
    event.preventDefault();
  }
},
```

做了较好的正则校验，本组件可以实现只限于字母和数字的输入。

# 0.0.2 更新记录

1. 增加了禁用Home和End键
```js
  // 禁用方向键
  // ↑、←、→、↓、Home、End
  forbidMoveCursor(event) {
    if (event.keyCode >= 35 && event.keyCode <= 40) {
      event.preventDefault();
    }
  }
```
