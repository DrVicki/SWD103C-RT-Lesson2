# SWD103C-RT-Lesson2

React is a library (not framework).It’s lightweight and easy to combine with other libraries or join any technical stack. Because it is lightweight, React is easy to learn; it reduces coding time with higher performance. React will help you:     
  - manipulate the DOM     
  - reuse code by implementing components
  - maintain code easily by one-way data flow from JavaScript object to the DOM

## 2.1  Creating React App   

### 2.1.1 Manually Create a React App 

Your first React app can just be an `HTML` file like the `index.html` file below. We create the application with the help of two libraries: `React` and `ReactDOM`.     
  - **React**: core React engine     
  - **ReactDOM**: helps React work with web browsers 
    - Example 1: put the below code into the `index01.html` file and run it in a web browser.
    
```
<!DOCTYPE html> 

<html lang="en"> 

 <head> <meta charset="UTF-8" /> 
  <title>My First React App</title> 

  <script src="https://unpkg.com/react@18/umd/react.development.js"></script> 
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script> 
</head> 

<body> 
  <div id="root"></div> 
    <script> function AppComponent() {
    return React.createElement("div", { className: "title-container" }, [ React.createElement( "h1", { className:         "title" }, "Welcome to my React app!" ), ]); } 

  const root = ReactDOM.createRoot(document.getElementById("root")); 
  root.render(React.createElement(AppComponent)); 

</script> 

</body> 
</html>

```

In example 1, we imported two libraries which are `react.development.js` and `react-dom.development.js` in the `<head>` tag; then wrote React code in the `<script>` tag.  In React, we use “`className`” instead of “class” in HTML code. The above example helps to create this HTML node:

```
<div class="title-container"> 
  <h1 class="title">Welcome to my React app!</h1> 
</div>
```
However, you can see the code to create `rootEle` is not `HTM`L friendly so it’s hard to read and maintain. The Babel library helps developers write `HTML` code inside JavaScript code, called `JSX`. Please try the below example to use this concept. 

Example 2: put the below code into the index02.html file

```
<!DOCTYPE html> 
<html lang="en"> 

<head> <meta charset="UTF-8" /> 
  <title>My First React App</title> 
  <script src="https://unpkg.com/react@18/umd/react.development.js"></script> 
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script> 
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>  
</head> 
  <body> 
  <div id="root"></div> 
  <script type="text/babel"> 
  
  function AppComponent() { 
    return ( <div className="title-container"> 
    <h1 className="title">Welcome to my React app!</h1> </div> );
   
   const root = ReactDOM.createRoot(document.getElementById("root")); 
   root.render(<AppComponent />); 
 </script> 
 </body> 
</html>

```













