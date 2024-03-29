书写格式：

## 标题

>引用多少页的内容

详细解释

```
代码
```

--------------------------------

## 目录

<!-- TOC -->

- [标题](#标题)
- [目录](#目录)
- [对常量的引用](#对常量的引用)
- [赋值运算右结合律，返回左侧运算对象](#赋值运算右结合律返回左侧运算对象)
- [解引用和递增运算符](#解引用和递增运算符)
- [条件运算符的右结合律](#条件运算符的右结合律)
- [逻辑和关系运算符，运算对象和求值结果都是右值](#逻辑和关系运算符运算对象和求值结果都是右值)
- [string （字符串） 和 char[] （字符数组）的指针](#string-字符串-和-char-字符数组的指针)
- [字符串赋值给字符指针](#字符串赋值给字符指针)
- [让 std::cin 读取空白字符](#让-stdcin-读取空白字符)
- [解引用和递增运算符](#解引用和递增运算符-1)
- [指针的引用](#指针的引用)
- [递归打印 vector](#递归打印-vector)
- [检查类型是否为字面值(literal type)](#检查类型是否为字面值literal-type)
- [处理string对象中的字符(such as `isdigit`, `isalpha`..)](#处理string对象中的字符such-as-isdigit-isalpha)
- [使用 std::boolalpha 在标准输出打印 true, false](#使用-stdboolalpha-在标准输出打印-true-false)
- [从数组向 vector 拷贝元素](#从数组向-vector-拷贝元素)
- [迭代器运算符 和 迭代器支持的算术运算](#迭代器运算符-和-迭代器支持的算术运算)
- [使用 cout 输出 float, double 指定的精度](#使用-cout-输出-float-double-指定的精度)
- [sizeof 求数组大小](#sizeof-求数组大小)
- [remove_if + erase 删除容器中符合要求的元素](#remove_if--erase-删除容器中符合要求的元素)
- [transform 将 string 中的大写转为小写](#transform-将-string-中的大写转为小写)
- [动态分配对象初始化（`new`）](#动态分配对象初始化new)
- [shared_ptr 初始化方式](#shared_ptr-初始化方式)
- [`new` 和 `delete` 方法](#new-和-delete-方法)
- [shared_ptr 的引用和拷贝(问题遗留)](#shared_ptr-的引用和拷贝问题遗留)
- [类内定义的成员函数默认是内联的，类外定义的成员函数需要加 inline 定义](#类内定义的成员函数默认是内联的类外定义的成员函数需要加-inline-定义)
- [拷贝构造函数的参数为什么一定是引用类型](#拷贝构造函数的参数为什么一定是引用类型)
- [vector 的元素为类类型时，添加元素、销毁容器时构造函数，析构函数调用情况](#vector-的元素为类类型时添加元素销毁容器时构造函数析构函数调用情况)
- [std::allocator<T> 类型对象拷贝](#stdallocatort-类型对象拷贝)
- [一个简单的 string 类的实现](#一个简单的-string-类的实现)
- [派生类的析构函数只负责销毁自己的成员](#派生类的析构函数只负责销毁自己的成员)
- [派生类只能在初始值列表中使用基类的构造函数](#派生类只能在初始值列表中使用基类的构造函数)
- [类成员的初始化只能使用等号或者花括号，不能用圆括号](#类成员的初始化只能使用等号或者花括号不能用圆括号)
- [多态(polymorphism)](#多态polymorphism)
- [extern 和 static](#extern-和-static)
- [RTTI(Run-Time Type Identification) and typeid](#rttirun-time-type-identification-and-typeid)
- [pimpl idiom(pointer to implementation)](#pimpl-idiompointer-to-implementation)
- [operator* operator+ 返回值是否需要为 const](#operator-operator-返回值是否需要为-const)
- [cin, cin.get, getline() 方法（对中止符的处理）(如何判断读入 enter)](#cin-cinget-getline-方法对中止符的处理如何判断读入-enter)
- [遍历 map](#遍历-map)
- [遍历 map 时删除元素](#遍历-map-时删除元素)
- [反向迭代器 reverse_itreator](#反向迭代器-reverse_itreator)
- [去除 string 首尾的标点符号 (punctuation)](#去除-string-首尾的标点符号-punctuation)
- [this pointer](#this-pointer)
- [什么时候使用类的 this pointer](#什么时候使用类的-this-pointer)
- [二分法实现 lower_bound 和 upper_bound](#二分法实现-lower_bound-和-upper_bound)
- [类没有任何变量和函数/类只含有构造函数和析构函数/类只有虚函数 sizeof 各占多少空间](#类没有任何变量和函数类只含有构造函数和析构函数类只有虚函数-sizeof-各占多少空间)
- [sizeof vector](#sizeof-vector)
- [convert double/float to string without trailing zeros](#convert-doublefloat-to-string-without-trailing-zeros)
- [std::unordered_map 为什么慢](#stdunordered_map-为什么慢)
- [std::thread 作为 std::unordered_map 的 value](#stdthread-作为-stdunordered_map-的-value)
- [pair<T, T> 作为 unordered_map, unordered_set 的 key](#pairt-t-作为-unordered_map-unordered_set-的-key)

<!-- /TOC -->
--------------------------------

## 对常量的引用

>p127 逻辑和关系运算符

s被声明为了对常量的引用，在这里因为text的内容是string对象，可能非常大。所以把s声明成引用可以避免对元素的拷贝。由于不需要对s进行写，所以声明成对常量的引用。

```cpp
for (const auto &s: text){
    cout << s;
    if (s.empty() || s[s.size()-1] == '.') cout << endl;
    else cout << " ";
}
```

## 赋值运算右结合律，返回左侧运算对象

>p129 赋值运算符

赋值运算符满足右结合律，返回左侧运算对象。

```cpp
int a, b;
a = b = 1;
// 相当于，其中b为右侧赋值运算符的返回值
a = (b = 1);
```

## 解引用和递增运算符

>p132 递增运算符

递增运算符的优先级大于解引用运算符。所有执行结果是返回当前值，然后向前移动一个位置。

`*p++` = `*(p++)`

## 条件运算符的右结合律

>p135 嵌套条件运算符

条件运算符的结合性是右结合的，即 `a?b:c?d:e` 为 `a?b:(c?d:e)` ，即靠右边的条件运算构成了靠左边的条件运算的分支。

若它是左结合的话，上述条件表达式加括号应为 `(a?b:c)?d:e` .

## 逻辑和关系运算符，运算对象和求值结果都是右值

>p126 逻辑和关系运算符

留个坑

## string （字符串） 和 char[] （字符数组）的指针

>p133 成员访问运算符

对于该章节的例子，声明指向某一个 string 的指针：

```cpp
string s1 = "hello, world", *p1 = s1; 
```

上述写法报错：

```
error: cannot convert 'std::string {aka std::basic_string<char>}' to 'std::string* {aka std::basic_string<char>*}' in initialization
     string s1 = "hello, world", *p = s1;
```

正确写法为：需要在 s1 前方加上取地址符。

```cpp
string s1 = "hello, world", *p1 = &s1;
```

不要和指向字符数组的指针搞混，指向字符数组可以不加取地址符。

```cpp
char s2[] = "HELLO WORLD", *p1 = s2;
cout << *p1;  // 输出'H'
```

## 字符串赋值给字符指针

对于语句 `const char *a = "HELLO"`来说，声明了一个字符指针，并将字符串常量的第一个字符的地址赋值给指针 a。

```cpp
char *a = "hello";
cout << *a << " " << *(a+1) << endl; 
// warning: deprecated conversion from string constant to 'char*' [-Wwrite-strings]
//     char *a = "hello";
// 不赞成将字符串常量转换成 char*
```

正确写法应该为 `const char *a = "hello";`

## 让 std::cin 读取空白字符

>p164 习题5.11

习题5.11统计空格，制表符，换行符的数量。所以需要 std::cin 读取空格。

在标准的流中，有一个skipws标记，默认是置位的，表明当读取空白字符时，会将它们丢弃。使用std::noskipws操纵符可以清除这个标记：

```cpp
while (std::cin >> std::noskipws >> c)
{
     std::cout << c << std::endl;
}
```

默认是忽略掉空格的，也就是：

```cpp
while (std::cin >> std::skipws >> c)
{
     std::cout << c << std::endl;
}
```

## 解引用和递增运算符

>p132 在一条语句中混用解引用和递增运算符

后置运算符的优先级要高于解引用运算符，运算符优先级表见 [运算符优先级表](https://github.com/piaoliangkb/CppPrimer#%E8%A7%A3%E5%BC%95%E7%94%A8%E5%92%8C%E9%80%92%E5%A2%9E%E8%BF%90%E7%AE%97%E7%AC%A6)

```cpp
cout << *begin++ << endl;
// 相当于
cout << *(begin++) << endl;
```

作用为输出 begin 开始指向的元素，并且将指针向前移动一个位置。

## 指针的引用

>p196 习题6.22

习题要求交换两个int指针，则需要将指针形参设置为指针的引用。

```cpp
void swap(const int* &p1, const int* &p2)
{
     auto temp = p1;
     p1 = p2;
     p2 = temp;
}
```

## 递归打印 vector

练习 6.47

```cpp
void output(vector<int> &v)
{
    if (!v.empty())
    {
        auto last = v.back();
        v.pop_back();
        output(v);
        cout << last << " ";
    }
}
```

练习 6.33

```cpp
void output(vector<int> &v, vector<int>::iterator it)
{
    if (it != v.end())
    {
    cout << *it << endl;
    output(v, ++it);  // or output(v, next(it));
    }
}
```

## 检查类型是否为字面值(literal type)

见练习7.55

```cpp
#include <type_traits>

std::is_literal_type<std::string>::value;
```

## 处理string对象中的字符(such as `isdigit`, `isalpha`..)

>3.2.3 p82

| 函数                    | 功能                                      |
| ----------------------- | ----------------------------------------- |
| isalbum(c)              | 当c为字母或数字                           |
| isalpha(c)              | 当c为字母                                 |
| iscntrl(c)              | 当c是控制字符                             |
| isdigit(c)              | 当c为数字                                 |
| isgraph(c)              | 当c不是空格但是可以打印                   |
| islower(c) / isupper(c) | 当c为小写字母 / 大写字母                  |
| isprint(c)              | 当c是可打印字符（是空格或者具有可视形式） |
| ispunct(c)              | 当c是标点符号                             |
| isspace(c)              | 当c是空白时                               |
| isxdigit(c)             | 当c是十六进制数字时                       |
| tolower(c) / toupper(c) | 转为小写 / 大写字母                       |

## 使用 std::boolalpha 在标准输出打印 true, false

>p305 练习9.15等

```cpp
bool isOk()
{
    if(...) return true;
    else return false;
}

std::cout << std::boolalpha << isOk() << std::endl; // 可以打印出 true or false 而不是 0 1
```

## 从数组向 vector 拷贝元素

>p312 练习9.26

可以提供数组首地址，和使用 std::end() 函数获得数组尾地址。

```cpp
int ia[] = {0, 1, 2, 3, 4, 5};
std::vector<int> v(ia, std::end(ia));
// 判断是否为2的倍数使用位运算
if (*iter2 & 0x1) iter2 = lst.erase(iter2);
```

## 迭代器运算符 和 迭代器支持的算术运算

>p96 标准迭代器支持的运算符

| 运算符                          | 含义                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------ |
| *iter                           | 返回迭代器iter所指元素的引用                                                                     |
| iter->name                      | 解引用iter并获取该元素名为name的成员，等价于(*iter).name                                         |
| ++iter                          | 令iter指向容器中的下一个元素                                                                     |
| --iter                          | 令iter指向容器中的上一个元素                                                                     |
| iter1 == iter2 / iter1 != iter2 | 判断两个迭代器是否相等，如果两个迭代器指示的是同一个元素或者同一个容器的尾后迭代器，那么他们相等 |

特别注意：forward_list 迭代器不支持递减运算符。

>p99 string, vector, deque, array 支持的算术运算

| 运算符        | 含义                                                                                                  |
| ------------- | ----------------------------------------------------------------------------------------------------- |
| iter + n      | 迭代器指示的新位置比原来的位置向前移动n个元素，结果为指向容器内的一个元素或者容器结尾元素的下一个位置 |
| iter - n      | 同上                                                                                                  |
| iter += n     | 将iter+n的结果赋给iter                                                                                |
| iter -= n     | 将iter-n的记过赋给iter                                                                                |
| iter1 - iter2 | 同一个容器中两个迭代器之间的距离                                                                      |
| \>, >=, <, <= | 指向同一个容器中迭代器前后位置的比较                                                                  |

## 使用 cout 输出 float, double 指定的精度

>p327 9.5.5 string 和 double 类型数值转换

在使用 cout 输出 float, double 的时候，默认会输出一定精度的数值，（6位）：

```cpp
double d = 3.1415909988;
std::cout << d << std::endl; // 3.14159
double d1 = 3.1415;
std::cout << d1 << std::endl;// 3.1415
```

我们若要输出所有的精度，需要通过 `cout.precision(n)` 进行设定。


>https://stackoverflow.com/questions/45084317/what-is-the-role-of-stdsetprecision-without-stdfixed-in-c  stackoverflow 问题1
>http://www.cplusplus.com/reference/ios/ios_base/precision/

>Using the default floating-point notation, the precision field specifies the maximum number of meaningful digits to display in total counting both those before and those after the decimal point.  
使用默认的 float-point 表达方式，precision 制定了小数点前后表达数字的最大值。

```cpp
double d = 3.1415909988;
std::cout.precision(11);
std::cout << d << std::endl; // 3.1415909988


std::cout.precision(10);
std::cout << std::fixed << d << std::endl; // 3.1415909988
```

注意是否使用 `std::fixed` 是有区别的。

>In both the fixed and scientific notations, the precision field specifies exactly how many digits to display after the decimal point, even if this includes trailing decimal zeros.  
使用 std::fixed 之后，precision 指定了小数点之后显式的位数。不足则补0

```cpp
double item1 = 0.01;
std::cout << std::fixed << item1 << std::endl;
```

## sizeof 求数组大小

>p341 拷贝算法

对于数组 `int a[] = {1, 2, 3, 4, 5}`

- `sizeof(a) = 20;` sizeof 数组名表示数组占用字节大小。

- `sizeof(*a) = 4;` 表示元素占用字节大小。

所以 `sizeof(a)/sizeof(*a)` 代表数组大小。

对于指针 `int *aa = new int[5]`

- `sizeof(aa) = 8;` sizeof 指针名计算指针的大小，8字节，64位。

- `sizeof(*aa) = 4;` 求元素占用字节大小。

## remove_if + erase 删除容器中符合要求的元素

>ex11.4

>ref: https://en.wikipedia.org/wiki/Erase%E2%80%93remove_idiom

`std::remove_if` 函数可以接受一个谓词，将容器中使得谓词为真的元素放到容器的末尾，返回最后一个使得谓词为假的元素的后一个元素迭代器。

`erase` 为容器特有的操作，可以删除范围内的元素。

两个函数配合可以删除容器中符合要求的元素：

```cpp
word.erase(remove_if(word.begin(), word.end(), 
                            [](const char c){return ispunct(c);}), word.end());
```

上述删除了 `word` 这个字符串中的标点符号。

## transform 将 string 中的大写转为小写

>ex12.7

>ref: https://zh.cppreference.com/w/cpp/algorithm/transform

```cpp
string word("Hello, From, The,  World!");
transform(word.begin(), word.end(), word.begin(),
                       [](char c) { return tolower(c); });
```

其中，第三个参数是目标范围的起始。可以等于第一个参数。

## 动态分配对象初始化（`new`）

>chapter 12.1.2 直接管理内存

几种方式：

默认初始化，直接初始化方式（直接构造，列表初始化），值初始化

- 默认初始化

`new` 无法为其分配的对象命名，而是返回一个指向该对象的指针。

`int *pi = new int;`

默认情况下，动态分配的对象是 **默认初始化** 的，即：

- 内置类型或者组合类型的对象的值是未定义的； `int *pi = new int;` pi指向未初始化的 int

- 类类型的对象将用默认构造函数进行初始化； `string *ps = new string;` 初始化为空 string

- 直接初始化方式（构造，列表初始化）

- 传统的构造方式：

```cpp
int *pi = new int(1024); // 传统的构造方式
string *ps = new string(10, '9');
```

- 列表初始化方式：

```cpp
vector<int> *pv = new vector<int>{0, 1, 2, 3, 4, 5, 6};
```

- 值初始化

在类型名之后跟一对括号，即对动态分配的对象值初始化：

```cpp
string *ps1 = new string;  // 默认初始化
string *ps2 = new string();// 值初始化为空 string

int *pi1 = new int;        // 默认初始化，*pi1未定义
int *pi2 = new int();      // 值初始化，*pi2 = 0
```

- 对于定义了自己构造函数的类类型来说(string)，值初始化没有意义：对象都会通过默认构造函数来初始化。

- 对于内置类型：值初始化的内置类型对象有着良好定义的值，默认初始化对象的值是未定义的。

使用括号包围的 **初始化器**：

若提供了一个括号包围的初始化器，就可以使用 auto 来推断我们想要分配对象的类型。

当括号中仅有单一初始化器时才可以使用 auto。

```cpp
auto p1 = new auto(obj);  // p 指向一个与 obj 类型相同的对象

auto p2 = new auto{a, b, c}; // error，括号中只能有单一初始化器
```

## shared_ptr 初始化方式

>chapter 12.1.1 shared_ptr 类 / 12.1.3 shared_ptr 和 new 结合使用

1. 不初始化，默认为空指针

```cpp
shared_ptr<int> p1;
```

2. 使用 `std::make_shared` 函数

```cpp
shared_ptr<string> s1 = make_shared<string>("hello"); // s1 指向一个 string 对象，值为"hello"
shared_ptr<int> s2 = make_shared<int>();  // 值初始化的 string，默认值为 0
```

3. 直接初始化（使用 new 返回的指针初始化智能指针）

```cpp
shared_ptr<int> pi(new int(42));
```

4. 此外：

- `shared_ptr<T> p(q)`：p 管理 **内置指针q** 所指向的对象；

- `shared_ptr<T> p(u)`：p 从 `unique_ptr u` 那里接管了对象的所有权；将 u 置空。

- `shared_ptr<T> p(q, d)`：p 接管了 **内置指针 q** 所指对象的所有权。q 必须能够转换成 `T*` 类型；p 使用可调用对象 d 来代替 `delete`。

- `shared_ptr<T> p(p2, d)`：p 是 **shared_ptr p2** 的拷贝；p 用可调用对象 d 来代替 `delete`。

## `new` 和 `delete` 方法

>chapter 12.2.2 allocator 类

- `new` 方法将 **内存分配** 和 **对象构造** 组合在了一起。

- `delete` 方法将 **对象析构** 和 **内存释放** 组合在一起。

## shared_ptr 的引用和拷贝(问题遗留)

>12.3.2 文本查询程序类的定义

下边一段代码：

![image.png](https://tva1.sinaimg.cn/large/7e197809ly1g8gijp1etyj20op0h4tcd.jpg)

其中 wm 的定义为：

```cpp
map<string, shared_ptr<set<int>>> wm;
```

即：wm 的 value 是一个 shared_ptr。

在途中获取某个 lines 使用了&，表示 lines 是一个 shared_ptr 的引用。当修改 lines 的时候，修改了原数据。

疑惑1：由于 shared_ptr 本身就是一个指针，若不加 & 号，获取的 lines 与获取的引用有何不同？

- 在 map 的 value 中获取 shared_ptr 的直接拷贝：

```cpp
map<string, shared_ptr<set<int>>> mp;

auto res = mp["hello"];

cout << res.use_count() << endl; // 0

res.reset(new set<int>);

cout << res.use_count() << endl; // 1

cout << mp["hello"].use_count() << endl; // 0
```

如上所示，在一个 scope 中，未初始化的 shared_ptr 直接拷贝给 res 之后 res 引用计数为0。res 初始化之后引用计数为1。但是未对原始 shared_ptr 进行初始化。

- 在 map 的 value 中获取 shared_ptr 的引用：

```cpp
map<string, shared_ptr<set<int>>> mp;

auto &res = mp["hello"]; // 0

cout << res.use_count() << endl; // 1

res.reset(new set<int>);

cout << res.use_count() << endl; // 1
cout << mp["hello"].use_count() << endl; // 1
```

获取引用相当于直接对原值进行操作，所以初始化 shared_ptr 之后所有的引用计数都变为1.

疑惑2：map的下标获取值的方法？拷贝？若 value 为 shared_ptr，如何拷贝？

## 类内定义的成员函数默认是内联的，类外定义的成员函数需要加 inline 定义

>chapter6.5.2 内联函数和 constexpr 函数

`inline` 是实现修饰符而不是定义修饰符。

定义在类内的成员函数默认为内联函数，类外的成员函数可以加 `inline` 修饰使其成为内联函数。

友元函数也可以定义在类内，此时它也被隐式定义为内联函数。(effective c++ item 30, page 135)

## 拷贝构造函数的参数为什么一定是引用类型

>chapter13.1.1 拷贝构造函数

拷贝构造函数被用来初始化非引用类类型参数，这一特性解释了为什么拷贝构造函数自己的参数必须是引用类型：

- 若拷贝构造函数的参数不是引用类型，当我们调用拷贝构造函数时，必须拷贝它的实参；

- 为了拷贝实参，我们必须调用拷贝构造函数。

如此循环。

## vector 的元素为类类型时，添加元素、销毁容器时构造函数，析构函数调用情况

>ex13.13 让拷贝构造函数，构造函数，析构函数成员都打印自己函数的名字

类 X 定义：

```cpp
struct X {
    X() { std::cout << "X()" << std::endl; }
    X(const X&) { std::cout << "X(const X&)" << std::endl; }
    ~X() { std::cout << "~X()" << std::endl; }
    X& operator=(const X&) {
        std::cout << "X& operator=(const X&)" << std::endl;
        return *this;
    }
};
```

测试：

```cpp
{
    X x1, x2, x3; // X() X() X()

    std::vector<X> vec{x1, x2}; // X(const X&)*4 两个拷贝到初始化列表中，两个用作拷贝给vector的元素 ~X() ~X() 拷贝到列表结束

    std::cout << "after vector initialization" << ", now the vector capacity is : " << vec.capacity() << std::endl;

    vec.push_back(x3);  // X(const X&)*3 存储空间重新分配，拷贝3次 ~X() ~X() 原来两个位置的元素 x1, x2 调用析构函数

    std::cout << "after push_back x3, now the vector capacity is : " << vec.capacity() << std::endl;

} // 离开作用域 x1, x2, x3 调用析构函数，vector 调用析构函数，其元素全部销毁，~X()*6
```

1. 当定义 x1, x2, x3 的时候，调用构造函数。

2. 使用列表初始化一个 vector 的时候，参数会先拷贝（调用拷贝构造函数），接着将参数当作 vector 元素插入（调用拷贝构造函数）。如上所示，初始化列表为两个参数的时候，共调用了4次拷贝构造函数。初始化完成后，当作参数被拷贝的元素被析构，调用两次析构函数。

3. 此时 `vector.capacity() = 2`，capacity 是指不分配新的内存空间的条件下最多可以保存多少元素。如果再插入元素，需要重新分配空间。

4. 插入了元素 x3，重新分配空间，拷贝三个元素（调用3次拷贝构造函数），将前两个元素析构（调用两次析构函数）。

5. 当离开作用域的时候，vector 被销毁，它的元素也被销毁（调用3次析构函数），x1, x2, x3 被销毁（调用3次析构函数）。

## std::allocator<T> 类型对象拷贝

>ex13.49 为 StrVec 添加一个移动构造函数和移动赋值运算符

StrVec 中的成员为：

```cpp
std::allocator<std::string> alloc;

void chk_n_alloc() {
    if (size() == capacity())
        reallocate();
}

std::pair<std::string *, std::string *> alloc_n_copy(const std::string *,
                                                        const std::string *);

void alloc_n_move(size_t);

void free();

void reallocate();

std::string *elements;   // 指向数组首元素的指针
std::string *first_free; // 指向数组第一个空闲元素
std::string *cap;        // 指向数组尾后位置的指针
```

定义的移动构造函数和移动赋值运算符为：

```cpp
StrVec::StrVec(StrVec &&s) noexcept
    : elements(std::move(s.elements)),
      first_free(std::move(s.first_free)), 
      cap(std::move(s.cap))
{
    s.elements = s.first_free = s.cap = nullptr;
}

StrVec &StrVec::operator=(StrVec &&rhs) noexcept
{
    if (this != &rhs) {
        free(); // 先销毁左侧对象的旧状态
        elements = std::move(rhs.elements);
        first_free = std::move(rhs.first_free);
        cap = std::move(rhs.cap);
        // alloc = std::move(rhs.alloc);
        rhs.elements = rhs.first_free = rhs.cap = nullptr;
    }
    return *this;
}
```

均没有对 `alloc` 进行拷贝或移动。同理拷贝操作也没有对 `alloc` 进行拷贝或移动。

## 一个简单的 string 类的实现

根据第十三章课后题目要求，分为不同的版本。

1. 使用 `std::allocator`, 成员变量分别为 `first`, `last` 的版本：

https://github.com/piaoliangkb/cppprimer/blob/master/chapter13/String.h

2. 参考陈硕的实现，抄一遍学习下：

ref: [A trivial String class that designed for write-on-paper in an interview](https://github.com/chenshuo/recipes/blob/fcf9486f5155117fb8c36b6b0944c5486c71c421/string/StringTrivial.h)

https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/String.h

## 派生类的析构函数只负责销毁自己的成员

>chapter 15.7.3 派生类的拷贝控制成员

- 派生类的拷贝和移动构造函数在拷贝和移动自有成员的同时，也要拷贝和移动基类部分的成员。

- 派生类赋值运算符必须为其基类部分的成员赋值。

- 析构函数只负责销毁派生类自己分配的资源，派生类对象的基类部分是自动销毁的。

## 派生类只能在初始值列表中使用基类的构造函数

>p555

若要使用拷贝或者移动构造函数，我们必须在构造函数的初始值列表中，显式地调用该构造函数。

```cpp
Bulk_quote(const Bulk_quote &rhs)
    : Quote(rhs), quantity(rhs.quantity), discount(rhs.discount) 
{
    // Quote(rhs); error
    quantity = rhs.quantity;
    discount = rhs.discount;
    std::cout << "[call func] Bulk_quote(const Bulk_quote&)" << std::endl;
}
```

## 类成员的初始化只能使用等号或者花括号，不能用圆括号

>chapter15.8.1 编写 Basket 类
>
>https://www.zhihu.com/question/267652570/answer/327087344
>
>[most vexing parse](https://en.wikipedia.org/wiki/Most_vexing_parse)


代码如下：

```cpp
class Basket {
public:
    void add_item(const std::shared_ptr<Quote> &sale) {
        items.insert(sale);
    }

    // 打印每本书的总价和 Basket 中所有书的总价
    double total_receipt(std::ostream&) const;

private:
    static bool compare(const std::shared_ptr<Quote> &lhs,
                        const std::shared_ptr<Quote> &rhs) {
                            return lhs->isbn() < rhs->isbn();
                        }
    
    // 传递 compare 参数的时候不可使用花括号，
    // 否则 items 会被当成函数
    // std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items(compare); error
    std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items{compare};
};
```

其中 items 的声明若写为 `std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items(compare);` 则会报错，items 会被认为是一个函数。
 
同理：

```cpp
struct A {
    static const int x(0);
};
```

上述写法 x 会被当成一个函数。只能写成 `static const int x = 0;` 或者 `static const int x{0};`

- 在类外，初始化可以使用圆括号，例如 `chapter11.2.2`：

```cpp
bool compareISBN(const Sales_data& lhs, const Sales_data& rhs)
{
    return lhs.isbn() < rhs.isbn();
}

multiset<Sales_data, decltype(compareISBN)*> bookstore(compareISBN);
```

## 多态(polymorphism)

>[c++ primer 15.3 虚函数](https://github.com/piaoliangkb/cppprimer/tree/master/chapter15#%E5%A4%9A%E6%80%81-polymorphism)
>
>https://zhuanlan.zhihu.com/p/37340242
>
>https://en.wikipedia.org/wiki/Polymorphism_(computer_science)

在编程语言和类型论中，多态（英语：polymorphism）指为不同数据类型的实体提供统一的接口。

>多态可分为变量多态与函数多态。
>
>- 变量多态是指：基类型的变量（对于C++是引用或指针）可以被赋值基类型对象，也可以被赋值派生类型的对象。
>
>- 函数多态是指，相同的函数调用界面（函数名与实参表），传送给一个对象变量，可以有不同的行为，这视该对象变量所指向的对象类型而定。因此，变量多态是函数多态的基础。

C++ 中的多态包括 overload（重载，函数重载） 和 override（重写）。

- overload，也可以看做静态多态(static polymorphism)、编译时多态，通过重载函数实现，具体调用函数在编译器决定。

- override，也可以看作动态多态(dynamic polymorphism)、运行时多态，通过类的虚函数实现，子类重写父类的虚函数，在程序运行过程中动态地决定调用哪个函数。

## extern 和 static

>https://www.zhihu.com/question/265415085/answer/293495989
>
>推荐使用 namespace?

- static

static 修饰的变量只存在于当前编译单元。

若 `static int a;` 写在一个头文件中，需要文件都包含了该头文件，那么每个文件都可以使用 `a`，但是每个 `a` 都是独立存在的，需要独立定义。

- extern

extern 修饰的变量存在，但是可能不在当前的编译单元，在链接的时候寻找定义。

包含 extern 声明的头文件的，共用这个全局变量。

例如：`extern int a; `如果在连接的时候，没有在任何地方发现 `a` 的定义，那么链接报错。

例子：

[static_and_extern.h](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/static_and_extern.h)

[sae_test1.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/sae_test1.cpp)

[sae_test2.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/sae_test2.cpp)

[sae_test3.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/sae_test3.cpp)

[sae_test4.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/sae_test4.cpp)

## RTTI(Run-Time Type Identification) and typeid

详细内容见 [C++Primer chapter 19.2]

C++ 提供了运行时类型识别(RTTI)，可以通过 `typeid` 操作符的得到动态的类型信息：

```cpp
class Book {
public:
    Book() {
    }
    virtual void func() {
        std::cout << "Book::func()" << std::endl;
    }
};

class Cppprimer : public Book {
public:
    Cppprimer() {
    }
    void func() override {
        std::cout << "Cppprimer::func()" << std::endl;
    }
};

int main()
{
    Cppprimer cpp;
    Book& bk = cpp;

    bk.func();
    std::cout << typeid(bk).name() << std::endl;  // Cppprimer

    Book* bk1 = &cpp;

    bk1->func();
    std::cout << typeid(*bk1).name() << std::endl; // Book
}
/*
Cppprimer::func()
9Cppprimer
Cppprimer::func()
9Cppprimer
*/
```

## pimpl idiom(pointer to implementation)

>effective c++ item25, 28
>
>参考：https://en.cppreference.com/w/cpp/language/pimpl
>
>https://www.geeksforgeeks.org/pimpl-idiom-in-c-with-examples/

pimpl 的全称为 pointer to implementation，即使用指针指向实现。含义就是将一个类的实现细节从类中移除，使用指针指向一个单独的类，在这个单独的类中实现原类的实现细节。

- 可以用来减少编译依赖。

>When changes are made to a header file, all sources including it needs to be recompiled. In large projects and libraries, it can cause build time issues due to the fact that even when a small change to the implementation is made everyone has to wait sometime until they compile their code. One way to solve this problem is by using the PImpl Idiom, which hides the implementation in the headers and includes an interface file which compiles instantly.

当某个头文件改变，所有包含这个头文件的源码都需要重新编译。使用 pimpl idiom 可以将类的具体实现从头文件中隐藏，放到一个单独的类中，那么当该实现更改的时候只需要重新编译这个类。

一个大体实现：

```cpp
// -------- Widget.h --------
class Widget {
public:
    // ...
private:
    struct impl;  // 实现类的前置声明
    std::unique_ptr<impl> pimpl;
};

// -------- Widget.cpp --------
struct Widget::impl {
    // ...
};
```

例子：

[User.h](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/User.h)
[User.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/User.cpp)
[test_User.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/some_tips/test_User.cpp)

```cpp
// just compile cpp files
clang++ -std=c++11 User.cpp test_User.cpp
```

使用 pimpl 的优势：

- 编译时间减少：只有实现部分的文件会重新编译，而不是修改类的 private 部分后重新编译整个文件。

- 数据封装：可以轻易的将内部的技术实现细节隐藏。

缺点：

- 内存管理：和将 private 部分内置于类中对比，使用 pimpl 实现的类消耗的内存增加。

- 维护成本：增添了一个类，使用时需要调用指针，使得维护工作变得复杂。

- 继承：被隐藏的实现是 private 成员，无法被继承。（[C++Primer chapter 15.2.2 静态成员与继承](https://github.com/piaoliangkb/cppprimer/tree/master/chapter15#%E9%9D%99%E6%80%81%E6%88%90%E5%91%98%E4%B8%8E%E7%BB%A7%E6%89%BF)）

## operator* operator+ 返回值是否需要为 const

根据 Effective c++: item03，对于有理数的 `operator*` 函数，定义为 `const Rational operator*(const Rational &lhs, const Rational &rhs);` 可以避免发生如下的情况：

```cpp
(A * B) = C;
// or
if (A * B = C) {
    // ...
}
```

那么 `operator+` 的返回值需要定义为 const 吗，为了防止发生 `(A + B) = C;` 的情况？

c++ primer p497 示例程序：Sales_data 的 operator+ 程序：返回值不为 const

```cpp
Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs) {
    Sales_data sum = lhs;
    sum += rhs;
    return sum;
}
```

## cin, cin.get, getline() 方法（对中止符的处理）(如何判断读入 enter)

>cs106b assignment1: soundex.cpp
>
>ref: https://stackoverflow.com/questions/29630513/difference-between-cin-and-cin-get-for-char-array

定义一个字符串，使用 `cin >> input` 来进行输入，在开头遇到结束符会忽略（空格，回车，制表），下一次遇到结束符号会结束输入。注意：`cin >>` 并不会丢弃结束符，仍然在缓冲区中。

```cpp
char m, n;
cin >> m;   // 输入结束后换行
cin.get(n); // n 将读到换行符
```

使用 `cin.get(input)` 进行输入，可以读取空格，但是遇到回车符会停止，不会丢弃回车符号 (leaves end-of-line character in stream)。读取单个字符的时候可以读取到回车符。通常用来吸收缓冲区中的回车符。例如，读取一行的 256个字符并且把回车符号消掉：

```cpp
cin.get(input, 256); cin.get();
// equals to
cin.getline(input, 256);
```

使用 `getline(cin, input)` 会读取到一行的内容，遇到回车符终止，但会清理掉缓冲区中的回车符。

判断是否读入一个 enter：

```cpp
getline(cin, input);
if (input == "") {
    cout << "You input a enter(return)" << endl;
}
```

## 遍历 map

- 方式1: 使用迭代器和 `iter->first, iter->second`

```cpp
for (auto it = m.begin(); it != m.end(); ++it)
{
    cout << it->first << " " << it->second << endl;
}
// or use while
auto it = m.begin();
while (it != m.end()) {
    cout << it->first << " " << it->second << endl;
    ++it;
}
```

- 方式2: for loop in c++11

```cpp
for (const auto &item: m) {
    cout << item.first << " " << item.second << endl;
}
```

- 方式3: decomposition declarations in c++17

```cpp
for (const auto& [key, val]: m) {
    cout << key << " " << val << endl;
}
```

## 遍历 map 时删除元素

>cs106b assgnment2 use `map.remove(key)` in an iterator

遍历的时候不能删除东西，如果一定要删，使用 `map.erase(iter)` 方法，该方法会返回删除位置之后一个迭代器的位置。

```cpp
map<string, string> m = {
    {"Hello", "world"},
    {"Python", "list"},
    {"golang", "google"},
};

auto it = m.begin();

while (it != m.end()) {
    if (it->first == "Python") {
        it = m.erase(it);
    }
    else {
        ++it;
    }
}
```

>How to do this in Python: https://stackoverflow.com/questions/1207406/how-to-remove-items-from-a-list-while-iterating

## 反向迭代器 reverse_itreator

>Remove punctuation from start and end of a string
>
>[cppprimer](https://github.com/piaoliangkb/cppprimer/blob/52c3df4f2bd993406573de6e13be209b16f286ba/chapter10/README.md#1043-%E5%8F%8D%E5%90%91%E8%BF%AD%E4%BB%A3%E5%99%A8) 
>
>[cppreference](https://en.cppreference.com/w/cpp/iterator/reverse_iterator/base)


反向迭代器需要递减运算符，除了 forward_list 之外，标准容器上的其他迭代器都支持递增和递减运算。

例如，找出一个字符串最后一个不是 数字 的字符，使用 `isdigit` 函数：

```cpp
string s = "       aksdjaj     ijijdsd123";
auto iter = find_if_not(s.rbegin(), s.rend(), ::isdigit);
cout << *iter << endl;  // d
cout << *(iter.base()) << endl; // 1
```

上述代码从字符串 s 结尾找到了第一个不为数字的字符 `d`, 通过对迭代器解引用，输出了字符 `d`.

使用迭代器的 `iter.base()` 方法，迭代器将会指向字符 `1`, 输出了字符 `1`.

实际上：

- reverse iterator 解引用会输出 previous element. 实际迭代器指向的是解引用项之后的一项。

- 使用 `reverse_iterator.base()` 方法，可以获得 **正向迭代器**, 指向 reverse iterator 恰好指向的内容。

    例如：

    >https://stackoverflow.com/questions/16609041/c-stl-what-does-base-do

    ```
                           i, *i
                             |
    -      0     1     2     3     4     -
                       |     | 
                       *ri   ri
    ```

- 从正向迭代器构造一个反向迭代器，反向迭代器会指向和正向迭代器相同的位置，但是反向迭代器解引用的数值是该位置的前一个数。

    例如：

    ```cpp
    std::vector<int> v = {0, 1, 2, 3, 4, 5};
    
    auto it = v.begin() + 3;
    std::reverse_iterator<std::vector<int>::iterator> rev_it(it);
    
    cout << *it;  // 3
    cout << *rev_it;  // 2
    cout << *(rev_it.base());  // 3
    cout << *(rev_it.base() - 1);  // 2
    ```

## 去除 string 首尾的标点符号 (punctuation)

>https://www.reddit.com/r/cpp_questions/comments/3ssstt/removing_punctuation_from_the_start_and_end_of_a/

使用 `cctype` 头文件的 `ispunct` 方法。

- 方法1:

去除开头的标点符号：

```cpp
s.erase(s.begin(), find_if_not(s.begin(), s.end(), ::ispunct));
```

去除结尾的标点符号：

这里使用了反向迭代器来去除结尾的标点符号。从结尾开始找到第一个不是标点的位置，使用 `base()` 方法转换为正向迭代器，删除从该位置到结尾的字符。

```cpp
s.erase(find_if_not(s.rbegin(), s.rend(), ::ispunct).base(), s.end());
```

测试：

```cpp
string s = ",.,.!!aksdjaj!!!@!#!#!l     ijijdsd123...((*!";
s.erase(s.begin(), find_if_not(s.begin(), s.end(), ::ispunct));
s.erase(find_if_not(s.rbegin(), s.rend(), ::ispunct).base(), s.end());
cout << s << endl;
```

输出：`aksdjaj!!!@!#!#!l     ijijdsd123`

- 方法2:

去除开头的字符串：

```cpp
while (::ispunct(s.front())) {
    s.erase(s.begin());
}
```

去除结尾的字符串：

```cpp
while (::ispunct(s.back()))  {
    s.pop_back();
}
```

## this pointer

>https://www.bogotobogo.com/cplusplus/this_pointer.php

this pointer 保存了 class 实例的地址，从而允许类的成员函数访问类的成员。

假定我们定义了 `class A`，创建了一个类 `A` 的实例 `objA`。`class A` 又一个非静态成员函数 `f()`。

当调用函数 `objA.f()` 的时候，函数 `f()` 储存了 `objA` 的地址：

```cpp
// 定义函数 A::f()
void A::f() {
    // ...
}

// 实际上应该是
void A::f(A* const this) {
    // ...
}
```

给出一个实际的例子：

```cpp
class Cart {
public:
    Cart(int item) {
        this->total = item;
    }

    Cart& addItem(int itemPrice) {
        total += itemPrice;
        return *this;
    }

private:
    int total;
}
```

首先创建一个 `Cart` 实例 `myCart`:

```cpp
Cart myCart(10);
```

当调用函数 `myCart.addItem(100)` 的时候，编译器将我们的函数转换成了：

```cpp
myCart.addItem(&myCart, 100);
```

该 `addItem` 函数实际的定义应该是：

```cpp
Cart& addItem(Cart* const this, int itemPrice) {
    this->total += itemPrice;
    return *this;
}
```

## 什么时候使用类的 this pointer

>https://stackoverflow.com/questions/993352/when-should-i-make-explicit-use-of-the-this-pointer

通常来说不需要使用 this pointer, 正常的访问类的成员变量，`this->` 是隐式的。如果 local variable 和类中已经存在的成员重名的话，需要使用 this->member 来表明要使用的是类的成员。

例如对于类中的一个函数：

```cpp
class A
{
public:
    int a;

    void f() {
        a = 4;
        int a = 5;
        cout << a << endl;
        cout << this->a << endl;
    }
};
```

另一个重名的示例：

```cpp
class A{
public:
    void setx(int x){
        this->x = x;
    }
private:
    int x;
}
```

然而在类的构造函数中使用 initializer list (initialization list) 初始化类成员的时候不需要考虑重名情况下加 this 指针的问题：

```cpp
class A {
public:
    // needed to add this pointer
    A(int num, string str)  {
        this->num = num;
        this->str = str;
    };

    // initialize A::num = num, A::str = str
    A(int num, string str): num(num), str(str) {
    };

private:
    int num;
    string str;
};
```


## 二分法实现 lower_bound 和 upper_bound

在有序数组中

- lower_bound：返回最左侧的 x >= target 的 index

- upper_bound：返回最左侧的 x > target 的 index

可以使用二分查找来实现

>参考：https://leetcode-cn.com/problems/search-insert-position/

具体实现见文件夹下的 [bound.cpp](https://github.com/piaoliangkb/cppprimer/blob/master/other_notes/other_notes/some_tips/bound.cpp)

具体的想法就是两个 `target` 和 `vector[mid]` 的判断条件，加入等号判断来左右逼近。注意退出 while 条件时 low 和 high 的关系。

```cpp
int lower_bd(vector<int> &v, int target) {
    int low = 0, high = v.size() - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (target > v[mid]) {
            low = mid + 1;
        }
        // 如果 target 还小于 mid，就让 high 一直向左逼近
        // 一直到最后，high 会到 target 的左侧，
        // 退出循环时，low = high + 1 所在的位置就是最小的等于 target 的
        if (target <= v[mid]) {
            high = mid - 1;
        }
    }
    return low;
}

int upper_bd(vector<int> &v, int target) {
    int low = 0, high = v.size() - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        // 如果 target 比 mid 大，就让 low 一直向右逼近
        // 一直到最后，low 会到 target 的右侧
        // 恰好是第一个大于 target 的位置
        if (target >= v[mid]) {
            low = mid + 1;
        }
        if (target < v[mid]) {
            high = mid - 1;
        }
    }
    return low;
}
```

## 类没有任何变量和函数/类只含有构造函数和析构函数/类只有虚函数 sizeof 各占多少空间

>剑指offer p23

具体见代码 `sizeof_class.cpp`

对于一个空类，它的实例占一个字节的空间。由编译器决定。为了每个实例在内存中都有一个独一无二的地址加以区分，**编译器给每个空类隐含的加一个字节**。

对于只有构造函数和析构函数的类，实例占一个字节的空间。函数的地址和类的实例无关。

只有一个虚析构函数的类，实例有一个虚函数表指针。在 64 位的机器上，一个指针占 8 字节的空间。

```cpp
#include <iostream>

using namespace std;

class A{

};

class B {
public:
    B(){}
    ~B(){}
};

class C {
public:
    C(){}
    virtual ~C() {}
};

int main() {
    cout << "Sizeof a empty class = " << sizeof(A) << endl;  // 1 bytes
    A a;
    cout << "Empty class instace sizeof = " << sizeof(a) << endl; // 1 bytes
    A aa;
    // address of two different instances are different
    cout << "Address of instance a: " << &a << endl;
    cout << "Address of instance aa: " << &aa << endl;

    cout << "Sizeof a class with ctor, dtor = " << sizeof(B) << endl;  // 1 bytes
    B b;
    cout << "Class with empty ctor, dtor sizeof = " << sizeof(b) << endl;  // 1 bytes

    cout << "Sizeof a class with virtual function = " << sizeof(C) << endl;  // 8 bytes
    C c;
    cout << "Class with virtual dtor, sizeof = " << sizeof(c) << endl; // 8 bytes
}
```

程序输出为：

```
Sizeof a empty class = 1
Empty class instace sizeof = 1
Address of instance a: 0x7ffee9c4d348
Address of instance aa: 0x7ffee9c4d340
Sizeof a class with ctor, dtor = 1
Class with empty ctor, dtor sizeof = 1
Sizeof a class with virtual function = 8
Class with virtual dtor, sizeof = 8
```

## sizeof vector

>https://stackoverflow.com/questions/34024805/c-sizeof-vector-is-24
>
>https://www.zhihu.com/question/34955591

sizeof 是一个运算符，编译期间进行运算。用来获得一个类型或者变量占用的真实字节大小。

对一个 vector 使用 sizeof 运算符，在 64 bits 机器上得到的结果是 24 bytes:

```cpp
int main() {
    vector<int> a;
    cout << sizeof(a) << endl;  // 24

    a.push_back(1);
    cout << sizeof(a) << endl;  // 24

    a.push_back(2);
    cout << sizeof(a) << endl;  // 24

    return 0;
}
```

The 24 size you see can be explained as 3 pointers (each pointer is 8 bytes in size on 64-bit architectures; so you have 3 x 8 = 24 bytes):

- begin of vector

- end of vector (size，或者用一个 size_t 代替指针)

- end of reserved memory for vector (capacity，或者用一个 size_t 来代替指针)

此外 vector 对象还有一个 allocator (可能少于 8 个字节)，但是 allocator 被隐藏了。

## convert double/float to string without trailing zeros

将 double 或者 float 转化成 string 输出，如果直接使用 `to_string()` 方法的话，会保留浮点数的后置0。例如：

```cpp
#include <iostream>
#include <sstream>

using namespace std;

int main() {
    double d = 3.13;
    float f = 2.1;

    cout << "d string is: " << to_string(d) << ", f string is: " << to_string(f) << endl;
}
// d string is: 3.130000, f string is: 2.100000
```

可以创建一个 `stringstream` 向该 stream 写入浮点数，然后使用 `stringstream.str()` 方法返回 stringstream 中存储的字符串的拷贝，输出没有后置 0 的字符串：

```cpp
#include <iostream>
#include <sstream>

using namespace std;

int main() {
    double d = 3.13;
    float f = 2.1;

    cout << "d string is: " << to_string(d) << ", f string is: " << to_string(f) << endl;

    stringstream ss;
    // 向 stringstream 写入内容
    ss << d;
    cout << "d string without trailing zeros is: " << ss.str() << endl;
    // 继续向 stringstream 写入内容，之前写入的内容仍然存在
    ss << f;
    cout << "f string without trailing zeros is: " << ss.str() << endl;
}
// d string without trailing zeros is: 3.13
// f string without trailing zeros is: 3.132.1
```

注意，第二次向 stringstream 输出内容时，第一次的东西并没有变动。所以不能复用，如果要复用的话，需要删除 stringstream 中上一次写入的内容。

如果想要重新使用该 stringstream，需要删除之前的内容，删除的方式就是设置：

>https://stackoverflow.com/questions/20731/how-do-you-clear-a-stringstream-variable

```cpp
ss.str("");
```

## std::unordered_map 为什么慢

- youtube 讲解：https://www.youtube.com/watch?v=nx5g5bwtUuA

- Google 开源 flat_hash_map: https://github.com/abseil/abseil-cpp/blob/master/absl/container/flat_hash_map.h

- Folly F14Map: https://github.com/facebook/folly/blob/master/folly/container/F14Map.h


## std::thread 作为 std::unordered_map 的 value

https://www.zhihu.com/question/443554916

`std::thread` 不支持复制和赋值，可以使用 `std::move` 移动。

解决方案：

1. `*thread` or `std::unique_ptr` 作为 map 的 value

```cpp

```

2. `thread` 作为 map 的 value 使用 `std::move`

```cpp
std::unordered_map<std::string, std::thread> m;
std::thread t{f, "hello"};
m["myfunc"] = std::move(t);

m["myfunc"].join();
```

3. 使用 lambda 函数隐式构造

## pair<T, T> 作为 unordered_map, unordered_set 的 key

unordered_map, unordered_set 需要 hash function，但是 pair 类型并不提供 hash 函数，所以需要自己定义。

```cpp
struct SimpleHash {
    size_t operator()(const std::pair<int, int>& p) const {
        return p.first ^ p.second;
    }
};

std::unordered_set<std::pair<int, int>, SimpleHash> S;
S.insert(std::make_pair(0, 1));
```

- https://stackoverflow.com/questions/21288345/unordered-set-of-pairs-compilation-error

- https://stackoverflow.com/questions/30419681/why-cant-i-use-pair-as-key-of-unordered-set-unordered-map

为什么 set, map 可以使用 pair 作为 key?

set, map 内置的数据结构为红黑树，没有使用 hashtable.

- https://gist.github.com/justinmeiners/57f38bddae9029db3c6401fae113bd7c

- https://stackoverflow.com/questions/5288320/why-is-stdmap-implemented-as-a-red-black-tree