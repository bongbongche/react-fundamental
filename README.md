# React Fundamental

### ES6 grammar

- __Arrow function__  
  
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

- __Template literals__

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
  Inside of ``, ${} can contain variable.  