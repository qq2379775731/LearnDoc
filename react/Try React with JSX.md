### 标题

在项目中使用JSX	

------

### 时间

2019-8-19

------

### 内容

#### 1.Quickly Try JSX

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

<script type="text/babel">
	//...
</script>
```

####2.Add JSX to a Project

需先安装node.js

1. **Step 1:** Run `npm init -y` 

2. **Step 2:** Run `npm install babel-cli@6 babel-preset-react-app@3`

3. **Step 3**: Run JSX Preprocessor

   Create a folder called `src` and run this terminal command:

4. ```shell
   npx babel --watch src --out-dir . --presets react-app/prod 
   ```

------

### 注释

主要是使用的babel[^babel]来对JSX语法进行解析编译

------

### 获取路径

https://reactjs.org/docs/add-react-to-a-website.html

------

### 其他

[^babel]: https://babeljs.io/docs/en/

------

