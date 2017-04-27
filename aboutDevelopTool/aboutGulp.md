[TOC]

## Gulp 使用  --前端自动化构建工具

### 5个核心方法
 - task('任务名',function(){....})

 - src('./*.js')

 - dest('./minjs/')
    指定处理后的文件输出路径

 - watch('./*.js',['任务名1'],['任务名2'])

 - run('任务名')

### 安装
 - `npm install gulp-cli -g` 全局安装

 - 使用时需要在项目中进行非全局安装
    `npm install gulp --save-dev`

### 使用
 - 在当前项目根目录创建 gulpfile.js 文件写具体的任务代码，可以保存为一个模板

 - gulp 插件
    + gulp-uglify 压缩，混淆，适用于js代码
        npm 安装：`npm install gulp-uglify --save-dev`
    + gulp-concat 合并，npm 安装：同上
    + gulp-cssnano 压缩，混淆，适用于css代码，安装同上
    + gulp-htmlmin 压缩 html 代码，需要传入参数
 - gulp 可以与 browser-sync 结合使用

## browser-sync
 1. npm 安装：`npm install browser-sync -g`

 2. 在需要监测的根目录下打开命令窗口，输入命令
    `browser-sync start --server --files "文件路径（可以多个，逗号分隔）"`
    
