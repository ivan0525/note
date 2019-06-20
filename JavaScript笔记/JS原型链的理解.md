## 一、原型链
-  **先来看看构造函数、原型和实例的关系**
 1. 在JavaScript中，所有的函数都有 `prototype` （显式原型）属性，这个属性指向一个对象，即原型对象。
 2. 原型对象中又包含一个指针（就是constructor），它指向原型对象所属的构造函数。
 3. 每个实例对象都有一个`__proto__`  **（隐式原型，这个属性官方定义为：`[[prototype]]`）** 属性，这个属性指向构造函数的原型对象。来看下代码，解释我所说的几点：

```
function Person(){
	this.name = [];
	this.say = function() {
	console.log(this.name);
	}
}
var jack = new Person();  // 创建一个Person实例
jack.name.push('jack');
console.log(jack.name);
jack.say();
console.log(Person.prototype.constructor === Person);   // true
// 实例对象的 constructor 属性是从构造函数的原型对象中继承过来的。
console.log(jack.constructor === Person);    // true
console.log(jack.__proto__ === Person.prototype)    // true
``` 
- 弄清楚构造函数、原型和实例的关系之后，我们进入正题：**原型链**  



原型链说白了就是实例对象和原型对象之间实现属性共享和继承的纽带吧，环环相扣像链条一样。

来看下代码
```
function Grand() {
			this.name = "grandpa";
		}
		Grand.prototype.sayName = function() {
			console.log(this.name);
		}
		Grand.prototype.hobby = function() {
			console.log("play chess");
		}

		function Father() {
			this.name = "father";
		}
		Father.prototype = new Grand();
		Father.prototype.hobby = function() {
			console.log("programme");
		}
		function Son() {
			this.name = "son";
		}
		Son.prototype = new Father();
		Son.prototype.hobby = function() {
			console.log("王者荣耀");
		}
		var grand = new Grand();
		var father = new Father();
		var son = new Son();

		grand.sayName();  // grandpa
		grand.hobby();  // play chess

		father.sayName();  // father
		father.hobby();  // programme

		son.sayName();   // son
		son.hobby();   // 王者荣耀
```



**我来解释下上述代码：**
首先，有三个构造函数，Grand，Father和Son.我们让 `Father.prototype = new Grand();` 来实现Father对Grand的继承，通过 `Son.prototype = new Father();` 来实现Son对Father的继承。这样Father 和 Son的实例就能够访问到Grand原型上的方法。
访问hobby方法的过程：

- 在实例对象father和son中都有一个 `__proto__`属性，这个属性指向各自的构造函数的原型对象。当我们通过`son.hobby()` 来访问hobby这个方法时，它首先会在自己身上找，看有没有这个方法，没有就进行下一步：

- 在`Son.prototype`  上面找，看有没有hobby这个方法，结果找到了，就可以调用该方法。

这里我们是重写了Grand原型对象中的hobby方法，当我们没有从写该方法时过程就是这样的：

**总结以下属性寻找规则：**

1. 在访问某个对象的某个属性的时候，会首先在自己身上找是否存在该属性；
2. 如果在对象身上没有该属性，就会到该对象构造函数的原型对象上去找；
3. 如果原型对像上还没有，就到原型对象的原型上去找;
4. 一直找到Object的原型对象的原型，即`Object.prototype.__proto__ = null` 为止。