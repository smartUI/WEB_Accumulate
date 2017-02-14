# ES6支持IE8

# 关键字

原理很简单 把双引号包含住,就不会有关键字错误了

## es3ify方法

例如class,default等关键字如果单独声明出来

比较常见的是babel转化import时会出现这句话

```javascript
function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { default: obj }; }

```

这里的default在IE8下就会报错

解决方法是在webpack中引入`es3ify-loader`

使用方法

```javascript
npm i es3ify-loader --save

//在webpack中
{
         test: /\.js$/,
         loaders: ['es3ify','babel'] //es3ify必须放在babel前
},
//或者
{
    postLoaders: [ //postLoaders表明在loader之后
      { test: /\.js$/, loader: 'es3ify' }
    ]
}
```

使用后的编码

```javascript
function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }
```
## babel es3插件

1. http://babeljs.io/docs/plugins/transform-es3-member-expression-literals/
2. http://babeljs.io/docs/plugins/transform-es3-property-literals/

在babel引入这两个plugins即可

# Object.defineProperty问题

babel中

```javascript
export default 42
```

会转化成

```javascript
Object.defineProperty(exports, "__esModule", {
  value: true
});
 
exports.default = 42;
```

在IE8中

`Object.defineProperty`没有实现,并且不让别人访问或修改!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

所以在plugins引入`babel-plugin-transform-es2015-modules-commonjs `

https://www.npmjs.com/package/babel-plugin-transform-es2015-modules-commonjs

就可以转化成

```javascript
exports.__esModule = true;
exports.default = 42;
```

## 参考链接

1. https://github.com/sorrycc/es3ify-loader/issues/3
2. https://github.com/sorrycc/es3ify-loader/issues/1
3. http://www.aliued.com/?p=3240
4. object.defineProperty解决: https://github.com/reactjs/react-redux/issues/227