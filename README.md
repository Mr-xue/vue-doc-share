# Vue知识整理 #
> **Author :  Mr.Xue**

> **涉及技术栈 : Vue 2.x + Vue-Router 3.x + Webpack 2.x + Es6**

## 一.Vue-cli搭建 ##

**准备工作：**

1.安装nodejs [下载地址](http://nodejs.cn/download/)，安装后在命令窗口运行以下命令，查看nodejs及npm版本，有版本信息代表安装成功

![](https://i.imgur.com/6QeirZw.png)

2.npm安装成功后，配置淘宝npm镜像，配置成功后可使用cnpm替代npm执行一系列命令

- npm install -g cnpm --registry=https://registry.npm.taobao.org

- [→淘宝镜像官网](https://npm.taobao.org/)


**初始化项目：**

1.全局安装vue-cli

- npm install -g @vue/cli

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