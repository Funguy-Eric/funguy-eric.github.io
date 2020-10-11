## JS Study Note

### 数组元素的相关操作

1. 增

   * `push`方法：从尾部加

     ```javascript
     let hero=['亚瑟','干将莫邪','露娜'];
     
     //在尾部增加一个元素
     hero.push('赵云');
     console.log(hero); //'亚瑟','干将莫邪','露娜','赵云'
     
     //在尾部增加多个元素
     hero.push('孙悟空','上官婉儿');
     console.log(hero); //'亚瑟','干将莫邪','露娜','赵云','孙悟空','上官婉儿'
     ```

   * `unshift`方法：从头部加

     > 与push方法操作类似，只是改成了加在数组最前面

2. 删

   * `pop`方法：从后往前删除

   * `shift`方法：从前往后删除

     ```js
     let hero=['亚瑟','干将莫邪','露娜','赵云'];
     
     hero.pop();
     console.log(hero); //'亚瑟','干将莫邪','露娜'
     
     hero.shift();
     console.log(hero); //'干将莫邪','露娜'
     ```

   * `splice`方法：用作删除时，splice方法有一个参数或两个参数

     ```js
     let hero=['亚瑟','干将莫邪','露娜','赵云','孙悟空','上官婉儿'];
     
     //一个参数：表示删除从指定位置开始到结束位置的所有元素,并返回被删除的元素
     let deleteHero=hero.splice(4);
     console.log(hero); //'亚瑟','干将莫邪','露娜','赵云'
     console.log(deleteHero); //'孙悟空','上官婉儿'
     
     //两个参数：表示删除从下标1开始，往后数2个元素
     let deleteHero2=hero.splice(1,2);
     console.log(hero); //'亚瑟','赵云'
     console.log(deleteHero2); //'干将莫邪','露娜'
     ```

3. 改

   `splice`方法：用作修改时，splice方法有三个参数

   ```js
   let hero=['亚瑟','干将莫邪','露娜','赵云'];
   
   //从下标1开始，往后走0个步长，用'关羽'替换这0个步长里的内容
   //实际作用相当于在下标1和2之间添加了'关羽'这个元素
   hero.splice(1,0,'关羽');
   console.log(hero); //'亚瑟','干将莫邪','关羽'，'露娜','赵云'
   
   //从下标1开始，往后走1个步长，用'鲁班'替换这1个步长里的内容
   hero.splice(1,1,'鲁班');
   console.log(hero); //'亚瑟','鲁班','关羽'，'露娜','赵云'
   
   //从下标1开始，往后走2个步长，用'安琪拉'替换这2个步长里的内容
   hero.splice(1,2,'安琪拉');
   console.log(hero); //'亚瑟','安琪拉'，'露娜','赵云'
   ```

4. 查

   `indexOf`方法：常用的是一个参数的形式

   ```js
   let hero=['亚瑟','干将莫邪','露娜','赵云'];
   
   let result1=hero.indexOf('干将莫邪'); //1 返回下标
   let result2=her0.indexOf('达摩');  //-1 不存在返回-1
   ```



### 循环

1. `for...in...`和`for...of...`

   * `for...in...`

     ```js
     let hero=['亚瑟','干将莫邪','露娜','赵云'];
     
     //i指的是数组每一项的下标
     for(let i in hero){
       console.log(hero[i]);
     }
     //输出：
     //亚瑟
     //干将莫邪
     //露娜
     //赵云
     ```

   * `for...of...`

     ```js
     let hero=['亚瑟','干将莫邪','露娜','赵云'];
     
     //i指的是数组的每一项
     for(let i of hero){
       console.log(i);
     }
     //输出：
     //亚瑟
     //干将莫邪
     //露娜
     //赵云
     ```

2. `break` /  `continue`

   break：跳出循环

   continue：跳出循环中的一次迭代



### 函数

1. 函数的声明

   ```js
   //1.function命令声明
   function code() {
       console.log("Hi!");
   }
   
   //2.函数表达式生命（注意结束的分号）
   let code = function() {
       console.log("Hi!");
   };
   
   //第二种方法可写为
   let code = () => {
       console.log("Hi!");
   };
   ```

2. 计时器

   * `setTimeout()`的三种形式

     ```js
     /**
     
      * 第一个参数是代码，注意代码需用引号包裹，否则会立即执行代码
      * 第二个参数是 1000，即 1000ms 后执行 console.log(2)
        */
        setTimeout('console.log(2)', 1000);
     
     /**
     
      * 第一个参数是匿名函数
      * 第二个参数是 2000，即 2s 后执行 console.log(3)
        */
        setTimeout(function () {
          console.log(3);
        }, 2000);
     
     // 第一个参数是函数名，注意函数名后不要加小括号“()”，否则会立即执行 print4
     setTimeout(print4, 3000);
     
     console.log(5);
     
     function print4() {
       console.log(4);
     }
     ```

     运行结果：依次输出1，5，2，3，4

   * 无限调用：`setInterval()`

     一个60秒的计时器：

     ```js
     let i = 60;
     print();
     let timer = setInterval(print, 1000);
     
     function print() {
       console.log(i);
       i--;
       if (i < 1) {
         clearInterval(timer);
       }
     }
     ```

     > setInterval中函数print第一次执行在1s后，所以需在此前先调用一次print()



### 对象

