##box-shadow动画
	.circle{
	    width:50px;
	    height:50px;
	    border-radius:50%;
	    background:#8c8c8c;
	    color:#fff;
	    line-height:50px;
	    text-align:center;
	    box-shadow:0 0 0 30px transparent;
	    margin:30px auto;
	    transition: box-shadow .6s ease-in-out;
	}
	.circle:hover{
	    box-shadow: 0 0 0 0 rgba(255,255,255,0.2);
	    transition:box-shadow .4s ease-in-out;
	}
##高斯模糊
	.blur-container.blur-3 {
		 --bg: url("background.jpg");
		 background-image: var(--bg);
	}
	.blur-container.blur-3 .blur-box {
		 color: #31405e;
		 width: 100%;
		 height: 100%;
		 max-height: 300px;
		 overflow: hidden;
	}
	.blur-container.blur-3 .blur-box h2 {
	 	font-size: 37px;
	}
	.blur-container.blur-3 .blur-box::before {
		 z-index: 10;
		 opacity: 0.5;
		 background-color: #fff;
	}
	.blur-container.blur-3 .blur-box::after {
		 background-size: cover;
		 background-position: center;
		 background-attachment: fixed;
		 -webkit-filter: blur(15px) brightness(110%);
		 filter: blur(15px) brightness(110%);
		 background-image: var(--bg);
	}
##before after
	.box3 span:hover::after{
        background:#f00;
        transform:rotate(-45deg);

    }
    .box3 span:hover::before{
        background:#f00;
        transform:rotate(45deg);
    }
##queue   dequeue
	$(".next").hover(function(){
        $(".next img").addClass("imghover").delay(300).queue(function(){
            $(".next h3").addClass("imghover");
            $(this).dequeue();
        })
    },function(){
            $(".next h3").removeClass("imghover").delay(300).queue(function(){
                $(".next img").removeClass("imghover")
                $(this).dequeue();
            })
    })

##让一个物体向上浮动2000毫秒(2秒)，并且在前1000毫秒物体完全不透明，而在后1000毫秒物体从完全不透明变成完全透明
	function animateR(){
	    $("#section4object")
	        .delay(1000, "fader")
	        .queue("fader", function(next) {
	        $(this).animate({opacity: 0},{duration: 1000, queue: false});
	        next();//   next()是保证在执行完这次队列后再次执行下一个动画函数
	        })
	        .dequeue("fader")
	        .animate({top: "-=40"}, {duration: 2000})
	}
	function animateU(){
	    $("#section4object2").animate({opacity: 0, top: "-=40"}, {duration: 2000});
	}
	$("#section4start").click(function(){
	    $("#section4object,#section4object2").css({'top':'100px','opacity': '1'}).show();
	    animateR();
	    animateU();
	});
##获取队列长度

	比如用队列名取得匹配元素的长度：
	
	var $queue=$("div").queue('fx');
	很明显，就是取得队列名为'fx'的队列，如果想取得长度的话：
	
	var $length=$('div').queue('fx').length;
	注意这里的队列长度只是匹配元素还未运行的队列长度，当动画运行完之后，队列长度会自动归为0，举下面一个例子：
	
	function animateT(){
	    $("#section2-div").slideToggle('3000')
	    .slideToggle('3000')
	    .hide('3000')
	    .show('3000')
	    .animate({left:'+=200'},2000)
	    .hide('3000')
	    .show('3000')
	    .animate({left:'-=200'},2000,animateT);//在这轮动画结束的时候再调用自己，使动画无限循环下去          
	            }
	然后当点击按钮的时候显示队列的长度：
	
	$("#section2-input").click(function(){
	    var $queue=$("#section2-div").queue('fx');
	    $('#section2-h1').text($queue.length);
	});