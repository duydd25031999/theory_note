# box model

## box-sizing
content-box
- "width" và "height" chỉ để định nghĩa content size.
- Border và padding không included
- **(!)** Default
border-box
- "width" x "height" = content + border + padding

# the cascade (thác nước)
If a class is added to that element, apply these styles.

If element X is a child of element Y, apply those styles.

Khi thuộc tính của parent được áp dụng cho thằng child (inheritance)

## Declarations conflict
1 style property của 1 element bị nhiều nguồn khác nhau sửa => Declarations conflict

### Stylesheet origin
Where the styles come from. 
- Style của element kết hợp giữa code + browser’s default styles
- origin => cách browser lấy style

author styles
- style do coder defind
- higher priority

user agent styles
- browser’s default styles
- lower priority
- với mỗi browser khác nhau thì user agent styles sẽ khác nhau

important declaration
```
# Template
    attribute: value !important
# Code
    color: red !important;
```

Declarations marked !important are treated as a higher-priority origin
1. Author important
1. Author
1. User agent
        
### Selector specificity
Độ ưu tiên lựa chọn của từng style đối với 1 element

inline styles
- Inline styles have no selector because they are applied directly to the element they target.
- Nó sẽ bỏ qua các style khác
    - internal style `<style>`
    - external style `<link rel="stylesheet" type="text/css" href="mystyle.css">`
- **(!)** “scoped” declarations

A selector được chọn bằng cách tính độ specificity
- `#id` =higher priority=> `.class` =higher priority=> `tag`
1. Tính theo `#id` : 
    - có #id nhiều hơn sẽ thắng
    - 1 #id =higher priority=> nhiều class
2. Tính theo `.class` : 
    - không có #id thì .class nhiều hơn sẽ thắng
3. Tính tag : không có #id + .class thì <tag> nhiều hơn sẽ thắng
- Ví dụ 1
```
# Html
<li>
    <a href="/specials" class="featured">
        Specials
    </a>
</li>
```
```
# Css
#main-nav a {   // có #id
    color: white;
    background-color: #13a4a4;
    padding: 5px;
    border-radius: 2px;
    text-decoration: none;
}

.featured {     // ko có #id
    background-color: orange;
}
```
- Ví dụ 2
```
# Html
<p class="class1 class2">.class1 .class2</p>
<p id="id1">#id1</p>
<p id="id1" class="class1 class2">#id1 .class1 .class2</p> 
```
```
# Css
.class1.class2 {
    color: red;
}
#id1 {
    color: blue; //lấy #id1
}
```

Source order
- Order in which styles are declared in the stylesheet.
- thức tự css được import vào
- **(!)** khi code css thì phải code cho đúng thứ tự
```
a:link {
    color: blue;
    text-decoration: none;
}

a:visited {
    color: purple;
}

a:hover {
    text-decoration: underline;
}

a:active {
    color: red;
}
```
                    
Flow giải quyết declarations conflict
```
-----------------------------      ----------------------------      --------------------      ----------------------      --------------------------
|                           |      |       Different          |      |  Is one an       |      |    Do selectors    |      |    Use declaration     |
|   declarations conflict   |=====>|  origin or importance?   |==NO=>|  inline style?   |==NO=>|    have different  |==NO=>|    that comes later    |
|                           |      |                          |      |  (Scope)         |      |    specificity ?   |      |    in source order     |
-----------------------------      ----------------------------      --------------------      ----------------------      --------------------------
                                                ||                            ||                          ||
                                                YES                           YES                         YES
                                                ||                            ||                          ||
                                                \/                            \/                          \/
                                    ----------------------------      -------------------      ----------------------
                                    |   Use declaration with   |      | Use inline      |      |    Use declaration |
                                    |   higher priority origin |      | declaration     |      |    with higher     |
                                    |                          |      |                 |      |    specificity     |
                                    ----------------------------      -------------------      ----------------------
```
- **(!)** Don’t use IDs in your selector.
- **(!)** Don’t use !important.

## shorthand values
dùng cho padding, margin
- top, right, bottom, left
- top, right & left, bottom
- horizonal, vertical
    - top & bottom, right & left

# css variable

var()
```
# Template 
var(custom-name)        /* lâý value của 1 custom-name */
var(custom-name, value) /* define variable + assign value cho variable + lấy ra chính value đó */
```
    
live (trực tiếp)
- Nó không phải preprocessor giống như scss | sass
- Sử dụng như 1 công thức có thể thay đổi đầu vào
```
# Html
<button class="btn">Hello</button>
<button class="btn red">Hello</button>
<button class="btn yellow">Hello</button>
<button class="btn green">Hello</button>
<button class="btn orange">Hello</button>
<button class="btn teal">Hello</button>
```
```
#CSS
.btn {
    padding: 2rem 4rem;
    border: 2px solid var(--color, black); //define varialbe + assign value
    background: transparent;
    font-size: 0.6em;
    border-radius: 2px;
}
.btn:hover {
    cursor: pointer;
    background: var(--color, black);//define varialbe + assign value
    color: white;
}

/* variations */

.btn.red {
    --color: red //assign giá trị khác cho varible
}
.btn.yellow {
    --color: yellow
}
.btn.green {
    --color: green
}
.btn.orange {
    --color: orange
}
.btn.teal {
    --color: teal
}
```

chỉ có thể sử dụng variable trong scope mà nó được khai báo
- `:root` : khai báo global mà những file khác có thể sử dụng

# relative units
em
- 1em = 1 x font-size of current element
    
rem
- 1rem = 1 x root font-size

@media
```
# Type 
all	Default.    Used for all media type devices
print	        Used for printers
screen      	Used for computer screens, tablets, smart-phones etc.
speech	        Used for screenreaders that "reads" the page out loud
```
```
@media (min-width: 800px) { // Applies only to screens 800
    :root {                 // px and wider, overriding
        font-size: 0.875em; // the original value
    }
} 

@media (min-width: 1200px) { // Applies only to screens
    :root {                  // 1,200 px and larger,
        font-size: 1em;      // over
    }
}
```

# margin
## Negative margin
### left
div sẽ `CHIẾM` phần của left element (cùng z-index)
```
----------------(!)-------------
!           |///(!)////////////|
!   left <= |///(!)////////////|
!           |///(!)////////////|
----------------(!)-------------
```
### top
div sẽ `CHIẾM` phần của top element (cùng z-index)
```
..................
|      top       |
|       /\       |
|       ||       |
------------------
|////////////////|
..................
|////////////////|
|////////////////|
|////////////////|
------------------
```
### right
div sẽ `BỊ CHIẾM` bởi right element (cùng z-index)
```
-------------------------------------
|/////////(!)/////////|           (!)
|/////////(!)right <= |           (!)
|/////////(!)/////////|           (!)
-------------------------------------
```
### bottom
div sẽ `BỊ CHIẾM` bởi bottom element (cùng z-index)
```
..................
|                |
|                |
|                |
------------------
|////////////////|
..................
|////// || //////|
|////// \/ //////|
|//// bottom ////|
------------------
```

## Margin collapse
- Nếu 2 elements ngang hàng => margin giữa 2 element chọn cái lớn hơn (không phải tổng 2 cái)
- Chỉ xảy ra với chiều dọc (vertical), không xảy ra với chiều ngang horizontal

# float
purpose of float
- Normal flow of the page : sắp xếp element tuân theo thứ tự trong code
- Floated element vẫn trong flow of the page nhưng không phải là normal flow
- Các elements trong normal flow ignore những floated elements và flow tiếp

Float Collapsing
- Khi các children trong div đề là floated => normal flow rỗng => height = 0

# display
## inline
không chiếm dòng

không custom kích thước (kích thước theo content)

luôn có margin có sẵn
## block
chiếm cả 1 dòng

thay đổi margin để chiếm dòng đó

custom kích thước

## inline-block
hiển thị chiếm phần kích thước của nó
