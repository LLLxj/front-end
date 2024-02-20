### this的指向

* 全局上下文：
  #### this指向全局对象（在浏览器中通常是window对象）

  ```javascript
  console.log(this === window); // true
  ```
* 函数中
  * 独立的函数中
    #### this指向全局对象（非严格模式）或undefined（严格模式）
  
    ```javascript
    function globalFunction() {
      console.log(this === window);
    }

    globalFunction(); // true
    ```
  * 在对象方法中
    #### this指向调用该方法的对象
  
    ```javascript
    var obj = {
      method: function() {
        console.log(this === obj);
      }
    };

    obj.method(); // true
    ```
* 构造函数
  #### this指向实例化的对象

  ```javascript
  function Person(name) {
    this.name = name;
  }

  var person1 = new Person('Alice');
  console.log(person1.name); // Alice
  ```
* 箭头函数
  #### this绑定在定义时的作用域，而不是调用时的对象

  ```javascript
  var obj = {
    method: function() {
      setTimeout(() => {
        console.log(this === obj);
      }, 100);
    }
  };

  obj.method(); // true
  ```
  