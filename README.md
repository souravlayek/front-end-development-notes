---
description: All the notes related to htm
---

# HTML

### Tags

* Normal Tag
  * Every HTML element has one opening and one closing tag, In between that if you write anything it will be visible in the browser.
  * Like in this example \<h1> \</h1>, \<h1> This is referd to openning tag but \</h1> This is refered to closing tag
* Self Closing Tag
  * Some HTML elements don't have a closing tag that closes in their opening tag
  * Link in this example \<input /> this tag is self-closing

### Structure of HTML

Html Document (The file which has a .html extension, e.g index.html) contains some predefined structure

<pre class="language-html"><code class="lang-html">&#x3C;!DOCTYPE html>
&#x3C;html>
<strong>    &#x3C;head>
</strong><strong>        &#x3C;title>Dymmy Page&#x3C;/title>
</strong><strong>        &#x3C;meta name="description" content="This is render when we search in google" />    
</strong><strong>    &#x3C;/head>
</strong><strong>    &#x3C;body>
</strong><strong>        &#x3C;!--
</strong><strong>        This is a comment it won't render in the browser
</strong><strong>        and inside the body whatever we write it will show in the browser
</strong><strong>        -->
</strong><strong>    &#x3C;/body>
</strong>&#x3C;/html></code></pre>

In the above code, we have a few tags, below I have discussed why we have to create this structure for every HTML

* \<!DOCTYPE html>
  * This is used as a 'declaration'. It isn't a tag. It is used to tell the browser how to render the page, which means how to show that page you have written in the code.
  * The browser doesn't understand different HTML versions, there are fewer tags in an older version of HTML like in HTML 4.1, the way we write in the above example the browser will understand it's an HTML5 document and it will render the same in every browser as you expect.
* The \<html> tag is used to tell the browser it is the entire document. It isn't necessary but it is an industry standard.
* \<head>
  * This is used to store information about the webpage, there are some predefined tags to show different things.
  * We will discuss these later about those but for now, we will understand two tags
  * title: Which are used to store the title of any site which is visible in two places One is in the tab of the browser and another is in the google search (In the example two this violet color youtube test is the title)
  * meta for all the information related to the webpage
    * In the second example, we use meta with name description for the Text written in gray

<figure><img src=".gitbook/assets/2022-08-30 20_30_25-HTML - Front End Notes.png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/2022-08-30 20_34_04-youtube - Google Search (1).png" alt=""><figcaption></figcaption></figure>

The body is the content that will be visible in the browser



### Different HTML tags and their use

| Tag Name                         | Purpose                                                                                                                                                                          |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \<html>\</html>                  | Start and end of document                                                                                                                                                        |
| \<h1>\</h1>                      | Leargest Heading, There are 6 type of heading tag h1, h2, ... h6                                                                                                                 |
| \<p>\</p>                        | paragraph tag, use to show text in normal size.                                                                                                                                  |
| \<br/>                           | Use to add like break. Using this will put everything after this tag in the next line                                                                                            |
| \<strike>\</strike>              | Text with strike through like ~~This is strike through text~~                                                                                                                    |
| \<b>\</b> OR \<strong>\</strong> | Both b and strong use to bold the text. Like **Bold Text**                                                                                                                       |
| \<i>\</i>                        | i tag is used to make the text italic. Like _Italic Text_                                                                                                                        |
| \<u>\</u>                        | This is used to underline text.                                                                                                                                                  |
| \<table>\</table>                | table tag is used to create table this contains multiple tags to create a proper table Like td, tr, thead, tbody. We will have different section for that to uderstand properly. |
| \<img />                         | This is used to show images. it has multiple [attributes](./#undefined), like src with the value of the image file. alt for alternative text if the image isn't visible.         |
| \<form>\<form>                   | This is used to create a form, it also contains multiple [attribute](./#undefined), That will help to set the behavior of the form.                                              |
| \<input />                       | This is used to take input from the user. [visit here for more](./#undefined)                                                                                                    |
| \<button>\</button>              | To show a clickable button                                                                                                                                                       |
| \<a href="website link" />       | This is used to add link to another page or website                                                                                                                              |
| \<!-- Comment between this -- >  | We use this way to comment between HTML, comment doesn't reflect in the browser.                                                                                                 |

### Attributes & Content\`

There are different sections of a tag

<figure><img src=".gitbook/assets/2022-08-30 20_57_56-Microsoft Whiteboard.png" alt=""><figcaption></figcaption></figure>

In the above example, I have show different section of a tag

* In the **red line,**  we have the tag name which is p in this example
* in the **green underline,** we have the attribute name which is  class in the example
* in the **Yellow Line,** we have the value for that attribute, Like here infoParagraph is the value of class attribute
  * We write attribute as **attributeName="attributeValue"**
* In the **Blue Line,** we have the content for the tag.
* We use attributes for different purposes, every tag has its own set of predefined attributes.

### Input

**\<input type="type of the different input" />** eg. _**\<input type="text" />**_

| type     | purpose                                                                                                                                           |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| text     | To take Text Input                                                                                                                                |
| password | To take password input, no character in the input box will be visible everything will look like \*.                                               |
| email    | takes only email input                                                                                                                            |
| radio    | To select only one between options                                                                                                                |
| checkbox | use to select multiple options.                                                                                                                   |
| button   | To show a clickable button, but we need to pass value attribute to give content to the button                                                     |
| submit   | Submit is also like type button but it can submit a form, this is mainly used to submit a form.                                                   |
| file     | This helps us to take file input                                                                                                                  |
| number   | Takes only number as input                                                                                                                        |
| range    | it wil give us a slider to take a range between two values, we can pass min and max as attribute                                                  |
| search   | this will help us to create a seach box, it looks similar like text box, but when we write something it will show a 'x' button to clear the text  |
| tel      | to take phone number as input                                                                                                                     |
| time     | this will help us to take time input                                                                                                              |
| reset    | just like a button helps to clear a form                                                                                                          |
| url      | to take url inputs                                                                                                                                |

Here is the example of different tags and how it looks

<div>

<figure><img src=".gitbook/assets/2022-08-30 21_29_42-cool-surf-uf0ymf - CodeSandbox.png" alt=""><figcaption><p>Click to zoom</p></figcaption></figure>

 

<figure><img src=".gitbook/assets/2022-08-30 21_30_22-cool-surf-uf0ymf - CodeSandbox.png" alt=""><figcaption><p>Click to zoom</p></figcaption></figure>

</div>

### How to link CSS?

Create a CSS (Cascade Style Sheet) file in your project folder. And then use link tag as the child of head tag of your HTML document.

\<link rel="stylesheet" href="./styles.css" />

In the above line the

* The link is the tag to link other files
* the rel attribute is used to show the type of file you linked
* and the href to link the file, we pass the path of the file as the href's value.

In the example in the project folder where you html is present we have created a style.css file. And then we linked that with this tag.

### How to style any tag?

This is a two-step process after linking your css file to your html.

The first one is to name the tag, or some kind of identifier to find that tag. We have two kind of identifier

1. class: we can pass class in any tag as an attribute and the value of that class is the name of that tag.
2. id: As class we can also pass id as an argument of any tag and pass value as the name of that tag. **BUT the key difference between id and class is we can use same class name for multiple tags, but not for id, id must be unique.**

```html
<body>
    <!-- In this tag I have showed you how you can write class
      we can add multiple classs of one tag separated by space( )
      Most preferable way to write class name is the secondClass way
      -->
    <div class='first-class secondClass'>
    </div>
    <!-- we can use class and id both in one tag -->
    <div class="testClass" id="testID">
    </div>
</body>
```

The Second step is, using that identifier in css

In the css, we have three way to point a element of a HTML, in the below example I will show it how

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <p>Hello Partner</p>
    <div class="firstBox">
      first box
    </div>
    <div id="secondBox">
      second box
    </div>
  </body>
</html>

```

Here below I have attached the CSS of the above HTML, read the comment's to understand what happened.

```css
/* All the example here is for the above HTML */

/* We use no prefix before the tag name
 to point the tag, and change css of that tag 
 This isn't good as it will select all p in the whole HTML
 */
p {
  color: red;
}

/*
We use a dot (.) as prefix of the class to identify as 
a class, this is best way to point a tag
*/
.firstBox {
  color: blue;
}

/* We use the pound symbol (#) as to identify as Id
This is also a good way to point a tag, only down side and also upside
is that you can only style a single tag with this but in terms of class
you can use that class to similar like tag, where you want the style
and the style will be applied
*/

#secondBox {
  color: purple;
}

```

Here you can see the output of that HTML

<figure><img src=".gitbook/assets/2022-09-11 20_22_58-Html code editor (forked) - CodeSandbox.png" alt=""><figcaption><p>OUTPUT with style</p></figcaption></figure>

