# React Fundamental

### ES6 grammar

- **Arrow function**

  Before es6, function looks like this

  ```
  function sayHello(name){
      return "Hello " + name
  }

  const hyun = sayHello("Hyun")

  console.log(hyun)
  ```

  Result is Hello Hyun. 'return' is needed to hava a result.  
  In case of this, if i don't give parameter, like "Hyun", result is Hello undifined.  
  So i can set default value of name.

  ```
  function sayHello(name = "Hyun"){
      return "Hello " + name
  }
  ```

  It's not a es6 thing. And it can be used in es6.

  In es6, function looks like this

  ```
  const sayHello = name => "Hello " + name

  const hyun = sayHello("Hyun")

  console.log(hyun)
  ```

  Result is Hello Hyun. 'return' isn't needed to hava a result.  
  without {}, arrow function imply 'return'

- **Template literals**

  Template literals is useful to handle templates, variables, strings.

  Before,

  ```
    const sayHello = name => "Hello " + name
  ```

  After,

  ```
      const sayHello = name => `Hello ${name}`
  ```

  It uses backticks. not '', not "".  
  Inside of ``, \${} can contain variable.

- **Object Destructuring**

  ```
  const human = {
    name: "Hyun",
    lastName: "Che",
    nationality: "Korean",
    favFood: {
      breakfast: "Milk",
      lunch: "Egg",
      dinner: "Water"
    }
  }
  ```

  Before destructing,

  ```
  const name: human.name;
  const lastName: human.lastName;
  ```

  After destruction,

  ```
  const { name, lastName, nationality: whatever, favFood: { lunch } } = human;
  ```

  'nationality: whatever' part changes variables name. nationality to whatever  
  'favFood: { lunch }' part can go deep inside object.

- **Spread operator**

  Spread operator can be applied both array and object.  
  It gives us item inside of array and object. Just item. Not shell.

  There are arrays of days.

  ```
  const days = ["Mon", "Tue"];
  const otherDays = ["Thu", "Fri"];
  ```

  If I want all days,

  ```
  const allDays = days + otherDays;

  result is Mon,Tue,Thu,Fri
  ```

  Instead items of arrays, It gives a string.

  ```
  const allDays = [days + otherDays];

  result is ["Mon,Tue,Thu,Fri"]
  ```

  Result is an array. But it has only one item.

  ```
  const allDays = [days, otherDays];

  result is [Array[2], Array[2]]
  ```

  Result is an array. But it has two array.

  Spread operator looks like this.

  ```
  const allDays = [...days, ...otherDays];

  result is ["Mon", "Tue", "Thu", "Fri"]
  ```

  '...' can unpack array or object.

  ```
  const ob = {
    first: "hi"
  };

  const ab = {
    second: "hello"
  };

  const two = {...ob, ...ab};

  result is { first: "hi", second: "hello"}
  ```
