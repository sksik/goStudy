# go基础

## 程序结构

### 1.1 命名

go语言中，需要对函数、变量、常量、类型、语句标号、包等进行命名。

名字必需以字母或下划线开头，后面可以跟任意数量的字母、数字、下划线

命名使用的字母区分下划线

命名不能使用go关键字，同时也不建议使用预定义的名称

```go

// 关键字

break
default
func
interface
select
case
defer
go
map
struct
chan
else
goto
package
const
fallthrough
if
range
type
for
import
return
var
continue
switch

// 预定义名称

// 内建常量

true
false
iota
nil

// 内建类型

int int8 int16 int32 int64
uint uint8 uint16 uint32 uint64
float32 float64 complex128 complex64
bool byte rune string error

// 内建函数

make
len
cap
new
append
copy
close 
delete
complex
real
imag
panic
recover

```

预定义的名称，可以重新使用，但最好避免使用，避免引起语义混乱

如果一个名字再函数内部定义，那么它就只能在函数内部有效

在函数外部定义，将在当前包的所有文件都

名字的开头字母的大小写决定了名字在保外的可见性

名字是大写字母开头的，那么它是导出的，也就是可以被外部的包访问

名字的长度没有限制，但需尽量简洁明了

### 1.2 声明

声明语句定义了程序的各类实体对象和属性

声明语句：var、 const、 type 和 func。分别对应变量、常量、类型、函数实体对象的声明

源文件首先声明自己属于哪个包（package），然后声明导入了哪些包（import）

之后是包一级的类型、变量、常量、函数和声明语句

然后是包一级的类型、变量、常量、函数的声明语句

包一级的各种类型声明顺序无关紧要

## 1.3 变量

var声明语句可以创建一个特定类型的变量，然后给变量附加一个名字，并且设置变量的初始值

> var name type = expression
> 其中type或 = expression可以去掉

expression可以时字面量或者任意的表达式。同时也可以是函数

如果省略类型信息，则会根据初始化表达式来推到

如果初始化的表达式省略，则用零值初始化该变量

**各类型的零值**

- 数值类型 0
- 布尔类型 false
- 字符串类型 ""
- 接口或引用类型（包括slice、指针、map、chan和函数） nil
- 数组或结构体等聚合类型 每个元素或字段都对应该类型的零值

声明时，可以同时声明多个变量。且初始化成不同的类型

> var i, j, k int

> var x, y, z = true, 1, 32.0

### 1.3.1 简短变量声明

> name := expression

简短变量更具表达式自动推导类型

简短变量声明，一般用于局部变量的声明和初始化。具有简洁、灵活的特点

var形式的声明语句往往需要显式指定变量类型的地方