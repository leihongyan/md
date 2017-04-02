##html

	<script id="j-tmpl" type="text/template">
	{{ if(it.success){ }}
	        <h2>results:</h2>
	        <ul>
	                {{ for (var i = 0, l = it.data.length; i < l; i++) { }}
	                        <li>
	                                <h5>{{=it.data[i].title}}</h5>
	                                <p>{{!it.data[i].message}}</p>
	                        </li>
	                {{ } }}
	        <ul>
	{{ }else{ }}
	        <h2>暂无数据</h2>
	{{ } }}
	</script>
##js
	<script>
	var obj = {
	        success: true,
	        data:[
	                {title:'item1',message:11},
	                {title:'item1',message:22}
	        ]
	}
	var tmpl = document.getElementById('j-tmpl').innerHTML;
	var doTtmpl = doT.template(tmpl);
	console.log(doTtmpl(obj ));
	</script>
##jquery插件
	$.extend({
	tmpl: function(template, data){
	        return doT.template(template).apply(null,[data]);
	}
	});