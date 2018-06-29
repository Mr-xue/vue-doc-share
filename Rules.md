## 前端开发规范 ##

[参考：Vue官方风格指南](https://cn.vuejs.org/v2/style-guide/#%E8%A7%84%E5%88%99%E5%BD%92%E7%B1%BB)

**1.所有html选择器的命名禁用驼峰**

>错误：exampleClass

>正确：example-class


**2.vue模板的命名统一使用大驼峰，组件名应该始终是多个单词的，根组件 App 除外( 这样做可以避免跟现有的以及未来的 HTML 元素相冲突，因为所有的 HTML 元素名称都是单个单词的 )**

>错误：header.vue

>正确：BaseHeader.vue

**3.vue路由配置统一使用懒加载配置方法，页面中组件的引用根据情况尽量使用异步组件的引用方式**

**4.Prop 定义应该尽量详细，至少需要指定其类型**

	// 完美主义者的做法
	props: {
	  status: {
	    type: String,
	    required: true,
		default:xxx,
	    validator: function (value) {
	      return [
	        'syncing',
	        'synced',
	        'version-conflict',
	        'error'
	      ].indexOf(value) !== -1
	    }
	  }
	}

**5.模板文件中，使用注释对DOM模块进行标识**

	<!-- 模块名 start-->

	  HTML代码

	<!-- 模块名 end-->

**6.在使用Vue的混入模式时,自定义的私有属性使用 $_ 前缀。并附带一个命名空间以回避和其它插件的冲突 (比如 `$_yourPluginName` )**


**7.为组件样式设置作用域,防止组件之间的样式冲突**

> 方法1：通过scoped

> 方法2：根据组件的根元素选择器，配合less进行层级控制