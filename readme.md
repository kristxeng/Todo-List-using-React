# 使用 React 做的 Todo List  
將 jQuery 做的 Todo List 改用 React 實現  

**使用 webpack 作為主要建置工具**  
React 主要透過 JavaScript 渲染整個網頁，因此 index.html 只剩下 `<div id="root"></div>` 讓 React 可以掛載元件。建置工具使用 webpack 打包成 bundle.js。  

**用 callback function 的方式讓子元件可以修改父元件的 state**  
這個 Todo List 只簡單分成兩個 Component：`<TodoList />` 和 `<TodoItem />`，而待辦事項的資料都存在 `<TodoList />` 的 state 中，`<TodoList />` 用 props 把資料內容傳遞給 `<TodoItem />` 顯示。也因為資料是存在父元件的 state，`<TodoItem />` 並沒有辦法直接做刪除或是標示已完成，所以將父元件(即`<TodoList />`)內的 Method 當作 porps 傳遞給 `<TodoItem />` 當作 callback function，來達到子元件可以更改父元件的 state 值。  

**元件內的 Method 要綁定 this**  
因為 JavaScript 的特性，在 Component 裡面的 Method 都要 在 constructor 內加上 `this.methodName = this.methodName.bind(this)` 以避免 this 沒有指向這個 Component。  

**連結後端資料庫**  
如果之後串後端資料庫，會是在 `<TodoList />` 的 `componentDidMount()` 中發送AJAX 向資料庫拿到資料後，在用 props 傳遞給 `<TodoItem />` 顯示。  