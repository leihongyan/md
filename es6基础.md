## ES6 常用语法总结
**什么是ECMA？**  
	ECMA是标准，js是实现  
	类似HTML5是标准，IE10，chrom，FF都是实现    

**目前版本：**  
低级浏览器：主要支持ES3.1  
高级浏览器：正在从ES5过渡到ES6  
**历史：**  

	1996 ES1.0   js稳定  Netscape将js提供给ECMA组织，ES正式出现  
	1998 ES2.0    ES2.0正式发布  
	1999 ES3.0    ES3被浏览器被广泛支持  
	2007 ES4.0    ES4过于激进，被废除了  
	2008 ES3.1    4.0退化为严重缩水版的3.1，代号Harmony（和谐）  
	2009 ES5.0    ES5.0正式发布 ，同时公布了Javascript.next也就是后来的6.0  
	2011 ES5.1    ES5.1成为ISO国际标准  
	2013 ES6.0    ES6.0 制定草案  
	2013.12  ES6.0  ES6.0草案发布    
	2015.6 ES6.0    ES6.0预计发布正式版，同时JavaScript.next指向ES7.0  

---------------------------------------------------
**兼容性：**  
    目前为止 ES5 ES6支持情况，凑合  
    nodejs用的就是chrom内核，在node中可以使用ES5 ES6很多特性    
    ES5 和 ES6 已经逐渐沦为后台语言  

--------------------------------------------

**在浏览器里如何使用?**  
    需要用到编译工具

    babel
    --------------------
    traceur ---由Google出的编辑器，把ES6语法编译为ES5
    bootstrap   引导程序，跟css里面认识bootstrap不一样

**在网页上使用**
	 用法一： 
	    <script type="text/javascript" src="traceur.js"></script>
	    <script type="text/javascript" src="bootstrap.js"></script>
	    <script type="module">
	        
	    </script>
	用法二：
	    直接在线编译---主要用于测试
	    bable:http://babeljs.io/repl/
	用法三：
	    直接在node里面使用
	    a). 直接用，需要添加 'use strict'
	    b). node --harmoney_destructuring 1.js
--------------------------------------------------------
1.定义变量 let 已经被浏览器实现了
    let ---用来去定义变量
    代码块：{}包起来的代码，形成了一个作用域，块级作用域
            比如 if  for while
    特点:只能在代码块里面使用
        var 只有函数作用域

    a). let 具备块级作用域
    b). 不允许重复声明
        let a =12;
        let a =5;   //错误
     总结：其实let才接近其他语言的变量  
    
     用处：
        封闭空间：（匿名函数自调用）
             (function(){
                var a=12;
                })()
        现在：
            {
                let a=12;
            }
        i问题：
            之前的解决办法：
            var aBtn=document.getElementsByTagName('input')
            for(var i=0;i<aBtn.length;i++){
                (function(i){
                    aBtn[i].onclick=function(){
                        alert(i)
                    }
                })(i)
            }
            es6 let解决办法：
                var aBtn=document.getElementsByTagName('input')
                for(let i=0;i<aBtn.length;i++){
                        aBtn[i].onclick=function(){
                            alert(i)
                        }
                    }
                }
        总结: 块级作用域，其实就是匿名函数自调用
2. const ---用来定义 常量
    一旦赋值，以后再也修改不了了
    注意：const必须给初始值 ，不能重复声明
          因为以后再也没办法赋值了，所以声明的时候一定得有值
    作用：为了防止意外修改变量
          比如引入库名，组件名
3.字符串连接：
    之前：
        var str="";
        var str='';
    反单引号： var str=``  字符串模板

    之前: "abc'+变量名+'ef"
    现在：`abc${变量名}ef`
------------------------------------------------------------
4.解构赋值： //自我感觉用到的地方不是很多
    var [a,b,c]=[12,5,101];
    var {a,b,c}={b :12,a:4,c:101}; 跟顺序无关

    模式匹配：--- 左侧的样子需要和右侧的样子一样
        var [a,[b,c],d]=[12,[1,2],5];
        console.log(a,b,c,d)

        var [{a,e},[b,c],d]=[{e:'eee',a:'aaa'},[1,2],5]
        console.log(a,b,c,d,e)
    用处-->交互：数据解析
       var arr= [{title:'',href:'',img:''}];
       var [{title,href,img}]=arr;
       console.log(title,href,img);
    解构赋值还可以给默认值：
        语法：
            var {time=12,id=0}={};
        运动框架：
            function move(obj,json,options){
                options=options || {};
                options.time=options.time||300;
            };
            //用结构赋值来表示给一个默认值
            function move(obj,json,{time=300}={}){
               
            };
---------------------------------------------------------
5.复制数组
    a) 循环
    b) Array.from(arr)
    c) var arr2=[...arr]
       '...'的第二个用法：
       function show(...args){
            args.push(5);
            console.log(args)
       }  
       show(1,2,3,4)
------------------------------------------------------
6.循环
     普通：for  
           for in 
      es6: for of 循环
         遍历(迭代、循环)整个对象,  表现 类似 for in
         真正的目的是为了循环 map对象
     Map 对象：
        和json相似，也是一种 key-value 形式
        Map 对象是为了for of 循环配合而生的
        
        var map= new Map()
        设置：
            map.set(name,value);
        获取： 
            map.get(name)
        删除：
            map.delete('a');
            //json:删除  delete map.a
        遍历map：
            不能使用 for in,没有效果
            
            var map=new Map();
            map.set('a','apple');
            map.set('b','banana');
            map.set('c','pear');
            map.set('d','orange');

            for(var name of map){
                console.log(name); // a,apple  b,banana
            }
            for(var [key,value] of map){
                console.log(key,value); // key value
            }
            for(var key of map.keys()){  //只循环key
                console.log(key) 
            }
            for(var val of map.values()){  //只循环val
                console.log(val) 
            }
    for.. of 也可以循环数组：
        只循环值：
            for(var value of arr){}
        支循环索引：
            for(var key of arr.keys()){}
        索引和值都循环：
            for(var some of arr.entries())
-------------------------------------------------------
7.函数
    箭头函数：
        () => {

        }
    注意：
        1>.this的问题：（指的是window）
        2>.arguments,不能使用了
        var json={
            a:1,
            b:2,
            show:()=>{
                alert(this.a)  //undefined
            }
        };
        json.show();
-----------------------------------------------------
8.对象：
    对象语法简洁化：
        单例模式：
            json
            var name='abb';
            var age=101;
            var person={
                name,                  //不需要用key:value的形式了
                age,
                showName(){
                    return this.name;
                },
                showAge(){
                    return this.age
                }
            }
            alert(person.showName())  -->abb
            alert(person.showAge())   -->101
        面向对象：
            之前：
                人类   工人类
                function Person(name,age){   //类，构造函数
                    this.name=name;
                    this.age=age;
                }
                Person.prototype.showName=function(){
                    return this.name;
                }
                Person.prototype.showAge=function(){
                    return this.age;
                }
                var p1=new Person('许嘉宁',23);
                alert(p1.showName())
            ES6:
                类    class
                构造函数   constructor
                class Person{                //类
                    constructor(name,age){
                        this.name=name;
                        this.age=age;
                    }
                    showName(){
                        return this.name;
                    }
                    showAge(){
                        return this.age;
                    }
                }
                var p1=new Person('许嘉宁',20);
                var p2=new Person('aaa',23);
                alert(p1.showName())
        **函数给默认值    
            function move(obj='对象是必须要填写的',json={},options={}){
                console.log(options)
            }
            move();       //给了默认值之后及时不填参数也不会是undefined

--------------------------------------------------------------
9.继承
    之前:  子类.prototype=new 父类
        function Worker(name,age){
            Person.apply(this,arguments);
        }
        Worker.prototype=new Person();
        var w1=new Worker('ddd',20);
        alert(w1.showName());
    es6:
        class Worker extends Person{
            constructor(name,age,job="扫地的"){
                super(name,age);   //调用父级的构造
                this.job=job;
            }
            showJob(){
                return this.job
            }
        }
        var w1=new Worker('mmm',56);

10.模块化：(可能有兼容性问题：需要引入traceur和bootstrap，type必须写成module)
    seajs requireJs

    ES6自带模块化
        如何定义(导出)模块: 
            const a=12;
            export default a;
            --------------------
            const a =12;
            const b = 10;
            export default {a,b};
        如何使用(引用):
            import modA from './a.js'
---------------------------------------------------------------------
11.Promise:   ---------承诺
    作用：就是一个对象，用来传递异步操作的数据(消息)
    异步：多个操作可以同时进行
    状态：
        pending(等待、处理中)--> Resolve(完成、fullFilled)
                             --> Rejected(拒绝、失败)

    使用：
        var p1=new Promise(function(resolve,reject){
            if(异步处理成功了){
                resolve(成功数据)
            }else{
                reject(失败原因)
            }
        })
        p1.then(成功(resolve),失败(reject))    
       /********************************/
        const fs=require('fs');
        fs.readFile('index.html',function(err,data){
            var p1=Promise(function(resolve,reject){
                if(err){
                    reject(err)
                }else{
                    resolve(data)
                }
            });
            p1.then(function(value){
                console.log(value)
            },function(value){
                console.log(value)
            })
        })
        ---------------------------------------------
        catch-----用来捕获错误
        var p1=new Promise(function(resolve,reject){
            resolve('成功了！');
        })
        p1.then(function(value){
            console.log(value);
            throw '出错了!';
        }).cache(function(e){
            console.log(e);
        })
        --------------------------------------------
        Promise.all-- 可用于多个数据都到达才执行某个操作   
        全部，用于将多个promise对象，组合，包装成一个全新的promise实例
              Promise.all([p1,p2,p3...]);
              所有的Promise对象，都正确，才走正确
              否则，只有一个错误，就失败了
        ----------------------------------------------
        Promise.race ---返回也是一个promise对象
                最先能执行的promise结果，哪个最快，用哪个
                var p1=new Promise(function(resolve,reject){
                    setTimeout(resolve,50,'one');
                })
                var p2=new Promise(function(resolve,reject){
                    setTimeout(resolve,100,'two');
                })
                Promise.race([p1,p2]).then(function(value){
                    console.log(value)
                })
        ----------------------------------------------------
        Promise.reject()  ---生成一个错误的promise
        -------------------------------------------------------
        Promise.resolve()  ---生成一个成功的promsie
            语法：Promise.resolve(value)
                  Promise.resolve(promise)
-----------------------------------------------------------------------
12. Generrator --生成器
    是一个函数
    可以遍历 ， Generrator 就是一个状态机
    语法：
        function show(){          //普通函数

        }
        function* show(){         //Generrator 函数
                yield  xxx
        }
    形式上：
        a). 函数名字前面有 *
        b). 函数内部使用yield语句
    例子：
        function* show(){
            yield 'Hello';
            yield 'World';
            yield 'ES6';
            return 'well';
        }
        var res=show();
        console.log(res.next());  //{value: "Hello", done: false}    done:是否遍历完毕
        console.log(res.next());  //{value: "World", done: false}
        console.log(res.next());  //{value: "ES6", done: false}
        console.log(res.next());  //{value: "undefined", done: true}  undefined:没有返回值
    总结：每次返回一个value和done结果
           value,每次yield后面值
           done是一个布尔值，代表是否遍历结束
    yield 是否有返回值？
        yield语句本身没有返回值，或者每次返回undefined
    next()可以带参数？
        给上一个yield值
    for...of循环：循环generator函数
    generator函数放到对象里面：
        var json={
            *fn(){
                yield 'a';
                yield 'b';
                return 'c';
            }
        }
        var res=json.fn();
        console.log(res.next());       
    

