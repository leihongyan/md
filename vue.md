##防止闪烁
	v-cloak
	v-text	
	v-html=‘msg’   相当于{{{}}}  解析成HTML
##计算属性的使用
	1 
		computed:{
			b:function(){//默认调用get
				return this.a+2；		
			}
		}
	*******************
		computed(){
			b:{
				get:function(){
					return this.a+2
				},
				set:function(val){//此处的val为10
					this.a=val
				}
			}
		}
   		

		document.onclick=function(){
			vm.b=10;
		}
	***********************

	*****computed 里面可以放置一些业务逻辑代码，记得return*********
##vue实例简单方法
	1. vm.$el 获得的是dom元素
	2. vm.$data  本身的数据对象data
	3. vm.$mount  手动挂载vue程序
		html:
			<div id="box">
				<span v-text='a'></span>
			</div>
		js:
			var vm=new Vue({
				data:{
					a:1
				}
			})                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
	4. vm.$opations 获取自定义属性
	5. vm.destory  销毁对象
	6. vm.$log()  查看现在数据的状态
##循环
	v-for='value in arr'
	会有重复的数据？--->  track-by='$index/uid'  提高循环的性能
##vue生命周期
	钩子函数：
		created       ----->   实例已经创建
		beforeCompile ----->   编译之前
		compiled      ----->   编译之后
		ready         ----->   插入到文档中
		beforeDestory ----->   销毁之前
		destoryed     ----->   销毁之后
	
				
##过滤器
	一、 vue提供的过滤器
		1. debounce  配合事件  延迟执行
	二、 数据配合使用过滤器
		1. limitBy  限制几个	limitBy  参数（取几个） 从哪开始
		    <li v-for="val in arr | limitBy 2"></li>   
		2. filterBy  过滤数据
		3. orderBy 排序  1 正序  -1  倒序
		4. 
			Vue.filter('toDou',function(input){
				return input<10?'0'+input:''+input;
			})
		5. 过滤html标记   
		6. 双向过滤器   
##自定义指令
		1.		
			Vue.directive('red',{
				bind:function(el){
					el.style.background='red';
				}
				
			})
		2. 
			Vue.directive('focus',{
				inserted:function(el){
					console.log(el)
					el.focus();
				}
			})	
##组件
	1. 全局组件
		<aa-a></aa-a>
		Vue.component('aa-a',{
			template:'<h3>我是标题3</h3>'
		})
	2.局部组件
		var Aaa={
			template:'<h3>我是标题3</h3>'
		}
		var vm=new Vue({
			el:'#box',
			components:{
				'aa-a':Aaa
			}
		}）//只能在box里面使用
	3. data：通过Vue传入数据
		var Aaa={
			template:'<button v-on:click="counter+=1">{{counter}}</button>',
			data:function(){
				return {
					counter:0
				}
			}
		}
		Vue.component('aa-a',Aaa)
	4. 动态组件
		<component :is='a'></component>
	5.父子组件数据传递
		1. 子组件获取父组件data
		示例：
			<template  id='aaa'>
				<div>
					<h1>111</h1>
					 <bbb :m='msg1' :my-msg='msg2'></bbb>
				</div>
			</template>
			
			new Vue({
				el:"#box",
				data:{
					a:'aaa'
				},
				components:{
					'aaa':{
						data:function(){
							return{
								msg1:'我大UIof爬大抽奖哦啊',
								msg2:'dakjpouhgfuidhbufauid'
							}
						},
						template:'#aaa',
						components:{
							'bbb':{
								props:['m','myMsg'],
								template:'<h2>我是bbb组件---->{{m}}----{{myMsg}}</h2>'
							}
						}
					}
				}
			})


			在调用子组件：
				<bbb :m='data'></bbb>
			子组件之内：
				props:['m','myMsg']
				props:{
					'm':String,
					'myMsg':Number
				}
		2. 父级获取子级数据
			 子组件把自己获取到的数据，发送到父级  
			 vm.$emit(事件名称，数据)	
			 v-on
##slot
	slot:位置  槽口 类似angular里的transclude
	多个slot 
		<ul slot="ul-slot">
			<li>11111</li>
		</ul>
		<slot name="ul-slot"></slot>
##vue -> SPA 应用，单页面应用
	vue-resource   交互
	vue-router  路由
	根据不同URL地址，出现不同效果
	
	<a v-link="{path:'/home'}">主页</a>

	1. 单级路由
		<router-link to="/foo">首页</router-link>
	    <router-link to="/bar">新闻</router-link>
	
	
		const Foo = { template: '<div>我是首页</div>' }
	    const Bar = { template: '<div>我是新闻</div>' }
	    const routes = [
			{path:'/',redirect:'/foo'},首页进来默认为foo页面
	        { path: '/foo', component: Foo },
	        { path: '/bar', component: Bar }
	    ]
	    const router = new VueRouter({
	        routes
	    })
	    const app = new Vue({
	        router
	    }).$mount('#app')
	2. 多级路由
	3. 路由其它信息
		/detail/:id/age/:age
		{{$route.params|json}}---->当前参数
		{{$route.path}}----------->当前路径
		{{$route.query}}---------->当前数据
##vue-loader基于webpack
	webpack  模块加载器,一切东西都是模块
	broserify  模块加载，只能加载js
		
		.vue文件
			放置的是vue组件代码
	************************
	简单的目录结构
		index.html  
		main.js  入口文件
		APP.vue  vue文件
		package.json  工程文件（项目依赖、名称、配置） npm init --yes生成
		webpack.config.js  webpack配置文件	
	ES6:模块化开发
		导出模块：export defaut()
		引入模块：import模块名from地址
##webpack 准备工作
	npm install webpack
	npm install webpack-dev-server
	App.vue  -->  变成正常代码  vue-loader	
				
	vue-html-loader css-loader vue-style-loader
	vue-hot-reload-api@1.3.2

	babel-loader  babel-core  babel-plugin-transform-runtime
	babel-preset-es2015 babel-runtime
##vue-cli  脚手架
	个人推荐使用，没有代码检查
	vue init webpack-simple vue-webpack-simple-demo
	基本使用
	1. 
		npm install vue-cli -g  安装vue命令环境
			验证OK？   vue--version
	2. 
		生成项目模板		
			vue init <模板名>本地文件夹名称
	3.
		进入到生成目录里面
			cd  xxx
			npm  install
	4.	
		npm run dev
##vue 2.0 变化
	1.template每个模板，不支持片段代码
		现在：必须有根元素，包裹住所有的代码 
	2.生命周期
		beforeCreate	组件实例刚刚被创建,属性都没有
		created			实例已经创建完成，属性已经绑定
		beforeMount		模板编译之前
		mounted			模板编译之后，代替之前ready  *
		beforeUpdate	组件更新之前
		updated			组件更新完毕	*
		beforeDestroy	组件销毁前
		destroyed		组件销毁后
	3. 循环
		2.0里面默认就可以添加重复数据

		arr.forEach(function(item,index){
	
		});
	
		去掉了隐式一些变量
			$index	$key
	
		之前:
			v-for="(index,val) in array"
		现在:
			v-for="(val,index) in array"
	4. track-by="id"
		变成
			<li v-for="(val,index) in list" :key="index">
	5. 自定义键盘指令
		之前：Vue.directive('on').keyCodes.f1=17;	
	
		现在:  Vue.config.keyCodes.ctrl=17
	6. 自定义过滤器
		Vue.filter('toDou',function(n,a,b){
			alert(a+";"+b)
			return n<10?'0'+n:n;
		})
		自定义过滤器传参

		之前:	{{msg | toDou '12' '5'}}
		现在: 	{{msg | toDou('12','5')}}

#简单的vue使用
##vue 多图片存储
	**html**
		<div v-for="(ii,index1) in rr.img"  :style="style_to(index,index1)" :key="index1"></div>
	**js**
	
		img_zt_to:function(xid,a){
            if(systemType=='ios'){
                return this.zhuti_list[xid].img[a];
            }
            var url=this.zhuti_list[xid].img[a];
            Vue.set(vm.zhuti_list[xid],'img_zt'+a,'../../image/loading_1.gif')
            api.imageCache({
                url: url
            }, function(ret, err) {
                Vue.set(vm.zhuti_list[xid],'img_zt'+a,ret.url);
            })
        },

        style_to:function(index1,index2){
            if(vm.zhuti_list[index1].img.length==1){
               var aa=this.zhuti_list[index1].img_zt0?this.zhuti_list[index1].img_zt0:this.img_zt_to(index1,0);
            }else{
               var aa=eval('this.zhuti_list['+index1+'].img_zt'+index2)?eval('this.zhuti_list['+index1+'].img_zt'+index2):this.img_zt_to(index1,index2);  
            }
            if(vm.zhuti_list[index1].img.length>3){
                var ww='1.6rem'
            }else{
                var ww='1.8rem'
            }
            return {
                backgroundImage:'url('+aa+')',width:ww,height:ww
            };
        }

	