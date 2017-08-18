##跳转页面的两种方式

	一、

	api.openFrame ({
        name: 'AllGroup',
        url: '../AllGroup.html',
        reload:'true',
        rect:{
            x:0,
            y:41,
            w:'auto',
            h:'auto'
        },
        bounces: false,
        pageParam: {
            "id":api.pageParam.id 
        }
    });

	二、

	api.openWin({
		name: type,
		url: 'header/'+type+'.html',
		bounces: false,
		pageParam: {
		"id":id	//id
		}
	});
	说明：pageParam是用来在页面间传值的，获取上一页面传来的值的方式是api.pageParam.id(其中id是在传值时的变量名,若变量名为name,这里就写api.pageParam.name).
	
	三、关闭页面
	
	api.closeWin({name:pagename});pagename是所要关闭页面的全名称
##沉浸式效果实现

	在config.xml文件配置是否开启:

	<preference name="statusBarAppearance" value="true" />
	沉浸式效果配置说明
	在Window或Frame的apiready事件后，调用$api.fixStatusBar()方法;
##CSS Framework
	清除浏览器默认样式（借鉴CSS Reset，Normalize.css）
	禁用系统长按菜单（-webkit-touch-callout:none）
	禁用字体大小自动调整（-webkit-text-size-adjust:none）
	去掉点击高亮（-webkit-tap-highlight-color:rgba(0, 0, 0, 0)）
	禁止选择内容（-webkit-user-select:none）
	清除浮动（.clearfix）
	加载更多默认样式（.loading_more）
##
		<permission name="call"/>打电话
	  <permission name="sms"/>短信
	  <permission name="camera"/>相机
	  <permission name="record"/>录音
	  <permission name="location"/>位置
	  <permission name="fileSystem"/>
	  <permission name="internet"/>
	  <permission name="bootCompleted"/>开机启动
	  <permission name="hardware"/>控制振动/闪光灯/屏幕休眠
	  <permission name="contact"/>联系人
##选择器
	var main = $api.byId('main');
	var headerPos = $api.offset(header);
##pageParam
	页面参数，JSON 对象类型

	用于获取页面间传递的参数值，为 openWin()、openFrame() 等方法中的 pageParam 参数对应值
##打开一个frame组
	api.openFrameGroup({
    name: 'group1',
    background: '#fff',
    scrollEnabled: false,
    rect: {
        x: 0,
        y: 0,
        w: 'auto',
        h: 'auto'
    },
    index: 0,
    frames: [{
        name: 'frame1',
        url: 'frame1.html',
        bgColor: '#fff'
    }, {
        name: 'frame2',
        url: 'frame2.html',
        bgColor: '#fff'
    }]
	}, function(ret, err) {
    	var index = ret.index;
	});
##关闭一个frame组
	api.closeFrameGroup({
    	name: 'group1'
	});
##execscript
	// 通用header的window
	var OpenCommon=function(name,title){
		api.execscript({
			name:'root',
			script:'indexOpenCommon("'+name+'","'+title+'")' 	
		})
	}
##setPrefs   localstorage  sendEvent
	sendEvent和setPrefs 这两个方法虽然都可以实现传值的功能，但
	是不建议使用此方法进行传值，如果是上级页面传值给下级页面的话建议使用openwin或者openframe里面的pageParam参数实现，
	如果是跨页面或者下级给上级传值建议使用execScript方法实现
##widget
	widget路径指的是最外面的路径
##使用flex布局出现的问题
	关于box-flex与flex两者之间实现的功能相同，但是对于不同的浏览器之间的兼容的问题有着不同的使用情况
	在apicloud中，使用09年的box-flex才起到作用	、
	有如下：
		1  
			-webkit-box-pack:justify;（相当于space-between）
			-webkit-justify-content:space-between;
		2 
			-webkit-box-align:center;
	        -webkit-align-items: center;
	        justify-content: center;
	        -webkit-box-pack:center;
	        -webkit-justify-content:center;
		3  	
			display: -webkit-box;
            display: -webkit-flex;
            display: flex;
		4
            -webkit-box-orient: vertical;
            box-orient: vertical;
		5
            -webkit-flex-direction: column;
            flex-direction: column;
		6 
			弹性盒子：
			-webkit-box-flex: 1; 
			-webkit-flex: 1;
			flex: 1;
		7  
			-webkit-box-orient:horizontal
			-webkit-flex-flow:row
			flex-flow:row
		8
			-webkit-box-orient:vertical
			-webkit-flex-flow:column
			flex-flow:column
##倒计时
		var toDouble = function(num){
                var json;
                if (num < 10) {
                    num = '0' + num;
                } else{
                    num = num + '';
                }
                json = {
                    'n1': num.charAt(0),
                    'n2': num.charAt(1)
                };
                
                return json;
        }
	    var h1=$api.byId("h1");
	    var h2=$api.byId("h2");
	    var m1=$api.byId("m1");
	    var m2=$api.byId("m2");
	    var s1=$api.byId("s1");
	    var s2=$api.byId("s2");
	    var countTimer;
	    var countDown = function(date){
        	var  counting = (date.getTime() - (new Date().getTime()))/1000;
        	countDownTimer = setInterval(function(){
                counting -= 1; 
                if (counting <= 0) {
                    // 倒计时结束……
                    clearInterval(countDownTimer);
                }
                var hh = parseInt(counting/3600);
                var mm = parseInt((counting-hh*3600)/60);
                var ss = parseInt(counting - hh*3600 - mm*60);
                // toDouble(counting);
                $api.text(h1,toDouble(hh).n1);
                $api.text(h2,toDouble(hh).n2);
                $api.text(m1,toDouble(mm).n1);
                $api.text(m2,toDouble(mm).n2);
                $api.text(s1,toDouble(ss).n1);
                $api.text(s2,toDouble(ss).n2);

            },1000)
	    }
	    var countDownTime = new Date();
        countDownTime.setMinutes(countDownTime.getMinutes()+25);
	    countDown(countDownTime);
##前端框架
- val

		var input=$api.dom("input");
	   	$api.val(input,"45");
	   	alert($api.val(input));
- html	

		var html=$api.dom("p");
		$api.html(html,'<h1>world</h1>');
		alert($api.html(html));
- offset	

 		
		var offset=$api.offset(html);
		var width=offset.w;
		var height=offset.h;
		alert(width);
		alert(offset)
- setstorage
    
 		$api.setStorage('name','Tom');
		alert($api.getStorage('name'))
##防止iOS手机将数字转换成手机号码
	<meta name="format-detection" content="telephone=no"/>
##api+vue
	1. 转义
		"'xuan_new_qz('+row.uid+',\''+row.nickname+'\')'"