# 1. Các tag HTML phổ biến

## `<a>`
Gán 1 element với 1 link

href
- chứa link của `<a>`

## `<img> `
Ảnh show trong page

src
- link tới ảnh

alt
- short description tới ảnh

## heading `<h1> … <h6>`
Heading cho trang web

`<h1>` lớn nhất => `<h6>` bé nhất

## list 
### `<ol>`
Order list

### `<ul>`
Unordered list

### `<li>`
– từng item trong list

## `<html>`
container for the document 
- đánh dấu the beginning + the end of markup
- The root tag of a html file.

## `<head>`
a container for metadata (data about data) 
– title of page
- links to stylesheets are found
- Metadata is not displayed.

### `<title>`
title of page
- default title: domain của page

### `<style>`
define internal style information (CSS) for a document

### `<link>`
- indicates that an external file is linked to the current html document and is commonly used to link an external stylesheet to format the contents of the document

### `<meta>`
Metadata is data (information) about data.
- character set
- page description
- keywords
- author of the document
- viewport settings.

always go inside the `<head>` element

Metadata sẽ không hiển thị trên UI
- Là data chuyên để máy đọc
- Embed vào các web, application khác
- Search engine 

### `<script>`
Defind script của document
- `src` link tới file script
- `type` định nghĩa loại script
- HTML compile từ trên xuống dưới
    - compile tới đâu run tới đó
    - `<script>` để ở cuối để các UI tag được load hêt vào DOM

interal script
- Viết code trong tag `<script>`

external script
- link tới 1 file script

```
<script type="application/javascript" src="./main.js"></script>
```

## `<body>`
chứa những element sẽ được hiển thị UI

## `<div>`
A division or a section of a page.

## `<form>`
để nhập form trong web

action 
- specifies where to send the form-data when a form is submitted

target 
- specifies where to display the response that is received after submitting the form.

method 
- specifies the HTTP method to use when sending form-data

Autocomplete, novalidate

## `<input>`
used inside an HTML form and is used to accept user input or submit the input

### type
các cách có thể nhập vào UI input

checkbox: input dưới dạng checkbox
- nếu tích thì field = value của input
- ko thì field = null

color: nhập bảng màu

date: nhập ngày

file
- nhập file

email: nhập email
- check input đúng format email

number: chỉ nhập số
- có button lên xuống để tăng giảm value theo step

password: nhập password
- ẩn giá trị nhập liệu trên input
- vẫn có thể xem value = code

radio: nhập theo radio
- 1 field có thể có nhiều `input:radio`

button: input dưới dạng button

hidden: input ẩn
- dành cho field không để lộ trên UI

text: nhập text
- default type

submit: button để submit form

image: defines an image as a submit button

datetime-local

month

range

reset: button để reset toàn bộ value của form

search

tel

time

url

week

### value
default value của input

### readonly
không cho change value nhưng vẫn cho copy giá trị của input

### disabled
không cho change value + không copy giá trị của input

### size
số lượng character được hiện thị
- works with the following input types: text, search, tel, url, email, and password.
- vượt quá characters => overflow

maxlength
- maximum number of characters allowed in an input field.

min, max, 
- specify the minimum and maximum values for an input field
- work with the following input types: number, range, date, datetime-local, month, time and week

step
- specifies the legal number intervals for an input field.

### multiple
user is allowed to enter more than one value in an input field

works with the following input types: email, and file.

### placeholder
specifies a short hint that describes the expected value of an input field
The short hint is displayed in the input field before the user enters a value.

### pattern
defind regex để check input
- specifies a regular expression that the input field's value is checked against, when the form is submitted.

### required
check input trống khi submit

### autofocus
specifies that an input field should automatically get focus when the page loads.

### width,height 
- specify the height and width of an `<input type="image">` element.

### autocomplete
- Autocomplete allows the browser to predict the value. When a user starts to type in a field, the browser should display options to fill in the field, based on earlier typed values.
## `<label> `
used in forms and will label HTML input elements

for 
- should be equal to the id attribute of the `<input>` element to bind them together.

## comment tag
```<--...!-->```
Used to add text to your document that will not be displayed in the browser and is useful to document the design of the page.

# 2. Cấu trúc HTML của 1 page
```
<!DOCTYPE>
<html>
    <head>
        <title />
        <style />
        <link />
        <meta />
        <noscript />
    </head>
    <body>
        Cấu trúc của body thường bao gồm các phần sau:
        
        <header>
            có thể chứa logo, câu slogan, các liên kết, các banner liên kết, các button, đoạn flash, hoặc các form ngắn như form tìm kiếm,...
            <nav> 
                Global navigation, dùng để chứa các liên kết đến những trang quan trọng trong toàn bộ trang, trong phần này có thể chứa thêm các liên kết con (sub navigation).
            </nav>
        </header>

        <main>
            phần này chứa nội dung chính cần thể hiện cho người dùng xem.

            <section> 
                dùng để chia các thành phần trong <main>
            </section>  

            <aside>
                nằm trong <main> tag, phần này có thể chứa liên kết phụ của từng trang (local navigation), hoặc các banner chứa liên kết liên quan, hoặc có thể dùng để chứa các liên kết quảng cáo,...
            </aside>
            
        <footer>
            phần này thường chứa phần liên hệ như: tên công ty, địa chỉ, số điện thoại, email liên hệ,... và đặc biệt là copyright, hoặc có thể chứa các liên kết toàn trang, các banner liên kết,...
        </footer>

        <script />
    </body>
</html>
```
