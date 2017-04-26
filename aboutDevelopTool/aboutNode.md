## node环境配置
 - 直接官网下载，稳定版或最新版，这样只能有一个版本

 - 多版本方式，借助第三方工具 nvm 进行管理，window电脑使用nvm-windows,官网：https://github.com/coreybutler/nvm-windows

### 安装 nvm

 1. window电脑使用nvm-windows,官网：https://github.com/coreybutlnvm-windows
 releases -> nvm-noinstall.zip (解压版)

 2. 下载到 E:\Tools\03-develop （自己选择）

 3. D:\Develop 下创建 nvm 和 nodejs 文件夹，将 nvm 包解压到 nvm 文件夹下

 4. 打开 D:\Develop\nvm ，选择 install.cmd 单击右键，直接回车，会自动setting.txt 文件（该文件有可能创建在C盘）
 ```
 root:  D:\Develop\nvm  （改成相对应的路径）
 path: D:\Develop\nodejs  （改成相对应的路径）
 arch: 64 
 proxy: none
 ```

 5. 环境变量：计算机 -> 属性 -> 高级系统设置 -> 环境变量
 NVM_HOME -> 变量名改成：D:\Develop\nvm （与上面对应）
 NVM_SYMLINK -> 变量名改成：D:\Develop\nodejs （与上面对应）
 Path -> 复制路径后改成以下形式（%号开始）：

     ```C:\Program Files (x86)\Intel\iCLS Client\;C:\Program Files\Intel\iCLlient\;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Wiws\System32\WindowsPowerShell\v1.0\;C:\Program Files (x86)\Intel\IntR) Management Engine Components\DAL;C:\Program Files\Intel\Intel(Management Engine Components\DAL;C:\Program Files (x86)\Intel\Intel(Management Engine Components\IPT;C:\Program Files\Intel\Intel(Management Engine Components\IPT;C:\Program Files (x86)\NVIDCorporation\PhysX\Common;%NVM_HOME%;%NVM_SYMLINK%;
     ```

 6. windows + R 打开 cmd :nvm v 查看版本，查询到版本即为成功

### 安装nodejs（同时安装npm）
 - nvm install latest  -> 最新版本

 - nvm install 6.10.2  -> 指定版本

 - nvm list  ->  查看当前所有的node版本

 - nvm use 版本号  ->  切换使用版本Yellow

 - nvm arch ->  查看使用的是64位还是32位

 - 安装 node 时，可能存在 npm 安装失败的情况，此时可尝试安装其他版本的 node，或者直接下载一个 npm 安装包

### npm 安装注意事项
 - 如果采用 nvm 来管理 node 版本，由于 npm 在 node 包内，会导致切换 node 版本时，通过 npm 下载的各项资源无法共享，所以应该为 npm 指定一个唯一的全局安装目录 node_modules，而不是让每个版本的 node 都对应一个各自的安装目录

 - 配置 npm 的环境变量，同 nvm
    `NPM_HOME 路径名`

### 注意事项
 - 由于 nvm 官网在国外，可能会存在下载不下来的情况，可以采用淘宝镜像
     + node 地址：https://npm.taobao.org/mirrors/node

     + npm 地址：https://npm.taobao.org/mirrors/npm

     + 直接使用 nrm 管理包的下载服务器（ registry ）

     + 先通过 npm 下载 nrm ，然后通过 nrm 切换下载地址
        命令：`nrm use taobao`


 - 如果有翻墙软件则会很方便