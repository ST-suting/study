## npm 配置及使用
 
### 一、npm 配置

 1. 通过 nvm 下载 node 时一般会自行下载 npm，但可能会因为网络等原因出现下载失败的情况，此时可以通过[npm官网](https://www.npmjs.com/)手动下载后放入 node 包内。

 2. 即使在下载 node 时成功安装 npm，但是仍应该单独为 npm 创建一个文件夹，并配置到环境变量中——因为通过 nvm 来管理 node 版本时，其默认都会有一个用于存放全局包的 node_modules 目录，在切换 node 版本时可能会导致在使用其他 node 版本时安装的全局包在这个版本下无法使用，所以，应该为 npm 指定一个唯一的全局包安装目录 node_modules

 3. 在 nvm 同级目录下创建一个 npm 文件夹，并添加到环境变量中
    `变量名：NPM_HOME 变量值：npm 文件夹的路径 `

 4. 为 npm 指定全局存放目录 node_modules
    `先获取当前存放目录，命令：npm config get prefix`
    `设置唯一的全局存放目录，命令：npm config set prefix 存放路径（ D:\Develop\npm ）`

### 二、npm 常用命令

 - `npm init` 初始化 package.json

 - `npm install` 安装 package.json 中的生产依赖和开发依赖 

 - `npm install packageName` 安装指定的包

    + @latest 默认值，安装指定包的最新版本

    + @version 安装指定版本的指定包

    + 参数：--save 将本次安装的包添加到 package.json 文件中的生产依赖
            --save-dev 将本次安装的包添加到 package.json 文件中的开发依赖

 - `npm uninstall` 同上

 - `npm config` 配置 npm 相关选项
    
 - `npm cache` 指定 npm 下载包时的缓存，包括错误信息的保存

 - `npm update` 更新本地已安装的某个包
 
 - `npm install npm@版本号 -g` 安装指定版本的 npm ，也可以用于回退到某个较低版本
