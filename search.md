##搜索
	$(function(){     
		$("input[type=button]").click(function({      
			 var txt=$("input[type=text]").val();      
			 if($.trim(txt)!=""){          
				 $("table tr:not('#theader')").hide().filter(":contains('"+txt+"')").show().css("background","red");      
			 }else{         
				$("table tr:not('#theader')").css("background","#fff").show();       
			}   
		 });   
	}) 
##
This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.