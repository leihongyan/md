##浅拷贝
	这段代码就是浅拷贝，有时候我们只是想备份数组，但是只是简单让它赋给一个变量，改变其中一个，另外一个就紧跟着改变，但很多时候这不是我们想要的
	var obj = {
        name:'wsscat',
        age:0
    }
    var obj2 = obj;
    obj2['c'] = 5;
    console.log(obj);//Object {name: "wsscat", age: 0, c: 5}
    console.log(obj2);////Object {name: "wsscat", age: 0, c: 5}
##	深拷贝
	var obj = {
        name: 'wsscat',
        age: 0
    }
    var deepCopy = function(source) {
        var result = {};
        for(var key in source) {
            if(typeof source[key] === 'object') {
                result[key] = deepCopy(source[key])
            } else {
                result[key] = source[key]
            }
        }
        return result;
    }

	
	Object.prototype.deepCopy=function(){
    var obj=null;//用于最后返回一个对象，这个对象是深复制的结果
    for(var attr in this){//遍历这个对象的每一个属性
        if(this.hasOwnProperty(attr)){//主要是递归自有属性
            if(typeof (this[attr]==='object')){//如果对象的属性是一个对象，就递归复制它的每一个属性
                if(this[attr]===null){//如果对象为null
                    obj[attr]=null;
                }else if(Object.prototype.toString(this[attr])==='[object Array]'){//如果是个数组
                    obj[attr]=[];
                    for(var i=0;i<this[attr].length;i++){
                        obj[attr].push(this[attr][i].deepCopy());
                    }
                }else{//object
                    obj[attr]=this[attr].deepCopy();
                }
            }else{
                obj[attr]=this[attr];
            }
        }
    }
    return obj;
	}