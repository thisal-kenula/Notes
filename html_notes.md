# HTML

## Structure

```html
    <!DOCTYPE html>
    <html>
        <head>
            <title>Home</title>
        </head>
        <body>
            <h1>Welcome to the Home Page</h1>
            <p>This is the home page of the website.</p>
            <p>Click <a href="about.html">here</a> to go to the about page.</p>
        </body>
    </html>
    ```
    
## Attributes
### Hyperlink

`<a href="[https://www.w3schools.com](https://www.w3schools.com/)">Visit W3Schools</a>` 

### Source

`<img src="img_girl.jpg">`

- Absolute URL: [`https://www.w3schools.com/images/img_girl.jpg`](https://www.w3schools.com/images/img_girl.jpg)
- Relative: `/images/img_girl.jpg`
(For files within the website)
### Width/Height

`<img src="img_girl.jpg" width="500" height="600">`

### Alternative text

(Text to show when file couldn’t be loaded)

`<img src="images/NPP-wallpaper.002.png", alt="RED NPP wallpaper"/>`

### Style
- Font size
    
    `<h1 style="font-size: 75px;">Heading 1</h1>`
    

```html
<p style="color: green;" >
    • Pesuru Maths<br>
    • Physics
</p>
```

### Size

```html
<body>
<table style="width:100%">
```

- Percentages for `size` means how much compared to the parent element(`body` here)
### Tooltip

`<h1 title="I'm a tooltip">Books to be donated </h1>`

- Single quotes are also valid

`title='The "Original" computer'`

## Headings

```html
<body>
    <h1>Heading 1</h1>
    <h2>Heading 2</h2>
    <h3>Heading 3</h3>
    <h4>Heading 4</h4>
    <h5>Heading 5</h5>
    <h6> Heading 6</h6>
</body>
```

- Search engines use headings to index
- Don’t use headings as styling

## Paragraphs

```html
<p>
This is a paragraph
</p>
```

### Ignores multiple whitespaces and undefined line breaks

```html
<p>
    This   paragraph
    contains  a lot of spaces
    in the source         code,
    but the        browser
    ignores it.
</p>
```

This paragraph contains a lot of spaces in the source code, but the browser ignores it.

### Horizontal rule(Separator)

```html
<h1>Heading 1</h1>
**<hr>**
<p>This is some text.</p>
```

### Line break

```html
<p>
    • Pesuru Maths<br>
    • Physics
</p>
```

### Pre formatted text

```html
<h2>Heading 2</h2>
<pre>
    This is an example of pre-formatted
    text

    Line breaks  and whitespaces are applied just as it is
    and printed in fixed width font. But as intended text
</pre>
```

## Text Formatting

- Bold: `<b>This is bold text.</b>`
- Text with strong importance: `<strong>This is Important!</strong>`
- Italic: `<i>This text is in Italic</i>`  
For technical terms, a thought etc. (Don’t make whole text italic)
- Emphasize: `<em>This is also Italic</em>`  
This is also printed in italic. But the screen reader will pronounce with verbal stress
- Small: `<small> This is small</small>`
- Mark/Highlight: `<mark>This is highlighted</mark>`
- Strikethrough(Deleted text): `<del>Defines deleted text. Browsers will strikethrough.</del>`
- Underline(Inserted text): `<ins>Underlined text</ins>`
- Subscript: `H<sub>2</sub>O`
- Superscript: `E = mc<sup>2</sup>`

## Quotation and Citation

### Block quotes

```html
<p>This is an example for block-quote</p>
<blockquote cite="https://www.w3schools.com/html/html_quotation_elements.asp">
    The HTML element defines a section that is quoted from another source.
    Browsers usually indent elements.
</blockquote>
```

### Short quotations

```html
<p>
    Apple's commitment: <q>Carbon neutral by 2030</q>
</p>
```

- Browsers normally add quotation marks around
### Abbreviations

```html
<p>
    The <abbr title="University of Ruhuna">UOR</abbr> takes 200 students for Compueter.
</p>
```

- The `title` will be used as tooltip for abbreviation
- Also helps search engines and browsers
### Address

Contact info for the author/owner of a document/article

```html
<address>
    Written by Thisal Kenula<br>
    Visit us at:<br>
    thsl_knl.com<br>
    E49/3, Forest Hill<br>
    Kegalle
</address>
```

### Title of a creative work

`<p><cite>The Scream</cite> by Edvard Munch. Painted in 1893.</p>`

### Bi-Directional override

`<bdo dir="rtl">This text will be written from right to left</bdo>`

## Comments

`<!-- Write your comments here -->`

```html
<p>This is a paragraph.</p>
<!--
<p>Look at this cool image:</p>
<img border="0" src="pic_trulli.jpg" alt="Trulli">
-->
<p>This is a paragraph too.</p>
```

```html
<p>This <!-- great text --> is a paragraph.</p>
```

## Color

### Background

`<p style="background-color:Tomato;">Lorem ipsum...</p>`

### Text

`<p style="color:DodgerBlue;">Lorem ipsum...</p>`

### Border

`<h1 style="border:2px solid Tomato;">Hello World</h1>`

### RGB, HEX, HSL and RGBA, HSLA values

```html
<h1 style="background-color:rgb(255, 99, 71);">...</h1>
<h1 style="background-color:#ff6347;">...</h1>
<h1 style="background-color:hsl(9, 100%, 64%);">...</h1>

<h1 style="background-color:rgba(255, 99, 71, 0.5);">...</h1>
<h1 style="background-color:hsla(9, 100%, 64%, 0.5);">...</h1>
```

## Styles

- `<*tagname* style="CSS_*property*:CSS_*value;*">`
- Background: `background-color`
- Foreground: `color`
- Font size: `font-size:300%`
- Text Alignment: `text-align:center`

### Font: `font-family`
    
```css
body {
    font-family: 'Arial', 'Helvetica', sans-serif;
}
```

- The browser looks for a font named "Arial" installed on the user's computer.
- If "Arial" is not found, it moves to the next font, "Helvetica."
- If neither "Arial" nor "Helvetica" is available, it uses the generic fallback `sans-serif`, which selects a default sans-serif font available on the system
- Web fonts
    
    ```html
    <!--Using Google fonts-->
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
        }
    </style>
    ```
        
### Change based on device theme(Light dark)
        
```html
        <head>
            <title>Learn HTML</title>
            <link rel="stylesheet", href="styles.css">
            <style>
                @media (prefers-color-scheme: dark) {
                    body {
                        background-color: black;
                        color: white;
                    }
                }
            </style>
        </head>
```
        
## CSS

### Inline

`<h1 style="color:blue;">A Blue Heading</h1>`

### Internal

Defined in the head section

```html
<head>
    <style>
        body {background-color: black;}
        h1 {color: aquamarine;}
        p {color: gold;}
    </style>
</head>
```

### External
- HTML file
    
    ```html
    <head>
        <title>Test</title> 
        <link rel="stylesheet", href="styles.css">
    </head>
    ```
    
    - Full URL
        
        `<link rel="stylesheet", href="[https://www.w3schools.com/html/styles.css](https://www.w3schools.com/html/styles.css)">`
        
- CSS file
    
    ```css
    body {
        background-color: black;
        color: white;
    }
    h1 {
        color: gold;
    }
    p {
        color: aquamarine;
    }
    ```
    
### CSS properties

`color`: Text color

`font-family`: Font

`font-size`

- `border`
    
    ```css
    p {
        border: 2px solid yellow;
    }
    ```
    
    Adds border around paragraph
    
- `padding`
    
    Defines padding between text and the border
    
    ```css
    p {
        border: 2px solid yellow;
        padding: 30px;
    }
    ```
    
- `margin`
    
    Defines a margin outside the border
    
    ```css
    p {
        border: 2px solid yellow;
        padding: 30px;
        margin: 50px;
    }
    ```
    
## Links
    
`<a href="[https://www.w3schools.com/](https://www.w3schools.com/)">Visit [W3Schools.com](http://w3schools.com/)!</a>`
    
### Target
        
`a href="[https://www.w3schools.com/](https://www.w3schools.com/)" target="_self">Visit [W3Schools.com](http://w3schools.com/)!</a>`

`_self`: Opens in the same window/tab/frame (Default)

`_blank`: New window or tab

`_parent`: Opens in parent frame or same window/tab

`_top`: Opens in full body (Breaks out frames)

(`parent` and `top` behaves like self when not in iFrame)
        
### Absolute vs. Relative URL
        
Absolute: `<p><a href="[https://www.google.com/](https://www.google.com/)">Google</a></p>`

Relative: `<p><a href="html_images.asp">HTML Images</a></p>`
or
`<p><a href="/css/default.asp">CSS Tutorial</a></p>`
        
### Email
        
`<a [href="mailto:someone@example.com](mailto:href=%22mailto:someone@example.com)">Send Email</a>`

- use: `mailto:`
- Opens in users email program

### Button as a link
        
Add JavaScript code

`<button onclick="document.location='default.asp'">HTML Tutorial</button>`
        
### Title(Tooltip)
        
`<a href="[https://www.w3schools.com/html/](https://www.w3schools.com/html/)" title="Go to W3Schools HTML section">Visit our HTML Tutorial</a>`
        
### Link colors
        
```html
        <head>
          <style>
              a:link { /* unvisited link */
                  color: green;
                  background-color: transparent;
                  text-decoration: none;
              }
              a:visited { /* visited link */
                  color: pink;
                  background-color: transparent;
                  text-decoration: none;
              }
              a:hover {
                  color: red;
                  background-color: transparent;
                  text-decoration: underline;
              }
              a:active { /* When clicked (not released) */
                  color: yellow;
                  background-color: transparent;
                  text-decoration: underline;
              }
          </style>
        </head>
```
        
### Links as buttons
        
```html
        <style>
            a:link, a:visited { 
                background-color: red;
                color: white;
                padding: 15px 25px; /* 15px: top and bottom; 
                                        25px: left and right */
                text-align: center;
                text-decoration: none;
                display: inline-block; /* inline: flows alongside other elements;
                                        block: respects to the set dimensions;*/
            }
            a:hover, a:active {
                background-color: orange;
            }
        </style>
```
        
### Bookmark link
        
```html
<h2 id="C4">Chapter 4</h2> <!--Header with a bookmark-->
```

```html
<a href="#C4">Jump to Chapter 4</a> <!--Link to bookmark-->
```

- Clicking will scroll to the bookmark
- Link to a bookmark on another page
            
    ```html
    <a href="html_demo.html#C4">Jump to Chapter 4</a>
    ```
            

## Images

```html
<img src="img_chania.jpg" alt="Flowers in Chania">
```

`alt`: If the image cannot be viewed(couldn’t load/when using screen reader)

### Height and Width

- Using `style`
    
    ```html
    <img src="img_girl.jpg" alt="Girl in a jacket" style="width:500px;height:600px;">
    ```
    
- Using `height` and `width` attributes
    
    ```html
    <img src="images/NPP-wallpaper.001.png" alt="NPP wallpaper" width="500" height="600">
    ```
    
- Choose `style` or `width` and `height`
    - `style` will override what’s on style sheets
    - `width` and `height` will change according to style sheets
- To avoid stretching and distorting
    - Set one attribute to auto
        
        ```html
        <img src="images/NPP-wallpaper.001.png" alt="NPP wallpaper" style="width:500px;height:auto;">
        ```
        
    - Change `object-fit`
        
        ```html
        <img src="images/NPP-wallpaper.001.png" alt="NPP wallpaper" style="width:500px;height:500px;object-fit:cover;">
        ```
        

### `src`

- Another folder
    
    ```html
    <img src="/images/html5.gif" alt="HTML5 Icon" style="width:128px;height:128px;">
    ```
    
- Another server/website
    
    ```html
    <img src="https://www.w3schools.com/images/w3schools_green.jpg" alt="W3Schools.com">
    ```
    
- Allows `.gif`

### Use image as a link: put inside `<a>`

```html
<a href="default.asp">
  <img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
</a>
```

### Float (similar to arrange in documents)

```html
<p><img src="smiley.gif" alt="Smiley face" style="float:right;width:42px;height:42px;">
The image will float to the right of the text.</p>
```

### Set clickable areas of image

```html
<img src="images/NPP-wallpaper.001.png" alt="NPP wallpaper" style="width:500px;height:auto" **usemap="#nppmap"**>
<map **name="nppmap"**>
    <area shape="circle" coords="300, 600, 200" alt="NPP website" href="https://www.npp.lk">
</map>
```

- `circle`: “center_x, center_y, radius”
- `rect`: “top_left_x, top_left_y, bottom_right_x, bottom_right_y”
- `poly`: `<area shape="poly" coords="140,121,181,116,204,160,204,222,191,270,140,329,85,355,58,352,37,322,40,259,103,161,128,147" href="croissant.htm">`
- JavaScript
    
    ```cpp
    <map name="nppmap">
        <area shape="circle" coords="300, 600, 200" alt="NPP website" href="https://www.npp.lk" **onclick="myFunction()"**>
    </map>
    <script>
        function myFunction() {
            alert("You clicked the logo")
        }
    </script>
    ```
    

### Background image

- For a paragraph
    
    ```html
    <p style="background-image: url('images/NPP-wallpaper.001.png');">
    ```
    
    or in head:
    
    ```cpp
    <style>
    p {
      background-image: url('img_girl.jpg');
    }
    </style>
    ```
    
- For whole background
    
    ```html
    <style>
    body {
      background-image: url('img_girl.jpg');
    }
    </style>
    ```
    
- Avoid background repeating
    
    ```jsx
    body {
      background-image: url('example_img_girl.jpg');
      background-repeat: no-repeat;
    }
    ```
    
- Background cover
    
    ```jsx
    body {
        background-image: url('images/NPP-wallpaper.001.png');
        background-repeat: no-repeat;
        background-size: cover;
        background-attachment: fixed;
    }
    ```
    
    `background-size: cover;` : Cover entire page
    
    `background-attachment: fixed;` : Prevent moving the image when scrolling
    
- Background stretch
    
    ```jsx
    body {
      background-image: url('images/NPP-wallpaper.001.png');
      background-repeat: no-repeat;
      background-attachment: fixed;
      background-size: 100% 100%;
    }
    ```
    

### `<picture>` : Show different images for different screen sizes

```jsx
<picture>
  <source media="(min-width: 650px)" srcset="img_food.jpg">
  <source media="(min-width: 465px)" srcset="img_car.jpg">
  <img src="img_girl.jpg">
</picture>
```

- `img` is required to show an image on unsupported browsers or when none of the `source` tags match
- Browser will use the first `<source>` with matching attributes and ignore the rest
- When to use
    - Bandwidth
        - For smaller screens
    - Format support
        - Some browsers won’t support all formats. Use different format images and the browser will use the first format it recognize
        
        ```html
        <picture>
            <source srcset="images/tree.jpeg">
            <img src="images/camera.jpeg" alt="A camera">
        </picture>
        ```
        

### Favicon

🥲 Couldn’t figure out

## Title

```html
<head>
  <title>HTML Tutorial</title>
</head>
```

- Browser toolbar
- When added to favorites
- Search engine results

## Table

```html
<table>
    <tr>
        <th>First Name</th> 
        <th>Last Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>Thisal</td>
        <td>Kenula</td>
        <td>20</td>
    </tr>
    <tr>
        <td>John</td>
        <td>Doe</td>
        <td>30</td>
    </tr>
</table>
```

**`tr`**: table row
**`td`**: table data
**`th`**: table header

### Borders

```css
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

### Size(Row/column/table)

```html
<table width="100%;" border="1">
	<tr style="height: 100px;">
	    <th style="width: 20%">First Name</th> 
	    <th>Last Name</th>
	    <th>Age</th>
	</tr>
</table>
```

### Table headers

```html
<tr>
    <**th**>First Name</th> 
    <**th**>Last Name</th>
    <**th**>Age</th>
</tr>
<tr>
    <td>Thisal</td>
    <td>Kenula</td>
    <td>20</td>
</tr>
```

- Use `th` for table headers.
- Rows are also possible

### Column span / Row span (Merge cells)

```html
<table border="1">
    <tr>
        <th **colspan="2"**>Name</th> 
        <th>Age</th>
    </tr>
    <tr>
        <td>Thisal</td>
        <td>Kenula</td>
        <td>20</td>
    </tr>
    <tr>
        <td>John</td>
        <td>Doe</td>
        <td>30</td>
    </tr>
</table>
```

### Table caption

```html
<table border="1">
    **<caption>Table Caption</caption>**
    <!-- Add this jsut after table tag-->
    <tr>
        <th colspan="2">Name</th> 
        <th>Age</th>
    </tr>
    <tr>
        <td>Thisal</td>
        <td>Kenula</td>
        <td>20</td>
    </tr>
    <tr>
        <td>John</td>
        <td>Doe</td>
        <td>30</td>
    </tr>
</table>
```

### Cell padding

- Space between cell edges and cell content

```css
th, td {
  padding: 15px;
}
```

```css
th, td {
  padding-top: 10px;
  padding-bottom: 20px;
  padding-left: 30px;
  padding-right: 40px;
}
```

Or in HTML

```html
<table cellpadding="10">
```

### Cell spacing

- Space between each cell

```css
table {
  border-spacing: 30px;
}
```

or in HTML

```html
<table cellspacing="50">
```

### Table styling

- Zebra stripes
    
    ```css
    tr:nth-child(even) {
      background-color: #D6EEEE;
    }
    ```
    
    - For rows
        
        ```css
        td:nth-child(even), th:nth-child(even) {
          background-color: #D6EEEE;
        }
        ```
        
    - For both
        
        ```css
        tr:nth-child(even) {
          background-color: rgba(150, 212, 212, 0.4);
        }
        
        th:nth-child(even),td:nth-child(even) {
          background-color: rgba(150, 212, 212, 0.4);
        }
        ```
        
- Horizontal dividers
    
    ```html
    <table class="horizontal-dividers">
        <style>
            .horizontal-dividers th, .horizontal-dividers td {
                border-bottom: 1px solid black;
            }
        </style>
    ...
    ```
    
- Change color on hover
    
    ```html
    <table class="hoverable-table">
        <style>
            .hoverable-table tr:hover {
                background-color: rgba(150, 212, 212, 0.4);
            }
        </style>
    ...
    ```
    

### Style first columns

```html
<table>
  <colgroup>
    <col span="2" style="background-color: #D6EEEE">
  </colgroup>
  <tr>
    <th>MON</th>
    <th>TUE</th>
    <th>WED</th>
    <th>THU</th>
...
```

- Allowed CSS properties in `colgroup`
    
    `width`
    
    `visibility`
    
    `background`
    
    `border`
    

<aside>
💡

Notes from [Table `colgroup`](https://www.w3schools.com/html/html_table_colgroup.asp#legalcss)  were not written.
Just refer to [W3Schools](https://www.w3schools.com/html/html_table_colgroup.asp#legalcss)

</aside>