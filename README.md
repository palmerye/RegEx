# All In RegEx

> 正则表达式对程序猿来讲是很常见的，但这种非人类的言语表达起来，真的一点都不“正经”。但实质上常见的表达式并不复杂。我目前碰到的应用场景，无非是在某一长串字符串中，是否匹配你想要的内容，或者抠出你想要的内容。

## 语法

最简单的正则表达式就是从左到右逐字匹配，并且大小写敏感。如`am`，则会去字符串中搜索`a`，挨着搜索`m`。

``` javascript
var regex = /am/g;
var string = "I am palmer";
console.log( string.match(regex) ); 
// => ["am"]
```

### 元字符

> 在正则表达式中，经常会看到一些莫名其妙的字符，其实是有特殊的含义，这就是元字符。

|元字符|描述|
|:----:|----|
|.|句号匹配任意单个字符除了换行符.|
|[ ]|字符种类. 匹配方括号内的任意字符.|
|[^ ]|否定的字符种类. 匹配除了方括号里的任意字符|
|*|匹配>=0个重复的在*号之前的字符.|
|+|匹配>=1个重复的+号前的字符.
|?|标记?之前的字符为可选.|
|{n,m}|匹配num个大括号之前的字符 (n <= num <= m).|
|(xyz)|字符集, 匹配与 xyz 完全相等的字符串.|
|&#124;|或运算符,匹配符号前或后的字符.|
|&#92;|转义字符,用于匹配一些保留的字符 <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|
|^|从开始行开始匹配.|
|$|从末端开始匹配.|

#### 点运算符`.`

点运算符`.`，通配符，表示几乎任意字符。换行符、回车符、行分隔符和段分隔符除外。

``` javascript
var regex = /.m/g;
var string = "I am palmer";
console.log( string.match(regex) );
// => ["am", "lm"]
```

#### 字符集`[ ]`

方括号用来指定一个字符集，且不关心顺序。如`/[al]m/g`和`/[la]m/g`的匹配结果是一样的。

``` javascript
var regex = /[al]m/g;
var string = "I am palmer";
console.log( string.match(regex) );
// => ["am", "lm"]
```

##### 否定字符集`[^ ]`

`^`用在一个方括号的开头的时候, 它表示这个字符集是否定的，如表示后面跟着`m`的除`l`以外的任意字符

``` javascript
var regex = /[^l]m/g;
var string = "I am palmer";
console.log( string.match(regex) );
// => ["am"]
```

#### 重复

##### `*` 出现 >= 0次

`*`号匹配在`*`之前的字符出现大于等于0次.

``` javascript
var regex = /[A-Z]*/g;
var string = "I Am Palmer";
console.log( string.match(regex) );
// => ["I", "", "A", "", "", "P", "", "", "", "", "", ""]
// 这里为什么长度为12， 而`I Am Palmer`长度为11？

var regex = /.*/g;
var string = "";
console.log( string.match(regex) );
// => 结果居然是[""]，string的长度为0，但match结果是1？
```

##### `+` 出现 >= 1次

`+`号匹配`+`号之前的字符出现大于等于1 次.

``` javascript
var regex = /[A-Z]+/g;
var string = "I Am Palmer";
console.log( string.match(regex) );
// => ["I", "A", "P"]
```

##### `?` 出现 0次或者1次

``` javascript
var regex = /[^l]m/g;
var string = "I am palmer";
console.log( string.match(regex) );
// => ["am"]
```

#### 点运算符`.`

#### 点运算符`.`

### 简写字符集

> 

|简写|描述|
|:----:|----|
|.|除换行符外的所有字符|
|\w|匹配所有字母数字, 等同于 `[a-zA-Z0-9_]`|
|\W|匹配所有非字母数字, 即符号, 等同于: `[^\w]`|
|\d|匹配数字: `[0-9]`|
|\D|匹配非数字: `[^\d]`|
|\s|匹配所有空格字符, 等同于: `[\t\n\f\r\p{Z}]`|
|\S|匹配所有非空格字符: `[^\s]`|
|\f|匹配一个换页符|
|\n|匹配一个换行符|
|\r|匹配一个回车符|
|\t|匹配一个制表符|
|\v|匹配一个垂直制表符|
|\p|匹配 CR/LF (等同于 `\r\n`)，用来匹配 DOS 行终止符|


## 应用

### 匹配

### 抠抠


[参考文献]

[https://github.com/zeeshanu/learn-regex](https://github.com/zeeshanu/learn-regex)
