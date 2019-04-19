## ES6中解构的简单使用
- 解构是ES6中新增的一种数组赋值方式

```javascript
    //let [a, b] = [1, 3, 5]
    //let [a, b, c] = [1, 3, [2, 4]]
    let [a, b, [c,d]] = [1, 3, [2, 4]]
    console.log(a)
    console.log(b)
    console.log(c)
```

- 解构注意点：
  - 1.在数组解构赋值中，右边的个数和左边可以不一样，输出为undefined
  
    ```bash
        let [a, b, c] = [1];
        console.log(a,b,c); // 1 undefined undefined
    ```

    - 2.在数组解构赋值中，如果右边的个数和左边个数不一样，可以给左边指定默认值

      -  利用ES6中新增的扩展运算符 ... 
    ```javascript
        let [a, ...b] = [1, 3, 5];
        console.log(a,b) // 1, [3, 5]
    ```


## 箭头函数

- 定义:箭头函数是ES6中新增的一种定义函数的格式

```javascript
    // ES5定义函数
    function 函数名称(形参列表){
        语句;
    }
    let 函数名称= function(形参列表){
        语句;
    }
    // ES6函数写法
    let 函数名称 = (形参列表) =>{
        语句;
    }

````

- 箭头函数注意点
  - 1.箭头函数中,如果只有一个形参,那么()可以省略,没参数圆括号要写
  - 2.箭头函数中,如果{}中只有一句代码,那么{}可以省略,反之,不可以省略
  - 3.只包含一个表达式,可以省略{...}和return
  - 4.包含多条语句,这时候就不能省略{...}和return

    ```javascript

    function say(name){
            console.log("hello"+ name);
        }
    // 一个参数省略()
    let say = name =>{
        console.log("hello"+ name);
    }

    // 一句代码省略{}
    let say = (name) => console.log("hello"+ name);

    // 最终精简
    let say = name => console.log("hello"+name);
    say("Jack");

    // 只有一个语句可以省略return
    const add = (a,b) => a+b; 
    console.log(  add(3,4))  // 7

    // demo
    const isEven = n=> n%2 == 0;
    const res = isEven(5) 
    console.log(res)  // false

    ```
  - 3.箭头函数也支持解构现象
  
    ```javascript
    // demo1
    let sum = (a, ...b)=> {
        console.log(b)
        console.log(a + b)
    }
    sum(1) // 1
    sum(1,2) // 12
    sum(1,2,3)  // 12,3

    // demo2
    let f = ([a, b] = [1, 2], {x: c} = {x: a + b}) => console.log(a + b + c);
    f();  // 6

    ````
