## babel介绍
- 将 es6 转码成 es5 语法，以适应各大浏览器

### 使用
- 全局安装babel:`npm install -g babel`
- 安装babel-cli:'npm install -g babel-cli',建议不要全局安装，不然会产生环境依赖

### 配置
- 在项目根目录下创建`.babelrc`文件进行配置（至于为何要按如下情况配置请自行百度）：
·
{
  "presets": [
        "latest",
        "react",
        "stage-2"
        ],
  "plugins": []
}
·

### 转码
- 在根目录下打开命令行，输入：`babel es6.js -o es5.js` ，即可将es6文件转码成es5文件了

- 需要注意的是，Iterator、Generator、Set、Maps、Proxy、Reflect、Symbol、Promise等全局对象，
以及一些定义在全局对象上的方法（比如Object.assign）都不会转码。因此需要必须使用babel-polyfill，为当前环境提供一个垫片。
`npm install --save babel-polyfill`

### 结合webstorm自动转码
- 完成以上操作后，可以使用命令行进行转码，但开发过程会比较麻烦，因此：
+ 1. 打开webstorm后按住 ctrl+alt+s 打开设置面板
+ 2. 选择‘工具-file watchers-右侧的+号-babel’进行配置
+ 3. 一般只需要修改 program 也就是babel所在的路径这一项

#### 记得可能比较简单，但大概思路是有的，且亲自验证过。
