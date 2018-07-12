# Vue知识整理 #

> **作者 :  Mr.Xue**

> **时间：2018/2/6**

相关文档链接：

→ [Vue官方文档](https://cn.vuejs.org/v2/guide/)

→ [Vue-i18n多语言配置](https://github.com/Mr-xue/vue-doc-share/blob/master/%E5%A4%9A%E8%AF%AD%E8%A8%80%E9%85%8D%E7%BD%AE%E7%AE%80%E4%BB%8B.md)

→ [Vue-Router需要掌握知识点](https://github.com/Mr-xue/vue-doc-share/blob/master/vue-router.md)


## 一.Vue-cli搭建 ##

**准备工作：**

1.安装nodejs [下载地址](http://nodejs.cn/download/)，安装后在命令窗口运行以下命令，查看nodejs及npm版本，有版本信息代表安装成功

![](https://i.imgur.com/6QeirZw.png)

2.npm安装成功后，配置淘宝npm镜像，配置成功后可使用cnpm替代npm执行一系列命令

- npm install -g cnpm --registry=https://registry.npm.taobao.org

- [→淘宝镜像官网](https://npm.taobao.org/)


**初始化项目：**

1.全局安装vue-cli

- npm install -g vue-cli

- vue-cli安装命根据版本的不同可能会发生变化，如果安装失败请参考官方[github说明文档](https://github.com/vuejs/vue-cli)

- 安装完成后，在命令窗口执行 vue -V**（注意：V是大写、大写、大写）**查看脚手架版本，有信息代表安装成功。


2.使用vue-cli创建基于webpack的脚手架环境

- vue init webpack 项目名称

![](https://i.imgur.com/KYfRYPg.png)

- 现阶段除了vue-router需要安装，其都选no

- 最后选择Yes,use Npm. 脚手架会在项目创建完成后，自动安装依赖.( 如果依赖安装失败，删除项目目录下的**node_modules**文件夹，然后在当前目录下执行**cnpm install**命令重新安装依赖)

3.关于启动项目及构建项目

启动项目：npm run dev

构建项目：npm run build  (构建后会在本目录生成一个dist的目录，用于线上环境部署)

## 二.如何引用第三方插件（重要） ##
[参考此处](https://segmentfault.com/a/1190000007020623)

插件分两类:一类是发布过npm安装包的，一类是没有npm安装包的。

> 在引用插件前，可先通过[https://www.npmjs.com/](https://www.npmjs.com/)搜索，查看你想使用的插件有无发布npm安装包（插件可能重名，查看使用方法及简介确定是否是你要用的）

1.有npm安装包：可直接通过 `npm 插件名 --save or --save-dev` 安装，然后在文件中通过import导入
> 例：import fastclick from 'fastclick'

**关于 - -save 与 - -save-dev的区别，需要谨记、谨记、谨记**

**通过- -save安装扩展，扩展信息将会写入到package.json中的dependencies下面，代表此扩展最终线上环境会用到，同时vue-cli在构建项目时，会将该扩展构建到线上环境运行的代码中**
> 例如：幻灯片插件、多语言配置插件等

**通过- -save-dev安装扩展，扩展信息将会写入到package.json中的devDependencies下面,代表此扩展仅会在开发环境用到，项目在最终构建时，不会将此扩展构建到运行环境中**

> 例如：autoprefixer css自动补前缀、babel-polyfill Es6编译

**★★★一定要仔细阅读插件的使用说明，区分运行环境进行安装**


2.引用无npm安装包的插件
可在文件中通过 import引入
> 例：import cookie from '@/assets/js/cookie.js'

如果插件默认没有导出模块，则需要使用ES6的方式手动导出,ES6导出方法[参考](https://www.cnblogs.com/benpaodexiaopangzi/p/6085519.html)
> 常用导出方法：

> export default foo

> export {foo, bar}

> export {foo as bar}


如何配置jquery或其他插件为全局
![](https://i.imgur.com/gqL2GHM.png)

## 三.一些常见配置问题： ##
**注意：以下所有牵扯到配置文件修改的地方，修改完成后均需要重启服务**

1.vue-cli默认启动端口是8080，当启动多个项目时会产生端口冲突，导致启动失败，该怎么办？

答：打开项目根目录下 `config -> index.js`，修改dev下的port参数即可，参看下图
![](https://i.imgur.com/eARfglA.png)

2.将一些常用的目录路径配置到全局，妈妈再也不用担心我每次**../../../** 个没完.

答：打开项目根目录下 `build -> webpack.base.conf.js`，通过配置alias别名，即可实现全局调用

![](https://i.imgur.com/vao3K2B.png)

3.如何配置，可以使别人通过ip访问你本机的vue项目？
答：打开根目录 `config->index.js`，修改dev下的host参数为0.0.0.0，重启项目，同一网络下，别人就可以通过你电脑  ip:端口，访问你的项目了。（修改后本机启动项目可能会无法访问，访问时同样使用 ip：端口 即可）

4.我们在开发环境和线上环境通常调用接口的地址或一些配置选项都不同，如果区分运行环境，调用不同的配置文件？

答：通过 `process.env.NODE_ENV`区分，值为development代表开发环境，值为production代表线上环境。例如：
![](https://i.imgur.com/DOmvXEs.png)




## 四、vue应当掌握的知识点 ##

1.数据的双向绑定，computed的使用

2.component组件的使用，动态component的切换，props传参的使用

3.生命周期钩子函数概念的理解及使用

4.自定义事件，监听与触发

5.watch监听变量变化状态
