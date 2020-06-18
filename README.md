# React Fundamental

### **ES6 grammar**

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

- **Class**

  Class concept is came from object-oriented-programming.  
  It's like blueprint.

  ```
  class Human {
    constructor(name, lastName){
      this.first = name;
      this.last = lastName;
    }
  }
  ```

  Thanks to constructor, we can give Human some arguments which is name, lastName.
  'this' means 'class Human'

  ```
  const hyun = new Human('first', 'last')
  ```

  hyun.first is 'first', hyun.last is 'last'.

  Class can extend.

  ```
  class Baby extends Human {
    cry(){
      console.log("Yeaaaaaaaaah")
    }
    sayName(){
      console.log(`My name is ${this.first}`)
    }
  }

    const myBaby = new Baby('mini', 'me')

    console.log(myBaby.sayName())
  ```

  result is 'My name is mini'.  
  Extended from Human, So class Baby can have class Human's thing.

### **React**

- **React router**

  ```
  npm i react-router-dom
  ```

  - **What is React router**

    React router is component nesting. And route is component.

  - **When to use**

    Use when i have to tell App where to start and where to go.
    For example, go "/", go "/Tv", go "/Detail", etc.

  - **How to use**

    ```
    import React from "react";
    import { HashRouter as Router, Route } from "react-router-dom";
    import Home from "Routes/Home";
    import Tv from "Routes/Tv";
    import Search from "Routes/Search";

    export default () => (
      <Router>
        <Route path="/" exact component={Home} />
        <Route path="/tv" component={Tv} />
        <Route path="/search" component={Search} />
      </Router>
    );
    ```

    Path is a information that sets url.  
    Exact means It will be displayed when url is exactly same with path = "/".  
    If i don't use exact, Home, Tv, Search is displayed together.  
    Because "/tv", "/search" also have "/". It's called composition.  
    And Route cannot be used outside of Router

  - **Redirect**

    'Redirect' renders a new location.

    ```
    <Router>
      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/tv" component={Tv} />
        <Route path="/tv/popular" render={() => <h1>Popular</h1>} />
        <Route path="/search" component={Search} />
        <Redirect from="*" to="/" />
      </Switch>
    </Router>
    ```

    From "\*", to "/". So some bullshit url, for example, "/ajdfjae", will be redirected to "/".  
    But when you use 'from', You have to use 'Switch'.  
    'Switch' will do that route will be rendered only one.  
    So "/tv/popular" shows only "/tv".

- **Styled component**

  ```
  npm i styled-component
  ```

  - **What is styled-component**

    Styled-component can manage css inside of component.  
    Sc makes component that has a style.

    ```
    import styled from "styled-components";

    const Header = styled.header``;

    const List = styled.ul`
      display: flex;
      &:hover {
        background-color: pink;
      }
    `;

    const Item = styled.li``;

    const Slink = styled(Link)``;

    export default () => (
      <Header>
        <List>
          <Item>
            <Slink to="/">Movies</Slink>
          </Item>
          <Item>
            <Slink to="/tv">Tv</Slink>
          </Item>
          <Item>
            <Slink to="/search">Search</Slink>
          </Item>
        </List>
      </Header>
    );

    ```

  - **How to use**

    First, Just give it a name. The name can be anything.

    ```
    const List
    ```

    Second, Use styled-component and select tag name.  
    Not like a css, Sc uses backticks(``).

    ```
    const List = styled.ul``
    ```

    Third, Use just like a css.

    ```
    const List = styled.ul`
      display: flex;
      &:hover {
        background-color: pink;
      }
    `;
    ```

    If I want to use components which is not a sc, I can do this.

    ```
    import { Link } from "react-router-dom";

    const Slink = styled(Link)``;
    ```

    Now Link that coming from "react-router-dom" can be used  
    as a sc.
