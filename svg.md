##svg
	1 基本图形		
		<rect> 方形
		<circle>圆形
		<ellipse>椭圆
		<line>直线
		<polyline>折线
		<polygon>多边形  会闭合
	2 基本属性
		fill 填充
		stroke 描边
		stroke-width 描边粗细
		transform  变形
	3 基本操作API
		* 创建图形
			document.creatElementNS(ns,tagName)
		* 添加图形
			element.appendChild(childElement)
		* 设置/获取属性
			element.setAttribute(name,value)
			element.getAttribute(name)