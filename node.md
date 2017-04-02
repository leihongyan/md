##对module.exports赋值
	1 
		module.exports = {
		    hello: hello,
		    greet: greet
		};
	2
		exports.hello = hello;
		exports.greet = greet;
##异步读取一个文本文件
	'use strict';

	var fs = require('fs');
	
	fs.readFile('sample.txt', 'utf-8', function (err, data) {
	    if (err) {
	        console.log(err);
	    } else {
	        console.log(data);
	    }
	});
##同步读取一个文件
	'use strict';

	var fs = require('fs');
	
	var data = fs.readFileSync('sample.txt', 'utf-8');
	console.log(data);
##异步读取一个图片文件
	'use strict';

	var fs = require('fs');
	
	fs.readFile('sample.png', function (err, data) {
	    if (err) {
	        console.log(err);
	    } else {
	        console.log(data);
	        console.log(data.length + ' bytes');
	    }
	});
##将数据写入文件
	'use strict';

	var fs = require('fs');
	
	var data = 'Hello, Node.js';
	fs.writeFile('output.txt', data, function (err) {
	    if (err) {
	        console.log(err);
	    } else {
	        console.log('ok.');
	    }
	});
##创建一个简易的httpserver
	Node.js  Http server请求和响应的原理
	创建一个server对象（利用createServer 和回调函数），当我们的server获取的到来请求的时候，我们node.js就会通过Node 中的事件分发机制调用我们的回调函数，从而我们能够获取到请求的信息
##获取请求参数的方法
	//第一种利用querystring的方式获取参数的方法
     var parseRlt=url.parse(req.url).query;
    var nameValue=qs.parse(parseRlt)['name'];
    console.log('nameL:',nameValue);
    //第二种利用URL的方式获取参数的方法
    var parseRlt2=url.parse(req.url,true).query;
	console.log(parseRlt2.age);
##路由(利用request.url获取客户端的请求来去判断)

	    function onRequest(request,response){
    		request.url
    	}
	1 请求 / （index）
	2 请求 / （login）
	3 请求 / （resgister）
##处理Node.js中post的请求
	需要注册两个listener来实现，data  end
	request.addListener('data',function)
	request.addListener('end',function)
##events
	var EventEmitter=require("events").EventEmitter;
	var life=new EventEmitter()
	life.setMaxListeners(11)

	life.emit('hello','anna');
	life.removeAllListeners();//移除所有的事件
	//查看长度
	console.log(life.listeners('hello').length);
	console.log(EventEmitter.listenerCount(life,'hello'))