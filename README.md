## function ##
    什么是函数：
    函数：封装一项专门任务的步骤清单的代码段，起一个名字。（**程序中提供的一项服务的步骤说明**）
     何时使用函数？当一项任务需要反复执行，但又不希望重复编写时。（**代码重用！**）
     如何声明函数：function 任务名([参数变量列表]){
    			步骤清单代码段
                            [return 返回值]
                      }
  

         ***函数名(任务名): 指向函数定义的一个变量
                          函数：封装函数定义的引用类型对象
                ***声明时，不执行！也不读取内部的代码!
            如何调用函数执行：任何位置: 函数名([参数值列表]);
                ***调用时，才读取内部的代码，执行
                
     参数变量：专门接收要传入方法中处理的数据的变量。
      何时需要定义参数：如果一个函数，必须一些数据才可正常执行，需要几个数据，就定义几个参数变量。
      何时如何为参数变量赋值：在调用函数时，按照参数定义时的顺序和个数，依次传入参数值。
      
        返回值：函数的执行结果
                何时需要返回值：只要函数需要有明确的执行结果时
                             如果调用者需要获得明确的执行结果时
                如何定义返回值: 函数定义内部，一般函数体结尾
                                return 值;
                调用者何时如何获得返回值:
                        1. 一个有返回值的函数调用，可以当做一个值使用
                        2. 调用时，可使用变量保存住函数调用的返回值
    
    function buy(what,moeny){
        console.log("Step1:取盒饭");
        console.log("Step2:去食堂");
        console.log("Step3:打饭"+what);
        moeny-=3;
        console.log("Step4:扣款3元,余额:"+moeny);
        console.log("Step5:回宿舍");
        return "香喷喷的"+what;
       }
       console.log(buy("宫保鸡丁",10)); 
    
   
    
    ***变量作用域：一个变量的可用范围
        有2种：1. 全局作用域：window
    	      全局变量——放在全局作用域(window)中的变量
              可在程序的任何位置访问全局变量
             2. 局部作用域：在函数调用时才创建的作用域
                  局部变量:2种：1. 参数变量
                              2. 在函数定义中var的变量
                  ***仅在函数调用时，动态创建
                     调用时，如果局部有，就不用全局的！
                  ***调用后，随局部作用域一同销毁
    
    var kl=10;
       function rose(){
        var kl=5;
        kl--;
        console.log(kl);
       }
       function jack() {
        kl--;
        console.log(kl);
       }
       console.log(kl);//全局kl=10
       rose();//4
       console.log(kl);//全局kl=10
       jack();//9
       console.log(kl);//全局kl=9
    

## 声明提前 ##
      声明提前：正式开始执行程序前，先将var声明的变量和function声明的函数，提前到*当前作用域*顶部，集中声明，赋值留在原地。
  


var n=100;
			function fun(){
				var n;//undifend
				console.log(n);
				n=99;
				console.log(n);
			}
			fun();//99
			console.log(n);

按值传递：两变量间赋值，或将变量作为函数的参数传递时都仅将变量中的值，复制一个副本给对方！


var n=100;
			var m=n;
			n++;
			console.log(m);//100

全局函数：ES标准中规定的，由浏览器厂商实现的，不需要任何对象前缀就可直接访问的函数.
     比如：parseInt/Float(str)，isNaN(n)

     比如：alert() prompt()——BOM
## 分支结构 ##
分支结构：
    程序结构：3种：
     顺序结构：默认程序都是自上向下逐行顺序执行
     分支结构：根据不同的条件，选择执行不同的操作
             操作的复杂程度
     循环结构：让程序反复执行同一代码段。

    分支结构：3种情况：
    1. 一个条件，一件事：满足条件就执行，(不满足就什么都不做)
    短路逻辑：条件&&(操作1,操作2...)
        何时使用：操作非常简单时
      if结构：如果 满足*条件*, 就执行代码段
              if(条件){
	 	满足条件时，才能执行的代码段
              }

```
var price=parseFloat(prompt("请输入单价"));
			var count=parseFloat(prompt("输入数量"));
			var money=parseFloat(prompt("输入收款金额"));
            var total=price*count;
			if(total>=500){
				total*=0.8;
			}
			var change=money-total;
			console.log("应收："+total+";找零"+change);
```

    2. 一个条件，两件事：二选一执行！
             如果 满足*条件*，就执行操作1，否则，执行操作2
          三目运算：条件?操作1:操作2;
            何时使用：操作1和操作2，都非常简单时
             if...else结构：
             if(条件){
    	    满足条件才执行的代码段
             }else{//否则
    	    不满足条件才执行的代码段
             }

```
var price=parseFloat(prompt("请输入单价"));
			var count=parseFloat(prompt("输入数量"));
			var money=parseFloat(prompt("输入收款金额"));
			var total=price*count;
			if(money>=total){
				var change=money-total;
			  console.log("应收："+total+";找零"+change);
			}else{
				var change=total-moeny;
			  console.log("应收："+total+";还差"+change);
			}
```
   3. 多个条件，多件事，多选一执行！(有可能都不执行)
         如果 满足 条件1 就执行 操作1
    否则，如果满足 条件2 就执行 操作2
    ... ...
                      [否则，默认操作]
      三目：条件1?操作1:
            条件2?操作2:
                    ...:
                默认操作——不可省略
      if...else if结构：
           if(条件1){
		满足条件1才执行的操作1;
            }else if(条件2){
		满足条件2才执行的操作2;
            }else if(...){
		...
            }[else{
 		如果以上任何条件都不满足，则执行默认操作
            }]
```
if (score<0||score>100) {
      console.log("无效分数");
     } else if(score>=90){
      console.log("A");
     } else if (score>=80) {
      console.log("B");
     } else if (score>=70) {
      console.log("C");
     }  else {
      console.log("D");
     }
```

  

switch...case结构:
何时使用：当条件都是*全等*比较时,才可用switch结构
  switch(表达式){ //1. 计算表达式的结果
    //用表达式的值和每个case后的值做**全等**比较
    //碰到一个全等的case值，则进入该case开始执行
//并默认以此触发之后所有case的执行
case 值1:
     满足值1才执行的代码段1;
    case 值2:
         满足值2才执行的代码段2;
         ...:
         ... ...
     default:
     如果前边的值都不满足，执行默认代码段
  }

```
 switch(parseInt(prompt("请按键："))){
      case 1:
      console.log("查询进行中.....");
      case 2:
      console.log("取款中......");
      case 3:
      console.log("转账进行中....");
      case 0:
      console.log("欢迎下次再来!");
      default:
      console.lop("无效按键");
     }
```

  break: *中止*当前结构的执行，并跳出结构。
    位置：在每个case之间
  何时可以省略部分break：上下两个case希望执行相同代码时

```
switch(parseInt(prompt("请按键："))){
      case 1:
      console.log("查询进行中.....");
      break;
      case 2:
      case 3:
      console.log("系统维护中....");
      break;
      case 0:
      console.log("欢迎下次再来!");
      break;
      default:
      console.log("无效按键");
     }
```


  
