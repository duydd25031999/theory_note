# PHP tags
PHP parses a file =looks=> opening and closing tags ("<?php" + "?>")
- start and stop =interpreting=> the code between them
- "<?=" <=short-hand= "<?php"

```
# Template
<?php[khoảng trắng]code?>
```

Khoảng trắng có thể là 
- tabs              ( \t )
- newlines          ( \n )
- carriage returns  ( \r )
- space character   ( \s )

```
# Code
<?php /*space*/ echo "a"?>
<?php
/*end-of-line*/ echo "a"?>
<?php    /*tab*/ echo "a"?>
```

không close => php tự tính dòng cuối là đóng
```
<?php           =>  <?php     
... code            ... code
//end file          //end file
                    ?>
```

Escaping from HTML
```
<?php if ($expression == true): ?>
    <p>This will show if the expression is true.</p>
<?php else: ?>
    <p>Otherwise this will show.</p>
<?php endif; ?>
```

# Datatype
## Scalar types:
Boolean
- falsy -> if sai
    - 0
    - -0
    - 0.0
    - -0.0
    - false
    - null
    - undefined
    - “" (length = 0)
    - NaN
- truthy -> if đúng
    - tất cả không phải falsy
        
String
- concat
```$string_var.another_string // string_var "concat" another_string``

Number

Float

## Compound types:
Array
```
$myArr = array("value 1", "value 2", "value 3");
// (!) $myArr[1] == $myArr['1']
$myArr = ["x", "y", "z"];
array(3) {
    [0] => string(1) "x"
    [1] => string(1) "y"
    [2] => string(1) "z"
}
```

- Array with key value pair.
```
$myArr = [
    "a" => 2,
    "b" => 3
];

//push new key value pair
$myArr['c'] = "x";

array(3) {
    ["a"] => int(2)
    ["b"] => int(3)
    ["c"] => string(1) "x"
}
```

Object

Callable

Iterable

## Special types

resource

NULL

# Condition Statement
if
```
<?php
    $flag = true;
    if($flag == 1) {
        echo "if";
    }
    elseif($flag == true) {
        echo "elseif";
    }
    else {
        echo "else";
    }
?>
```

for
```
for($i = 0; $i < 5; $i++) {
    echo "<p>Hello</p>";
}
```

foreach
```               
$myArr = array("var 1", "var 2", "var 3");
foreach ($myArr as $i) {
    echo $i;
}
foreach ($arr as $key => $value) {
    echo "{$key} => {$value} ";
    print_r($arr);
}
```

# Function
```
function newCal($x) {
    $newX = $x*0.75;
    echo "new X = ".$newX;
}
$x = 100;
newCal(101); //75.75
```

Phải truyền đủ số arguments khi call function.
- Default value of argument `function demoFunction($x = 2)` 
- Unlimit number of argument `function demoFunction(...$x)`
    - `$x` = array

Anonymous function
```
<?php
$message = 'hello';

// Inherit $message
$example = function () use ($message) {
    var_dump($message);
};

$message = 'world';
$example(); //hello <= do function use value of $message before change value

# Để lấy value sau của `$message` => pass by reference.
// Inherit by-reference
$example = function () use (&$message) {
    var_dump($message);
};
$example();

// The changed value in the parent scope
// is reflected inside the function call
$message = 'world';
$example();
```

Closures can also accept regular arguments
```
$message = 'world';
$example = function ($arg) use ($message) {
    var_dump($arg . ' ' . $message);
};
$example("hello");
```

# OOP
## Access modifies
Public 
- Đây là default.

Protected

Private

## Class
Attribute & Method
```
class NewClass {
    public $info = "This is some info";
    private $abc = 1;
    function ower() {
        return $this->abc;
    }
}
$object = new NewClass;
var_dump($object->info);
echo "<br>".$object->ower();
```

Constructors
```
class Person {
    public $name;
    public $eyeColor;
    public $age;
    function __construct($name)
    {
        $this->name = $name;
    }
}
$person2 = new Person("Duy");
```
- Khi đã có contructor thì không thể $object = new NameClass
        
Destructors
```
function __destruct()
{
    echo $this->name." deleted<br>";
}
```
- Object trong PHP có thể delete bởi user.
``` unset($person2);```
        
Static
- `$this` : tương đương với object
- `self::` : tương đương với class
```
class Person {
    ...
    public static $drinkingAge = 21;
    ...
    static function setDrinkingAge($age) {
        self::$drinkingAge = $age;
}
...

echo Person::setDrinkingAge(12);
echo Person::$drinkingAge;
```

Const
```
class Person {
    ...
    const EXAMPLE = 1;
    ...
    self::EXAMPLE;
}

Person::EXAMPLE;
```

## Inheritance
```
class Child extends NewClass
```

parent : tương đương super + parent class
```
parent::normal_func();
parent::static_func();
```

# Polymorphism
Override không cần keyword, chỉ cần dùng lại tên → viết đè code khác.

# Abstract
Interface
```
interface ICanPrint {
    function print() : string;
}
class Animmal implements ICanPrint {
    function print() : string {
        return "Hello";
    }
}
$animal = new Animmal;
echo $animal->print();
```

Abstract class
```
abstract class AbstractClass
{
    // Force Extending class to define this method
    abstract protected function getValue();
    abstract protected function prefixValue($prefix);

    // Common method
    public function printOut() {
        print $this->getValue() . "\n";
    }
}
```

# Form
Get data from form
```
<body>
    <form method="get">
        <input type="text" name="person">
        <button>Submit</button>
    </form>
    <?php
        $name = $_GET['person'];
        /**
        * $_GET['name_input'] khi chưa submit sẽ ko được khởi tạo
        * => báo lỗi
        */
        echo $name." is a handsome fellow";
    ?>
</body>
```

# Include
Với file chỉ gồm php code thì chỉ include php code
```
<?php
    //chỉ include phần code trong tag php thôi
?>
```

Với file gồm html thì include toàn bộ code html
```
//trong file header.php
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
        <title>Php Lession</title>
    </head>
    <body>
        <header>
            <nav>
                <ul>
                    <li><a href="">nav 1</a></li>
                    <li><a href="">nav 2</a></li>
                    <li><a href="">nav 3</a></li>
                    <li><a href="">nav 4</a></li>
                </ul>
            </nav>
        </header>

//trong file index.php
        <?php
            include_once 'header.php';
        ?>
        <h1>Hello</h1>
    </body>
</html>
```
