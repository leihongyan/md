##打开个人主页
	这个是在标签卡页面有个打开私信按钮，如果是从对话框头像点进去标签卡，打开私信只需把这个标签卡页面关了，其他地方就需要打开一个新的对话框
	
	这个name是对话框window的名字
	从其他页面打开标签卡就传个0 ，从对话框打开传个对话框name，这样在标签卡页面判断传的这个name值就行,如果name==对话框，就把window关闭
##收藏
	if($api.hasCls($api.dom('.shoucang'),'sc1')){
        //收藏
            api.ajax({
                url: 'http://api.51fth.com/index.php?d=essay&c=details&m=sc_essay',
                method: 'post',
                data: {
                    values:{zid:zid,uid:uid}
                },
                dataType:'json'
            }, function(ret, err) {
                if(ret){
                    $api.removeCls($api.dom('.shoucang'),'sc1');
                    $api.addCls($api.dom('.shoucang'),'sc2');
                }else{
                    api.toast({
                        msg: '网络错误,请重试',
                        duration: 2000,
                        location: 'bottom'
                    });         
                }
            });
        }else{
            //取消收藏
            api.ajax({
                url: 'http://api.51fth.com/index.php?d=essay&c=details&m=qxsc_essay',
                method: 'post',
                data: {
                    values:{zid:zid,uid:uid}
                },
                dataType:'json'
            }, function(ret, err) {
                if(ret){
                    $api.removeCls($api.dom('.shoucang'),'sc2');
                    $api.addCls($api.dom('.shoucang'),'sc1');
                }else{
                    api.toast({
                        msg: '网络错误,请重试',
                        duration: 2000,
                        location: 'bottom'
                    });         
                }
            });
        }】
##表情
	function replace_em(str){
	    str = str.replace(/\[em_([0-9]*)\]/g,'<img src="../../image/face/$1.gif" border="0" style="display:inline" />');
	    return str;
	}
	$(function(){
	    $('.biaoqing').qqFace({
	        id : 'facebox', //表情盒子的ID
	        assign:'tanpan_nr', //给那个控件赋值
	        path:'../../image/face/'    //表情存放的路径
	    });
	});
	var kai=0;
	$(".face_img").click(function(){
	    if(kai==0){
	        $("#facebox").show();
	        kai=1;
	    }else{
	        $("#facebox").hide();
	        kai=0;
	    }
	})
	$(".tanpan_nr").focus(function(){
	    $("#facebox").hide();
	    kai=0;
	})
##replace（） 方法
	$1、$2、...、$99	与 regexp 中的第 1 到第 99 个子表达式相匹配的文本。
	str = str.replace(/\[em_([0-9]*)\]/g,'<img src="../../image/face/$1.gif" border="0" style="display:inline" />');

	把 "Doe, John" 转换为 "John Doe" 的形式：
	name = "Doe, John";
	name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1");
##好友圈
	1.
		打开好友圈有三个入口，执行的都是同一个方法，但是从标签卡进好友圈的时候，是需要传一个用户id，其他两个不需要，为了区别就传了个参数，就传了个0，根据0来判断是不是 从标签卡进去的
	2.
		下边的那个方式，是在写即时通讯用的，如果是别人的朋友圈，发即时通讯，不会收到消息
		function new_jiazai(){
		    if(id==0){
		        jiazai();
		    }
		}
	3. 好友圈三个入口
		点击发现-->好友圈-->进入好友圈
		进入到其他人的标签卡，点击进入他的好友圈
		自己的标签卡，左上角进入到自己的好友圈
##定位兼容IOS  
		var systemType = api.systemType;
    	if(systemType=="ios"){
    		bMap.initMapSDK(function(ret,err) {
    		    bMap.getLocation({
	    		    accuracy: '100m',
	    		    autoStop: true,
	    		    filter: 1
	    		}, function(ret, err) {
	    		    if (ret.status) {
	    		    	lat=ret.lat;
	    		    	lon=ret.lon;
	    		    }else{
	    		    	lat='37.868062';
	    		    	lon='112.547448';
	    		    }
	    		    jiazai(lon,lat);
	    		});
    		});	
    	}else{
    		bMap.getLocation({
			    accuracy: '100m',
			    autoStop: true,
			    filter: 1
			}, function(ret, err) {
			    if (ret.status) {
			    	lat=ret.lat;
			    	lon=ret.lon;
			    }else{
			    	lat='37.868062';
			    	lon='112.547448';
			    }
			    jiazai(lon,lat);
			});
    	}	