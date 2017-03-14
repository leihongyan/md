##canvas
	1 绘制矩形
		ctx.fillStyle="#FF0000";
		ctx.fillRect(0,0,150,75);
		设置fillStyle属性可以是CSS颜色，渐变，或图案。fillStyle 默认设置是#000000（黑色）。
		fillRect(x,y,width,height) 方法定义了矩形当前的填充方式

	2 绘制线段
		ctx.moveTo(0,0);
		ctx.lineTo(200,100);
		ctx.stroke();
	3 绘制圆形
		ctx.beginPath();
		ctx.arc(95,50,40,0,2*Math.PI);
		ctx.stroke();
	4 stroke与fill
		fill 填充图案  fillText   填充文字
		stroke 描边		strokeText  对文字描边	
	5 渐变
		// 创建渐变
		var grd=ctx.createLinearGradient(0,0,200,0);
		grd.addColorStop(0,"red");
		grd.addColorStop(1,"white");
		 
		// 填充渐变
		ctx.fillStyle=grd;
		ctx.fillRect(10,10,150,80);
	6 图像
		var img=new Image();
	    img.src="1.jpg"
	    c.drawImage(img,0,0);、
##地理位置
	1 使用地理位置
		var x=document.getElementById("demo");
		function getLocation()
		  {
		  if (navigator.geolocation)
		    {
		    navigator.geolocation.getCurrentPosition(showPosition);
		    }
		  else{x.innerHTML="Geolocation is not supported by this browser.";}
		  }
		function showPosition(position)
		  {
		  x.innerHTML="Latitude: " + position.coords.latitude +
		  "<br />Longitude: " + position.coords.longitude;
		  }
##WEB 存储
	localStorage - 没有时间限制的数据存储
	sessionStorage - 针对一个 session 的数据存储


	---------进行本地存储，使用localstorage.setItem  localstorage.getItem---

	if (typeof(Storage) !== "undefined") {
    // Store
    localStorage.setItem("lastname", "Gates");
    // Retrieve
    document.getElementById("result").innerHTML = localStorage.getItem("lastname");
	} else {
	    document.getElementById("result").innerHTML = "抱歉！您的浏览器不支持 Web Storage ...";
	}

	--------进行访问次数的判定---------------------

	if(localStorage.pagecount){
        localStorage.pagecount=Number(localStorage.pagecount)+1;
    }else{
        localStorage.pagecount=1;
    }
    demo.innerHTML=localStorage.pagecount+"次"
	