 1. 删除软件包：
 参考：https://www.linuxdashen.com/debianubuntu%E6%B8%85%E7%90%86%E7%A1%AC%E7%9B%98%E7%A9%BA%E9%97%B4%E7%9A%848%E4%B8%AA%E6%8A%80%E5%B7%A7
 >删除软件包：
sudo apt-get remove <package-name>
sudo apt-get purge <package-name>
remove是删除软件包，purge是删除配置文件。
查看系统上哪些软件包留下了残余的配置文件：
dpkg -l | grep "^rc"
删除这些软件包：
dpkg --list | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
删除孤儿软件包：
sudo apt-get autoremove 

 2. npm install 速度慢 
>换为国内镜像：
npm install --registry=http://registry.npm.taobao.org
永久设置：
npm config set registry http://registry.npm.taobao.org 

 3. webpack,intelliJ环境配置:
 https://docs.google.com/document/d/1skstzLF4PwscUjcJ5tWjJSg0rmo68L7cHglDl62iRUA/edit
 

 4. 使用 webpack-dev-server
 >运行命令：run start
 >可实时刷新页面
 

 5. 模块热替换HMR：在运行时更新各种模块，而无需进行完全刷新。
 >devServer: {
      contentBase: './dist',
     hot: true
    },
   

 6. List item