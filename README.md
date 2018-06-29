# 兼容性和浏览器相关

## Chrome浏览器表单自动填充默认样式
> Chrome会在客户登陆过某网站之后, 会自动记住密码 
> 当你下次再次进入该网站的时候, 可以自由的选择登陆的账号, Chrome会为你自动填充密码. 而你无需再输入密码 
> 这本身是一个很好的功能, 但是对于开发者而言, 却有一个很让人难受的问题.
> 当你选择账号密码之后, 你的输入框会变成黄色… x黄色
### 样式分析
> 之所以出现这样的样式, 是因为Chrome会自动为input增加如下样式.
```css
input:-webkit-autofill, textarea:-webkit-autofill, select:-webkit-autofill {
    background-color: rgb(250, 255, 189);
    background-image: none;
    color: rgb(0, 0, 0);
}
```
> 这个样式的优先级也比较高. 
> 无法通过important覆盖(这就比较恶心了).

### 解决方法
1. 关闭浏览器自带填充表单功能
```html
<!-- 对整个表单的设置 -->
<form autocomplete="off">
<!-- 单独对某个组件设置 -->
<input type="text" autocomplete="off">
```
2. 通过纯色的阴影覆盖底(huang)色

```css
input:-webkit-autofill {
 -webkit-box-shadow: 0 0 0px 1000px white inset;
 -webkit-text-fill-color: #333;
}
```