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
However, you can see the code to create `rootEle` is not `HTML` friendly so it’s hard to read and maintain. The Babel library helps developers write `HTML` code inside JavaScript code, called `JSX`. Please try the below example to use this concept. 

Example 2: put the below code into the `index02.html` file

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
In example 2, we imported `babel.min.js`, a library to help us write the `JSX` code (HTML inside JavaScript code). It's much easier using Babel. 
  - However, in reality, we do not create a React application this way. We’ll use the `npx` tool demonstrated in the next section.

### 2.1.2   Create a React App Using npx Tool 

Run this command to create a new single-page application in React. 
```
npx create-react-app your-app-name
```
What does the `npx` do? It downloads the latest version of the `create-react-app` tool and then immediately executes it with the argument `your-app-name`. When finished, `npx` will delete the `create-react-app` tool so that it won’t pollute your development environment. Let’s create your first React app!     

  - Open your Command Prompt on Windows or Terminal on other operating systems.
  - Go to a folder where your project code will be stored. For example, I choose the “/react-projects” folder.
  - Run the below command. 
    - `npx create-react-app cool-blog`  
  - `npx` will create a new folder (named “`cool-blog`”) inside the “`/react-projects`” folder, and create all initial files for your React app inside it.     
  - Go inside the project folder by running the command below. 
   -   `cd cool-blog`       
  -  Start your React app using this command. 
   - `npm start`   
    -Commands like “`npm start`”,“`npm run` ...” or “`npm install` ...” are executed in terminals at the project folder (e.g., “`/react-projects/cool-blog”`). 
    
As you can see in the terminal, it actually invokes the `react-scripts` tool. It will compile the code and then start a web server so you can try your website at the local address which often is http://localhost:3000. Currently, we can see only a simple web page since we haven’t written any code yet.

## 2.2  Examine Your React Project 

After creating a React app using `npx`, we can go to the project folder and check its content. Let’s examine your project. Open the project with VS Code by running the command below. 

```code .
```
### 2.2.1   The package.json File 

Open the `package.json` file at the root folder and check the dependencies in the file. 

```
"dependencies": { 
"@testing-library/jest-dom": "^5.16.4", 
"@testing-library/react": "^13.2.0", 
"@testing-library/user-event": "^13.5.0", 
"react": "^18.1.0", 
"react-dom": "^18.1.0", 
"react-scripts": "5.0.1", 
"web-vitals": "^2.1.4" } W
```
We can see the minimum packages required in a React application and also get important information. It is the React version that we use in the “`cool-blog`” project. At the time I wrote this, the React version was 18.1.0.


### 2.2.2   The index.js File 

Check the `index.js` file in the “`/src`” folder. Below is content of the file after removing redundant code.

/src/index.js 
```
import React from 'react'; 
import ReactDOM from 'react-dom/client'; 
import './index.css'; 
import App from './App'; 

const root = ReactDOM.createRoot(document.getElementById('root')); 
root.render( <React.StrictMode> <App /> </React.StrictMode> ); 
```

At the beginning of the file, we import `React` and `ReactDOM`. `React` is the core engine of the application and   `ReactDOM` is specifying that the engine will be directed to a web application. These two libraries are combined to help us build a web application in React.

`React.StrictMode` will notify us if we use deprecated code because the project is using a newer version of React. 
  - However, the Strict Mode will run more code and produce more console logs in the development environment. 
  - This behavior confuses and annoys the developer while debugging the code.  
  - Sometimes we can comment out the `React.StrictMode` code in the `index.js` file to get accurate logs on the console. When you're done debugging, be sure to uncomment it! 
  
The `render()` method will render the `App` component inside the `<div>` tag which has the “`root`” `id` in the “`/public/index.html`” file; that is the below element. 
```
<div id="root"></div>
```

### 2.2.3   The App.js File 

The `App.js` file in the “`/src`” folder defines the `App` component which was rendered inside the `<div id="root"></div>` tag in the “`/public/index.html`” file. We can change some text in the code, then save the file. Your change will be automatically built and reflected on the local web page. You could try the below code. 

Example: 

/src/App.js 

```
import './App.css'; 
function App() 

{ return ( <div className="App"> <h1>My First React App</h1> </div> ); } 
export default App;
```

## 2.3    JSX 

`JSX` is just a syntax extension of JavaScript which allows you to write HTML inside your JavaScript code. Let’s change the `App.js` file a little bit to have the first view of `JSX` code. Replace my name with yours and save the file. See your name on the web page? Cool! 

Example: 

/src/App.js 
```
import './App.css'; 
function App() 

{ const name = 'Neo'; 
return ( <div className="App"> 
<h1>Dr. Vicki's First React App</h1> 
<p>Hello {name}</p> 
</div> ); } 
export default App; 
```
The constant variable “name” can be accessed in the HTML code easily with the {name} syntax and whole HTML code was written in the App() function. That is JSX code.

 






