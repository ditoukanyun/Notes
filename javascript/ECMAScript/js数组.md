

## pop()
- pop()方法会从数组中删除最后一个元素,并返回最后一个元素.
```javascript
    const arrs = [1,2,3,4,5]
    const res = arrs.pop()
    console.log(res)   // 5
```

## push()
- push()方法允许你向数组中添加一个或多个元素
- push()会返回新增数组后新的长度
```javascript
    const arrs = [1,2,3,4,5]
    let res = arrs.push(888);
    console.log(arrs) // [1, 2, 3, 4, 5, 888]
    console.log(res)  // 6 得到新的数组长度
```

## shift()
- shift()方法会删除数组的第一个元素并返回它
```javascript
    const arrs = [1,2,3,4,5]
    const res = arrs.shift()
    console.log(res)   // 1
```

## unshift()
- unshift()方法允许向数组的开头添加一个或多个元素
- 会将新增后的数组长度返回
 ```javascript
    const arrs = [1,2,3,4,5]
    let res = arrs.unshift(888);
    console.log(arrs) // [888, 1, 2, 3, 4, 5]
    console.log(res)  // 6 得到新的数组长度
```

## 清空数组的几种方式
- 1.如何清空数组
```javascript
    let arr = [1,2,3,4,5];
    // 清空数组的三个方法；
    // 第一种：直接将空数组赋值给数组
    arr = [];
    // 设置数组的长度为0
    arr.length = 0;
    // 利用splice
    arr.splice(0, arr.length);
    console.log(arr);
```



## includes()
- includes作用就是判断元素元素是否在数组中,
  - 如果数组中有这个元素就返回true,否则返回的是false
```javascript
    const arrs = [1,2,3,4,5]
    // const hasParam = arrs.includes(2)   // true
    const hasParam = arrs.includes('2')  // false
    console.log(hasParam)
```

## concat()
- 数组与数组间的拼接不可以使用+加号进行拼接，如果使用加号进行拼接会将数组转换成字符串进行拼接
- 使用concat()方法可以将两个或多个数据组合起来,返回一个新的数组
- 注意点：不会修改原有的数组；
- 该方法的代替方式可以使用ES6的解构来实现
```javascript
    const arr1 = [1,3]
    const arr2 = [2,4]
    const arr3 = [5,6]
    // + 加号拼接数组
    const str = arr1 + arr2;
    console.log(str);  // 1,32,4
    console.log(typeof str); // string

    // const res = arr1.concat(arr2)
    // console.log(res);  //[1, 3, 2, 4]
    const res = arr1.concat(arr2,arr3)
    console.log(res);  // [1, 3, 2, 4, 5, 6]

    // 补充： 可以使用扩展运算符来拼接数组
    // 解构数组中会将解构出来的元素放在新的数组中，返回给我们
    let res1 = [...arr1, ...arr2, ...arr3];
    console.log(res1);  //  [1, 3, 2, 4, 5, 6]
    console.log(typeof res1) // obj

    // 自定义函数合并任意多个数组
    function concatAll(arr, ...arrays){
        return arr.concat(...arrays)
    }
    console.log(concatAll(arr1,arr2,arr3));  // [1, 3, 2, 4, 5, 6]
```

## forEach()
- 当你想要对一个数组进行遍历操作时，可以使用forEach()方法，它接受一个函数作为参数。事实上它本身接受三个参数：(当前值,索引,数组)

```javascript
    const arrs = [1,2,3,4,5]
    arrs.forEach(console.log)  // 当前值  索引 和数组
    arrs.forEach((value,index,arr)=>{
        console.log(value);
        console.log(index);
        console.log(arr);

    })

```

## indexOf()  
- indexOf(检索值，开始查找的位置)
- indexOf作用: 返回数组中给定元素的第一个索引值. indexOf()也被用于检查元素是否存在某一个元素
- indexOf()方法从左到右开始查到，找到元素就停止查找
- 注意点： 找到元素就会返回元素的对应位置，没有找到元素就返回-1

```javascript
    let arrs = [1,2,3,4,5,3]
    let index = arrs.indexOf(3);
    console.log(index);  // 2
    index = arrs.indexOf(3,4);
    console.log(index)  // 5
     
```
## lastIndexOf()
- 该方法和indexOf()方法使用和传参一样，但是查找方式是从右到左开始查找


## find()
- find()方法就是会查找数组中的元素,
- find()方法找到了就会返回找到的元素，如果找不到就返回undefined
- find()和filter()相似,但是find()函数找到一个匹配值就会停止查找,而filter会继续查找
```javascript
    const arrs = [1,2,3,4,5,4,3,2,1]
    const res = arrs.find(arr=> arr == 5)
    console.log(res)  // 5

    const obj = [
        {
            name: 'zs',
            age:12
        },
        {
            name: 'ww',
            age:33
        },
        {
            name: 'zs',
            age:16
        },
        {
            name: 'll',
            age:14
        },
    ]
    const res1 = obj.find(obj=> obj.name == 'zs')
    console.log(res1)  // {name: "zs", age: 12}

```
- 如果是过滤整个数组那么采用filter,搜索数组中唯一元素时,则使用find()

## findIndex()
- 它和find()方法相同,只是他返回的是找到第一个元素的索引值,而不是元素

```javascript
    const obj = [
        {
            name: 'zs',
            age:12
        },
        {
            name: 'ww',
            age:33
        },
        {
            name: 'zs',
            age:16
        },
        {
            name: 'll',
            age:14
        },
    ]
    const res2 = obj.findIndex(obj=> obj.name == 'ww')
    console.log(res2)  // 2

```
- 你可能会认为findIndex()和indexOf()是相同的。事实上他们还是有所差异的。indexOf()的第一个参数是一个原始值（Boolean、Number、String、Null、Undefined或Symbol），而findIndex()的第一个参数是一个回调函数。

- 因此，当你需要搜索原始值数组中元素的索引时，可以使用indexOf()。如果你有更复杂的元素，如对象，那得使用findIndex()。


## slice()
- slice方法可以帮助我们提取数组的一部分
- 返回一个新的数组，不会修改原数组
- slice方法是包含开始索引不包含结束索引 [开始索引，结束索引)
```javascript
    let arr = [1,2,3,4,5];
    let res = arr.slice(1,3);
    console.log(res); // [2, 3]
    console.log(arr); // [1, 2, 3, 4, 5]
```

## splice()
- splice()通常用于添加或删除某个所引出的元素.
- splice(开始位置（必需），删除数量（必需），item1,...item2(可选添加的项))
```javascript

let arr = [1,2,3,4,5];
// arr.splice(1,3);
// console.log(arr) // [1, 5]

arr.splice(1,3,111,2222);
console.log(arr) // [1, 111, 2222, 5]

```
  

## some()
- some方法:检测数组中至少有一个元素通过了测试
- some()方法将回调函数作为唯一的参数
- 如果至少有一个元素通过测试，则返回true，否则返回false。

## every()
- every()和some()类似,不同的是some()只要有一个元素符合条件就返回true,而every是所有元素都满足条件才返回true

## toString()
- 将数组转换成字符串
  ```javascript
     let arr = [1,2,3,4,5];
     let str = arr.toString();
     console.log(str)  // 1,2,3,4,5
     console.log(typeof str) // string
  ```


## join()
- join()方法没有传递参数，调用toString()方法
- join()方法可以传递参数，把参数作为元素间的连接符号
```javascript
    let arr = [1,2,3,4,5];
    let str = arr.join("-");
    console.log(str)  // 1-2-3-4-5
    console.log(typeof str) // string

```

## isArray()
- isArray()方法判断传递的值是否为数组,是数组返回true,否则返回false
  
## sort()
- sort()方法会对数组中的元素进行排序.
- 默认的排序方法将所有元素转换为字符串,并按字母的顺序排序

```javascript
    const fruits = ['banana', 'apple','orange','pear']
    fruits.sort()
    console.log(fruits)  // ["apple", "banana", "orange", "pear"] 默认按字母的顺序
```
- 但是对于数字
  ```javascript
    const nums = [3,72,33,42,5,8]
    nums.sort()
    console.log(nums)  // [3, 33, 42, 5, 72, 8]

  ```
- 对于数字,sort()接受了一个比较函数,并传递两个参数
- 参数分别为a,b;然后对这两个元素进行比较,并且返回一个数字
- 返回规则:
  - 如果返回的值是一个负数,则表示a排在b之前（升序）
  - 如果返回的值是一个正数,则表示a排在b之后（降序）
  - 如果返回的值是0,则没有变化

```javascript
    const nums = [3,72,33,42,5,8]
    nums.sort((a,b)=> a-b)
    console.log(nums)  // [3, 5, 8, 33, 42, 72] 升序
    nums.sort((a,b)=> b-a)
    console.log(nums) // [72, 42, 33, 8, 5, 3] 降序
```
  
## reverse()
- reverse()方法就是将数组反转
- 注意点： 该方法会修改原有的数组
```javascript
    const nums = [3,72,33,42,5,8]
    nums.reverse()
    console.log(nums) // [8, 5, 42, 33, 72, 3]

```




## map()
- map作用:修改数组的元素
- map()方法会创建一个新数组,其结果是该数据中的每个元素都调用一个提供的函数后返回的结果

```javascript
    //map使用
    const nums = [1,2,3,4]
    返回的结果 =  map(函数)
    const res = nums.map(n => n+1);
    console.log(nums);  // [1, 2, 3, 4]
    console.log(res);  // [2, 3, 4, 5]  会创建新数组

    // map可以保留对象的一个特定属性
    const obj = [
        {
            name: 'zs',
            age:12
        },
        {
            name: 'ww',
            age:33
        }
    ]
    const allName = obj.map(obj => obj.name);
    console.log(allName) // ["zs","ww"]


    // 自定义的map功能
    // myMap(数组,回调函数)
    function myMap (collection,callback){
        var iterationInputs = [];
        for(var i = 0 ; i<collection.length; i++){
            iterationInputs.push(callback(collection[i]))
        }
        return iterationInputs
    }

    const res1 =  myMap(nums,n=>n+1)
    console.log(res1)

```

## filter()
- filter作用: 过滤数组,它接受一个函数作为唯一的参数,
    - 该参数在数组的每个元素上调用,这个函数必须返回一个布尔值
    - true: 元素奖保留在数组中
    - false: 元素不会保留在数组中
    - 最终返回结果也会得到一个新数组,该数组中保留了条件为true下的元素
    - 返回数组中的偶数

```javascript
    const nums = [1,2,3,4,5,6,7,8]
    const filterNums = nums.filter( n => n%2 == 0)
    console.log(nums) // [1, 2, 3, 4, 5, 6, 7, 8]
    console.log(filterNums)// [2, 4, 6, 8]

    const objArrs = [
        {
            name: 'zs',
            age:12
        },
        {
            name: 'ww',
            age:33
        },
        {
            name: 'll',
            age:22
        }
    ]
    // 移除数组中的特定某项
    function removeObj(objArrs,name){
        return objArrs.filter(obj => obj.name !== name)
    }
    console.log(removeObj(objArrs,'zs'))

    // 自定义filter()
    function myFilter(collection,callback){
        var filterArr = [];
        for (var i = 0; i< collection.length; i++){
            if(callback(collection[i])){
                filterArr.push(collection[i])
            }
        }
        return filterArr
    }

    const res = myFilter(objArrs,obj => obj.name !== 'ww')
    console.log(res);
```


