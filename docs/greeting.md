# Using JavaScript to implement greeting effects in different languages in web pages

## Disclaimer

I simply enjoy programming and am not at a high level most of the time. The article suggests figure a fun, if you have any suggestions, please let me know.

## Introduction

First of all, I was inspired by here: [**CS128**](https://cs128.org) , this is the website of our school's C++ introduction course. Every time I enter the site, the page greets me in a different language with the name of that language.

![Untitled](greeting/Untitled.png)

![Untitled](greeting/Untitled%201.png)

The greeting language also changes with each refresh, which looks very interesting. So I also introduced this effect into my personal website: [**My personal website**](https://www.haozheli.com)

![Untitled](greeting/Untitled%202.png)

![Untitled](greeting/Untitled%203.png)

Today I will describe how to use html as well as JavaScript to achieve this function.

## HTML

In html, the code is very simple. For example, if we want the title to show the greeting and the paragraph below to explain the language of the greeting, we just need to insert the code in html for the title as well as the paragraph.

```html
<h1></h1>
<p></p>
```

where <h1> represents the title and <p> represents the paragraph. We just insert these two tags and don't need to write anything in them, because the JavaScript code afterwards will overwrite what we write now.

## Ideas

First of all the following are my ideas for implementing random greetings.

- First create two arrays of the same length: one with the greetings in different languages, and the other explaining what language the greetings are in. Note: these two arrays need to be the same length

```html
// This is a pseudo code!!!

Array of greetings = ["Hello", "Hello"]
Array of languages = ["Chinese", "English"]
```

- Then we need to create a random number to iterate over the two arrays to achieve a random greeting. Then access the contents of the two arrays by their indexes

```html
// This is still a pseudo code!!!

Random number = a magic algorithm to get a random number within the length of a list

greeting = array of greetings [random number]
language = array of languages [random number]
```

- Finally, we put the greeting and explanation language in the place specified in the previous HTML code

```html
// This is really still pseudo code!!!

Title = greeting + ", nice to meet you"
Explanation = greeting + "in" + language + "in means hello"
```

## JavaScript code implementation

Following the previous idea, we just need to implement the code step by step

- Declare an array

```jsx
var greetings = ["hello", "你好"];
var languages = ["英文", "中文"];
```

- generate a random number

```jsx
var index = Math.floor(Math.random() * greetings.length)
```

The idea of this line of code is to generate a random number and then use it as the index of an array, thus selecting a language greeting from the array.

First, the **`Math.random()`** method returns a random number between 0 (included) and 1 (not included).

Then, we multiply **`greetings.length`** in order to generate a number between 0 and **`greetings.length`**. This means that the randomly generated number can be chosen from 0 to the length of the array (excluding the array length) - 1.

Finally, we use the **`Math.floor`** method to round down the generated number in order to generate an integer, this is because the array index can only be an integer.

So, **`var randomIndex = Math.floor(Math.random() * greetings.length);`** indicates that a random integer is generated as the array index, thus selecting a linguistic greeting from the array **`greetings`**.

- Achieve single element with index

```jsx
var greeting = greetings[index];
var language = languages[index];
```

- Finally, we put the greeting and explanation language in the place specified in the previous HTML code

```jsx
document.querySelector('h1').innerHTML = greeting + ',';
document.querySelector('p').innerHTML = "In " + language + ", " + greeting + " means hello!";
```

The first line of code represents the selection of the first **`<h1>`** tag in the page and modifies its internal HTML content.

First, the **`document.querySelector`** method is used to select the first element on the page that matches the given selector. In this case, the selector is **`"h1"`**, so this method will select the first **`<h1>`** tag in the page.

We then use **`.innerHTML`** to modify the internal HTML of the selected element. if it is set to a new string, it will replace its original content.

So, **`document.querySelector("h1").innerHTML`** means select the first **`<h1>`** tag in the page and modify its internal HTML content to the specified string.

So similarly, the second line **`document.querySelector("p").innerHTML`** means select the first **`<p>`** tag in the page and modify its internal HTML content to the specified string.

But in such need to note that we must put our own title as well as the paragraph at the top of the page. To achieve the effect elsewhere, you can use the id's method, which I will not repeat here.

- Finally, we put the JavaScript code all under one function to achieve the effect that will be loaded only when the page is finished loading. The complete JavaScript code is as follows.

```jsx
<script>
        window.onload = function() {
          var greetings = ['你好', 'Bonjour', 'こんにちは', 'Hello', '안녕하세요', 'Здравствуйте', 'Aloha', 'Hallo', 'chào', 'Ciao', 'Hola'];
          var languages = ['Chinese', 'French', 'Japanese', 'English', 'Korean', 'Russian', 'Hawaiian', 'German', 'Vietnamese', 'Italian', 'Spanish']
          var index = Math.floor(Math.random() * greetings.length)
          var greeting = greetings[index];
          var language = languages[index];
          document.querySelector('h1').innerHTML = greeting + ',';
          document.querySelector('p').innerHTML = "In " + language + ", " + greeting + " means hello!";
        };
    </script>
```

Just put the code at the bottom of the html file

## Sample

You can [**visit here**](https://www.haozheli.com/blogs/greetingsSample.html) to see a sample of the effect, with the full code as follows.

```jsx
<!DOCTYPE html>
<html>
  <head>
    <title>My Simple HTML File</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a simple HTML file with only an h1 and a p tag.</p>
    <script>
        window.onload = function() {
          var greetings = ['你好', 'Bonjour', 'こんにちは', 'Hello', '안녕하세요', 'Здравствуйте', 'Aloha', 'Hallo', 'chào', 'Ciao', 'Hola'];
          var languages = ['Chinese', 'French', 'Japanese', 'English', 'Korean', 'Russian', 'Hawaiian', 'German', 'Vietnamese', 'Italian', 'Spanish']
          var index = Math.floor(Math.random() * greetings.length)
          var greeting = greetings[index];
          var language = languages[index];
          document.querySelector('h1').innerHTML = greeting + ',';
          document.querySelector('p').innerHTML = "In " + language + ", " + greeting + " means hello!";
        };
    </script>
  </body>
</html>
```

## Ending

That's all there is to this article, I'm glad you're here!

Read this article at zhihu.com

[在网页中使用JavaScript实现不同语言打招呼的效果](https://zhuanlan.zhihu.com/p/604068472)

-