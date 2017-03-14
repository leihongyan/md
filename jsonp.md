##jsonp原理
	首先JSON是一种基于文本的数据交换方式，或者叫做数据描述格式
	当一个网页在请求JavaScript文件时则不受是否跨域的影响，凡是拥有”src”这个属性的标签都拥有跨域的能力，比如<script>、<img>、<iframe>
	所以我们这里运用了script标签的跨域能力，让它用一个callback函数包裹着一段JSON格式的数据，当该数据返回到前端页面的时候，我们再执行这个函数就可以把数据读取出来

	jsonp.html
	
	<!DOCTYPE html>
	<html>
    <head>
        <meta charset="UTF-8">
        <title>Wsscat's jsonp</title>
    </head>
    <body>
        <button onclick="jsonpServer('jsonp.php')">JSONP</button>
    </body>
    <script>
        function jsonpServer(url) {
            var script = document.createElement("script");
            script.setAttribute("type", "text/javascript");
            script.setAttribute("src", url);
            document.body.appendChild(script);
        }   
        function JSON_CALLBACK(data) {
            console.log(data);
        }
    </script>
	</html>

	<?php
	$data = '[{"id":"1","name":"wsscat"},{"id":"2","name":"asw"}]';
	$data = "JSON_CALLBACK(" . $data . ")";
	echo $data;
	?>
##jquery的jsonp方法
	type：请求方式 GET/POST
	url:请求地址
	async:布尔类型，默认为true 表示请求是否为异步，如果为false表示为同步。
	dataType：返回的数据类型
	jsonp：传递给请求处理程序或页面的，用以获得jsonp回调函数名的参数名(一般默认为:callback)
	jsonpCallback：自定义的jsonp回调函数名称，默认为jQuery自动生成的随机函数名，也可以写"?"，jQuery会自动为你处理数据
	success：调用成功执行的函数
	error：异常处理函数

	js代码

	$.ajax({
	            url:'index.php',
	            type:'get',
	            dataType:'jsonp',
	            //jsonp:'JSON_CALLBACK',
	            jsonpCallback:'JSON_CALLBACK',
	            success:function(data){
	                console.log(data)
	            }
	        })
	php代码
	
	<?php
	    $data = '[{"id":"1","name":"wsscat"},{"id":"2","name":"asw"}]';
	    $data = "JSON_CALLBACK(" . $data . ")";
	    echo $data;
	?>