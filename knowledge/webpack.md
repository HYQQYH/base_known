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
   

 6. tree shaking:使用uglifyjs-webpack-plugin精简输出-------删除未使用代码，在生成的bundle.js中将不包括未被使用代码。在大型应用程序中可显著进行体积优化。
 7. 使用 inline-source-map 选项在编译时可准确定位到出错的代码处。
 8. 配置:为不同环境编写不同配置，例如开发环境与生产环境使用不同配置。使用webpack-merge可引用共同的配置。
 9. 避免在生产中使用 inline-\*\*\* 和 eval-\*\*\*，因为它们可以增加 bundle 大小，并降低整体性能。生产环境中用source-map,而不是开发环境中的inline-source-map.
 10. 指定环境
 >许多 library 将通过与 process.env.NODE_ENV 环境变量关联，以决定 library 中应该引用哪些内容。例如，当不处于生产环境中时，某些 library 为了使调试变得容易，可能会添加额外的日志记录(log)和测试(test)。其实，当使用 process.env.NODE_ENV === 'production' 时，一些 library 可能针对具体用户的环境进行代码优化，从而删除或添加一些重要代码。我们可以使用 webpack 内置的 DefinePlugin 为所有的依赖定义这个变量：

 11. List item