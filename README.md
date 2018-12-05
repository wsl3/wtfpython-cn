<p align="center"><img src="/images/logo.png" alt=""></p>
<h1 align="center">What the f*ck Python! 🐍</h1>
<p align="center">An interesting collection of surprising snippets and lesser-known Python features.</p>

[![WTFPL 2.0][license-image]][license-url] [![Commit id][commit-image]][commit-url]


Python, being a beautifully designed high-level and interpreter-based programming language, provides us with many features for the programmer's comfort. But sometimes, the outcomes of a Python snippet may not seem obvious to a regular user at first sight.

Here is a fun project to collect such tricky & counter-intuitive examples and lesser-known features in Python, attempting to discuss what exactly is happening under the hood!

While some of the examples you see below may not be WTFs in the truest sense, but they'll reveal some of the interesting parts of Python that you might be unaware of. I find it a nice way to learn the internals of a programming language, and I think you'll find them interesting as well!

If you're an experienced Python programmer, you can take it as a challenge to get most of them right in first attempt. You may be already familiar with some of these examples, and I might be able to revive sweet old memories of yours being bitten by these gotchas :sweat_smile:

If you're a returning reader, you can learn about the new modifications [here](https://github.com/satwikkansal/wtfpython/releases/).

So, here we go...

# Table of Contents
<!-- TOC -->

- [Table of Contents](#table-of-contents)
- [Structure of the Examples](#structure-of-the-examples)
- [Usage](#usage)
- [👀 Examples](#👀-examples)
    - [Section: Strain your brain!](#section-strain-your-brain)
        - [> Strings can be tricky sometimes/微妙的字符串 *](#-strings-can-be-tricky-sometimes微妙的字符串-)
        - [> Time for some hash brownies!/是时候来点蛋糕了!](#-time-for-some-hash-brownies是时候来点蛋糕了)
        - [> Return return everywhere!/到处返回！](#-return-return-everywhere到处返回)
        - [> Deep down, we're all the same./本质上,我们都一样. *](#-deep-down-were-all-the-same本质上我们都一样-)
        - [> For what?/为什么?](#-for-what为什么)
        - [> Evaluation time discrepancy/执行时机差异](#-evaluation-time-discrepancy执行时机差异)
        - [> `is` is not what it is!/出人意料的`is`!](#-is-is-not-what-it-is出人意料的is)
        - [> A tic-tac-toe where X wins in the first attempt!/一蹴即至!](#-a-tic-tac-toe-where-x-wins-in-the-first-attempt一蹴即至)
        - [> The sticky output function/麻烦的输出](#-the-sticky-output-function麻烦的输出)
        - [> `is not ...` is not `is (not ...)`/`is not ...` 不是 `is (not ...)`](#-is-not--is-not-is-not-is-not--不是-is-not-)
        - [> The surprising comma/意外的逗号](#-the-surprising-comma意外的逗号)
        - [> Backslashes at the end of string/字符串末尾的反斜杠](#-backslashes-at-the-end-of-string字符串末尾的反斜杠)
        - [> not knot!/别纠结!](#-not-knot别纠结)
        - [> Half triple-quoted strings/三个引号](#-half-triple-quoted-strings三个引号)
        - [> Midnight time doesn't exist?/不存在的午夜?](#-midnight-time-doesnt-exist不存在的午夜)
        - [> What's wrong with booleans?/布尔你咋了?](#-whats-wrong-with-booleans布尔你咋了)
        - [> Class attributes and instance attributes/类属性和实例属性](#-class-attributes-and-instance-attributes类属性和实例属性)
        - [> yielding None/生成 None](#-yielding-none生成-none)
        - [> Mutating the immutable!/强人所难](#-mutating-the-immutable强人所难)
        - [> The disappearing variable from outer scope/消失的外部变量](#-the-disappearing-variable-from-outer-scope消失的外部变量)
        - [> When True is actually False/真亦假](#-when-true-is-actually-false真亦假)
        - [> From filled to None in one instruction.../从有到无...](#-from-filled-to-none-in-one-instruction从有到无)
        - [> Subclass relationships/子类关系 *](#-subclass-relationships子类关系-)
        - [> The mysterious key type conversion/神秘的键型转换 *](#-the-mysterious-key-type-conversion神秘的键型转换-)
        - [> Let's see if you can guess this?/看看你能否猜到这一点?](#-lets-see-if-you-can-guess-this看看你能否猜到这一点)
    - [Section: Appearances are deceptive!](#section-appearances-are-deceptive)
        - [> Skipping lines?/跳过一行?](#-skipping-lines跳过一行)
        - [> Teleportation/空间移动 *](#-teleportation空间移动-)
        - [> Well, something is fishy.../嗯, 有些可疑...](#-well-something-is-fishy嗯有些可疑)
    - [Section: Watch out for the landmines!](#section-watch-out-for-the-landmines)
        - [> Modifying a dictionary while iterating over it/迭代字典时的修改](#-modifying-a-dictionary-while-iterating-over-it迭代字典时的修改)
        - [> Stubborn `del` operator/坚强的 `del` *](#-stubborn-del-operator坚强的-del-)
        - [> Deleting a list item while iterating/迭代列表时删除元素](#-deleting-a-list-item-while-iterating迭代列表时删除元素)
        - [> Loop variables leaking out!/循环变量泄漏!](#-loop-variables-leaking-out循环变量泄漏)
        - [> Beware of default mutable arguments!/当心默认的可变参数!](#-beware-of-default-mutable-arguments当心默认的可变参数)
        - [> Catching the Exceptions](#-catching-the-exceptions)
        - [> Same operands, different story!](#-same-operands-different-story)
        - [> The out of scope variable](#-the-out-of-scope-variable)
        - [> Be careful with chained operations](#-be-careful-with-chained-operations)
        - [> Name resolution ignoring class scope](#-name-resolution-ignoring-class-scope)
        - [> Needle in a Haystack](#-needle-in-a-haystack)
    - [Section: The Hidden treasures!](#section-the-hidden-treasures)
        - [> Okay Python, Can you make me fly? *](#-okay-python-can-you-make-me-fly-)
        - [> `goto`, but why? *](#-goto-but-why-)
        - [> Brace yourself! *](#-brace-yourself-)
        - [> Let's meet Friendly Language Uncle For Life *](#-lets-meet-friendly-language-uncle-for-life-)
        - [> Even Python understands that love is complicated *](#-even-python-understands-that-love-is-complicated-)
        - [> Yes, it exists!](#-yes-it-exists)
        - [> Inpinity *](#-inpinity-)
        - [> Mangling time! *](#-mangling-time-)
    - [Section: Miscellaneous](#section-miscellaneous)
        - [> `+=` is faster](#--is-faster)
        - [> Let's make a giant string!](#-lets-make-a-giant-string)
        - [> Explicit typecast of strings](#-explicit-typecast-of-strings)
        - [> Minor Ones](#-minor-ones)
- [Contributing](#contributing)
- [Acknowledgements](#acknowledgements)
- [🎓 License](#🎓-license)
    - [Help](#help)
    - [Want to surprise your geeky pythonist friends?](#want-to-surprise-your-geeky-pythonist-friends)
    - [Need a pdf version?](#need-a-pdf-version)
    - [Follow Commit](#follow-commit)

<!-- /TOC -->

# Structure of the Examples

All the examples are structured like below:

> ### > Some fancy Title *
> The asterisk at the end of the title indicates the example was not present in the first release and has been recently added.
>
> ```py
> # Setting up the code.
> # Preparation for the magic...
> ```
>
> **Output (Python version):**
> ```py
> >>> triggering_statement
> Probably unexpected output
> ```
> (Optional): One line describing the unexpected output.
>
>
> #### 💡 Explanation:
>
> * Brief explanation of what's happening and why is it happening.
>   ```py
>   Setting up examples for clarification (if necessary)
>   ```
>   **Output:**
>   ```py
>   >>> trigger # some example that makes it easy to unveil the magic
>   # some justified output
>   ```

**Note:** All the examples are tested on Python 3.5.2 interactive interpreter, and they should work for all the Python versions unless explicitly specified in the description.

# Usage

A nice way to get the most out of these examples, in my opinion, will be just to read the examples chronologically, and for every example:
- Carefully read the initial code for setting up the example. If you're an experienced Python programmer, most of the times you will successfully anticipate what's going to happen next.
- Read the output snippets and,
  + Check if the outputs are the same as you'd expect.
  + Make sure if you know the exact reason behind the output being the way it is.
    - If no, take a deep breath, and read the explanation (and if you still don't understand, shout out! and create an issue [here](https://github.com/satwikkansal/wtfPython)).
    - If yes, give a gentle pat on your back, and you may skip to the next example.

PS: You can also read WTFpython at the command line. There's a pypi package and an npm package (supports colored formatting) for the same.

To install the npm package [`wtfpython`](https://www.npmjs.com/package/wtfpython)
```sh
$ npm install -g wtfpython
```

Alternatively, to install the pypi package [`wtfpython`](https://pypi.python.org/pypi/wtfpython)
```sh
$ pip install wtfpython -U
```

Now, just run `wtfpython` at the command line which will open this collection in your selected `$PAGER`.

---

# 👀 Examples


## Section: Strain your brain!

### > Strings can be tricky sometimes/微妙的字符串 *

1\.
```py
>>> a = "some_string"
>>> id(a)
140420665652016
>>> id("some" + "_" + "string") # 注意两个的id值是相同的.
140420665652016
```

2\.
```py
>>> a = "wtf"
>>> b = "wtf"
>>> a is b
True

>>> a = "wtf!"
>>> b = "wtf!"
>>> a is b
False

>>> a, b = "wtf!", "wtf!"
>>> a is b
True
```

3\.
```py
>>> 'a' * 20 is 'aaaaaaaaaaaaaaaaaaaa'
True
>>> 'a' * 21 is 'aaaaaaaaaaaaaaaaaaaaa'
False
```

很好理解, 对吧?

#### 💡 说明:
- 这些行为是由于 Cpython 在编译优化时, 某些情况下会尝试使用已经存在的不可变对象而不是每次都创建一个新对象. (这种行为被称作字符串的驻留[string interning])
- 发生驻留之后, 许多变量可能指向内存中的相同字符串对象. (从而节省内存)
- 在上面的代码中, 字符串是隐式驻留的. 何时发生隐式驻留则取决于具体的实现. 这里有一些方法可以用来猜测字符串是否会被驻留:
  - 所有长度为 0 和长度为 1 的字符串都被驻留.
  - 字符串在编译时被实现 (`'wtf'` 将被驻留, 但是 `''.join(['w', 't', 'f']` 将不会被驻留)
  - 字符串中只包含字母，数字或下划线时将会驻留. 所以 `'wtf!'` 由于包含 `!` 而未被驻留. 可以在[这里](https://github.com/python/cpython/blob/3.6/Objects/codeobject.c#L19)找到 CPython 对此规则的实现.

    <img src="/images/string-intern/string_intern.png" alt="">

- 当在同一行将 `a` 和 `b` 的值设置为 `"wtf!"` 的时候, Python 解释器会创建一个新对象, 然后同时引用第二个变量. 如果你在不同的行上进行赋值操作, 它就不会“知道”已经有一个 `wtf！` 对象 (因为 `"wtf!"` 不是按照上面提到的方式被隐式驻留的). 它是一种编译器优化, 特别适用于交互式环境.
- 常量折叠(constant folding) 是 Python 中的一种 [窥孔优化(peephole optimization)](https://en.wikipedia.org/wiki/Peephole_optimization) 技术. 这意味着在编译时表达式 `'a'*20` 会被替换为 `'aaaaaaaaaaaaaaaaaaaa'` 以减少运行时的时钟周期. 只有长度小于 20 的字符串才会发生常量折叠. (为啥? 想象一下由于表达式 `'a'*10**10` 而生成的 `.pyc` 文件的大小). 相关的源码实现在[这里](https://github.com/python/cpython/blob/3.6/Python/peephole.c#L288).


---

### > Time for some hash brownies!/是时候来点蛋糕了!
* hash brownie指一种含有大麻成分的蛋糕, 所以这里是句双关

1\.
```py
some_dict = {}
some_dict[5.5] = "Ruby"
some_dict[5.0] = "JavaScript"
some_dict[5] = "Python"
```

**Output:**
```py
>>> some_dict[5.5]
"Ruby"
>>> some_dict[5.0]
"Python"
>>> some_dict[5]
"Python"
```

"Python" 消除了 "JavaScript" 的存在?

#### 💡 说明:

* Python 字典通过检查键值是否相等和比较哈希值来确定两个键是否相同.
* 具有相同值的不可变对象在Python中始终具有相同的哈希值.
  ```py
  >>> 5 == 5.0
  True
  >>> hash(5) == hash(5.0)
  True
  ```
  **注意:** 具有不同值的对象也可能具有相同的哈希值（哈希冲突）.
* 当执行 `some_dict[5] = "Python"` 语句时, 因为Python将 `5` 和 `5.0` 识别为 `some_dict` 的同一个键, 所以已有值 "JavaScript" 就被 "Python" 覆盖了.
* 这个 StackOverflow的 [回答](https://stackoverflow.com/a/32211042/4354153) 漂亮的解释了这背后的基本原理.

---

### > Return return everywhere!/到处返回！

```py
def some_func():
    try:
        return 'from_try'
    finally:
        return 'from_finally'
```

**Output:**
```py
>>> some_func()
'from_finally'
```

#### 💡 说明:

- 当在 "try...finally" 语句的 `try` 中执行 `return`, `break` 或 `continue` 后, `finally` 子句依然会执行.
- 函数的返回值由最后执行的 `return` 语句决定. 由于 `finally` 子句一定会执行, 所以 `finally` 子句中的 `return` 将始终是最后执行的语句.

---

### > Deep down, we're all the same./本质上,我们都一样. *

```py
class WTF:
  pass
```

**Output:**
```py
>>> WTF() == WTF() # 两个不同的对象应该不相等
False
>>> WTF() is WTF() # 也不相同
False
>>> hash(WTF()) == hash(WTF()) # 哈希值也应该不同
True
>>> id(WTF()) == id(WTF())
True
```

#### 💡 说明:

* 当调用 `id` 函数时, Python 创建了一个 `WTF` 类的对象并传给 `id` 函数. 然后 `id` 函数获取其id值 (也就是内存地址), 然后丢弃该对象. 该对象就被销毁了.
* 当我们连续两次进行这个操作时, Python会将相同的内存地址分配给第二个对象. 因为 (在CPython中) `id` 函数使用对象的内存地址作为对象的id值, 所以两个对象的id值是相同的.
* 综上, 对象的id值仅仅在对象的生命周期内唯一. 在对象被销毁之后, 或被创建之前, 其他对象可以具有相同的id值.
* 那为什么 `is` 操作的结果为 `False` 呢? 让我们看看这段代码.
  ```py
  class WTF(object):
    def __init__(self): print("I")
    def __del__(self): print("D")
  ```

  **Output:**
  ```py
  >>> WTF() is WTF()
  I
  I
  D
  D
  False
  >>> id(WTF()) == id(WTF())
  I
  D
  I
  D
  True
  ```
  正如你所看到的, 对象销毁的顺序是造成所有不同之处的原因.

---

### > For what?/为什么?

```py
some_string = "wtf"
some_dict = {}
for i, some_dict[i] in enumerate(some_string):
    pass
```

**Output:**
```py
>>> some_dict # 创建了索引字典.
{0: 'w', 1: 't', 2: 'f'}
```

####  💡 说明:

* [Python 语法](https://docs.python.org/3/reference/grammar.html) 中对 `for` 的定义是:
  ```
  for_stmt: 'for' exprlist 'in' testlist ':' suite ['else' ':' suite]
  ```
  其中 `exprlist` 指分配目标. 这意味着对可迭代对象中的**每一项都会执行**类似 `{exprlist} = {next_value}` 的操作.

  一个有趣的例子说明了这一点:
  ```py
  for i in range(4):
      print(i)
      i = 10
  ```

  **Output:**
  ```
  0
  1
  2
  3
  ```

  你可曾觉得这个循环只会运行一次?

  **💡 说明:**

  - 由于循环在Python中工作方式, 赋值语句 `i = 10` 并不会影响迭代循环, 在每次迭代开始之前, 迭代器(这里指 `range(4)`) 生成的下一个元素就被解包并赋值给目标列表的变量(这里指 `i`)了.

* 在每一次的迭代中, `enumerate(some_string)` 函数就生成一个新值 `i` (计数器增加) 并从 `some_string` 中获取一个字符. 然后将字典 `some_dict` 键 `i` (刚刚分配的) 的值设为该字符. 本例中循环的展开可以简化为:
  ```py
  >>> i, some_dict[i] = (0, 'w')
  >>> i, some_dict[i] = (1, 't')
  >>> i, some_dict[i] = (2, 'f')
  >>> some_dict
  ```

---

### > Evaluation time discrepancy/执行时机差异

1\.
```py
array = [1, 8, 15]
g = (x for x in array if array.count(x) > 0)
array = [2, 8, 22]
```

**Output:**
```py
>>> print(list(g))
[8]
```

2\.

```py
array_1 = [1,2,3,4]
g1 = (x for x in array_1)
array_1 = [1,2,3,4,5]

array_2 = [1,2,3,4]
g2 = (x for x in array_2)
array_2[:] = [1,2,3,4,5]
```

**Output:**
```py
>>> print(list(g1))
[1,2,3,4]

>>> print(list(g2))
[1,2,3,4,5]
```

#### 💡 说明

- 在[生成器](https://wiki.python.org/moin/Generators)表达式中, `in` 子句在声明时执行, 而条件子句则是在运行时执行.
- 所以在运行前, `array` 已经被重新赋值为 `[2, 8, 22]`, 因此对于之前的 `1`, `8` 和 `15`, 只有 `count(8)` 的结果是大于 `0` 的, 所以生成器只会生成 `8`.
- 第二部分中 `g1` 和 `g2` 的输出差异则是由于变量 `array_1` 和 `array_2` 被重新赋值的方式导致的.
- 在第一种情况下, `array_1` 被绑定到新对象 `[1,2,3,4,5]`, 因为 `in` 子句是在声明时被执行的， 所以它仍然引用旧对象 `[1,2,3,4]`(并没有被销毁).
- 在第二种情况下, 对 `array_2` 的切片赋值将相同的旧对象 `[1,2,3,4]` 原地更新为 `[1,2,3,4,5]`. 因此 `g2` 和 `array_2` 仍然引用同一个对象(这个对象现在已经更新为 `[1,2,3,4,5]`).

---

### > `is` is not what it is!/出人意料的`is`!

下面是一个在互联网上非常有名的例子.

```py
>>> a = 256
>>> b = 256
>>> a is b
True

>>> a = 257
>>> b = 257
>>> a is b
False

>>> a = 257; b = 257
>>> a is b
True
```

#### 💡 说明:

**`is` 和 `==` 的区别**

* `is` 运算符检查两个运算对象是否引用自同一对象 (即, 它检查两个预算对象是否相同).
* `==` 运算符比较两个运算对象的值是否相等.
* 因此 `is` 代表引用相同, `==` 代表值相等. 下面的例子可以很好的说明这点,
  ```py
  >>> [] == []
  True
  >>> [] is [] # 这两个空列表位于不同的内存地址.
  False
  ```

**`256` 是一个已经存在的对象, 而 `257` 不是**

当你启动Python 的时候, `-5` 到 `256` 的数值就已经被分配好了. 这些数字因为经常使用所以适合被提前准备好.

引用自 https://docs.python.org/3/c-api/long.html
> 当前的实现为-5到256之间的所有整数保留一个整数对象数组, 当你创建了一个该范围内的整数时, 你只需要返回现有对象的引用. 所以改变1的值是有可能的. 我怀疑这种行为在Python中是未定义行为. :-)

```py
>>> id(256)
10922528
>>> a = 256
>>> b = 256
>>> id(a)
10922528
>>> id(b)
10922528
>>> id(257)
140084850247312
>>> x = 257
>>> y = 257
>>> id(x)
140084850247440
>>> id(y)
140084850247344
```

这里解释器并没有智能到能在执行 `y = 257` 时意识到我们已经创建了一个整数 `257`, 所以它在内存中又新建了另一个对象.

**当 `a` 和 `b` 在同一行中使用相同的值初始化时，会指向同一个对象.**

```py
>>> a, b = 257, 257
>>> id(a)
140640774013296
>>> id(b)
140640774013296
>>> a = 257
>>> b = 257
>>> id(a)
140640774013392
>>> id(b)
140640774013488
```

* 当 a 和 b 在同一行中被设置为 `257` 时, Python 解释器会创建一个新对象, 然后同时引用第二个变量. 如果你在不同的行上进行, 它就不会 "知道" 已经存在一个 `257` 对象了.
* 这是一种特别为交互式环境做的编译器优化. 当你在实时解释器中输入两行的时候, 他们会单独编译, 因此也会单独进行优化. 如果你在 `.py` 文件中尝试这个例子, 则不会看到相同的行为, 因为文件是一次性编译的.

---

### > A tic-tac-toe where X wins in the first attempt!/一蹴即至!

```py
# 我们先初始化一个变量row
row = [""]*3 #row i['', '', '']
# 并创建一个变量board
board = [row]*3
```

**Output:**
```py
>>> board
[['', '', ''], ['', '', ''], ['', '', '']]
>>> board[0]
['', '', '']
>>> board[0][0]
''
>>> board[0][0] = "X"
>>> board
[['X', '', ''], ['X', '', ''], ['X', '', '']]
```

我们有没有赋值过3个 "X" 呢？

#### 💡 说明:

当我们初始化 `row` 变量时, 下面这张图展示了内存中的情况。

![image](/images/tic-tac-toe/after_row_initialized.png)

而当通过对 `row` 做乘法来初始化 `board` 时, 内存中的情况则如下图所示 (每个元素 `board[0]`, `board[1]` 和 `board[2]` 都和 `row` 一样引用了同一列表.)

![image](/images/tic-tac-toe/after_board_initialized.png)

我们可以通过不使用变量 `row` 生成 `board` 来避免这种情况. ([这个](https://github.com/satwikkansal/wtfpython/issues/68)issue提出了这个需求.)

```py
>>> board = [['']*3 for _ in range(3)]
>>> board[0][0] = "X"
>>> board
[['X', '', ''], ['', '', ''], ['', '', '']]
```

---

### > The sticky output function/麻烦的输出

```py
funcs = []
results = []
for x in range(7):
    def some_func():
        return x
    funcs.append(some_func)
    results.append(some_func())

funcs_results = [func() for func in funcs]
```

**Output:**
```py
>>> results
[0, 1, 2, 3, 4, 5, 6]
>>> funcs_results
[6, 6, 6, 6, 6, 6, 6]
```

即使每次在迭代中将 `some_func` 加入 `funcs` 前的 `x` 值都不相同, 所有的函数还是都返回6.

// 再换个例子

```py
>>> powers_of_x = [lambda x: x**i for i in range(10)]
>>> [f(2) for f in powers_of_x]
[512, 512, 512, 512, 512, 512, 512, 512, 512, 512]
```

#### 💡 说明:

- 当在循环内部定义一个函数时, 如果该函数在其主体中使用了循环变量, 则闭包函数将与循环变量绑定, 而不是它的值. 因此, 所有的函数都是使用最后分配给变量的值来进行计算的.

- 可以通过将循环变量作为命名变量传递给函数来获得预期的结果. **为什么这样可行?** 因为这会在函数内再次定义一个局部变量.

    ```py
    funcs = []
    for x in range(7):
        def some_func(x=x):
            return x
        funcs.append(some_func)
    ```

    **Output:**
    ```py
    >>> funcs_results = [func() for func in funcs]
    >>> funcs_results
    [0, 1, 2, 3, 4, 5, 6]
    ```

---

### > `is not ...` is not `is (not ...)`/`is not ...` 不是 `is (not ...)`

```py
>>> 'something' is not None
True
>>> 'something' is (not None)
False
```

#### 💡 说明:

- `is not` 是个单独的二进制运算符, 和分别使用 `is` 和 `not` 不同.
-  如果操作符两侧的变量指向同一个对象, 则 `is not` 的结果为 `False`, 否则结果为 `True`.

---

### > The surprising comma/意外的逗号

**Output:**
```py
>>> def f(x, y,):
...     print(x, y)
...
>>> def g(x=4, y=5,):
...     print(x, y)
...
>>> def h(x, **kwargs,):
  File "<stdin>", line 1
    def h(x, **kwargs,):
                     ^
SyntaxError: invalid syntax
>>> def h(*args,):
  File "<stdin>", line 1
    def h(*args,):
                ^
SyntaxError: invalid syntax
```

#### 💡 说明:

- 在Python函数的形式参数列表中, 尾随逗号并不一定是合法的.
- 在Python中, 参数列表部分用前置逗号定义, 部分用尾随逗号定义. 这种冲突导致逗号被夹在中间, 没有规则定义它.(译:这一句看得我也很懵逼,只能强翻了.详细解释看下面的讨论帖会一目了然.)
- **注意:** 尾随逗号的问题已经在Python 3.6中被[修复](https://bugs.python.org/issue9232)了. 而这篇[帖子](https://bugs.python.org/issue9232#msg248399)中则简要讨论了Python中尾随逗号的不同用法.
---

### > Backslashes at the end of string/字符串末尾的反斜杠

**Output:**
```
>>> print("\\ C:\\")
\ C:\
>>> print(r"\ C:")
\ C:
>>> print(r"\ C:\")

    File "<stdin>", line 1
      print(r"\ C:\")
                     ^
SyntaxError: EOL while scanning string literal
```

#### 💡 说明:

- 在以 `r` 开头的原始字符串中, 反斜杠并没有特殊含义.
  ```py
  >>> print(repr(r"wt\"f"))
  'wt\\"f'
  ```
- 解释器所做的只是简单的改变了反斜杠的行为, 因此会直接放行反斜杠及后一个的字符. 这就是反斜杠在原始字符串末尾不起作用的原因.

---

### > not knot!/别纠结!

```py
x = True
y = False
```

**Output:**
```py
>>> not x == y
True
>>> x == not y
  File "<input>", line 1
    x == not y
           ^
SyntaxError: invalid syntax
```

#### 💡 说明:

* 运算符的优先级会影响表达式的求值顺序, 而在 Python 中 `==` 运算符的优先级要高于 `not` 运算符.
* 所以 `not x == y` 相当于 `not (x == y)`, 同时等价于 `not (True == False)`, 最后的运算结果就是 `True`.
* 之所以 `x == not y` 会抛一个 `SyntaxError` 异常, 是因为它会被认为等价于 `(x == not) y`, 而不是你一开始期望的 `x == (not y)`.
* 解释器期望 `not` 标记是 `not in` 操作符的一部分 (因为 `==` 和 `not in` 操作符具有相同的优先级), 但是它在 `not` 标记后面找不到 `in` 标记, 所以会抛出 `SyntaxError` 异常.

---

### > Half triple-quoted strings/三个引号

**Output:**
```py
>>> print('wtfpython''')
wtfpython
>>> print("wtfpython""")
wtfpython
>>> # 下面的语句会抛出 `SyntaxError` 异常
>>> # print('''wtfpython')
>>> # print("""wtfpython")
```

#### 💡 说明:
+ Python 提供隐式的[字符串链接](https://docs.python.org/2/reference/lexical_analysis.html#string-literal-concatenation), 例如,
  ```
  >>> print("wtf" "python")
  wtfpython
  >>> print("wtf" "") # or "wtf"""
  wtf
  ```
+ `'''` 和 `"""` 在 Python中也是字符串定界符, Python 解释器在先遇到三个引号的的时候会尝试再寻找三个终止引号作为定界符, 如果不存在则会导致 `SyntaxError` 异常.

---

### > Midnight time doesn't exist?/不存在的午夜?

```py
from datetime import datetime

midnight = datetime(2018, 1, 1, 0, 0)
midnight_time = midnight.time()

noon = datetime(2018, 1, 1, 12, 0)
noon_time = noon.time()

if midnight_time:
    print("Time at midnight is", midnight_time)

if noon_time:
    print("Time at noon is", noon_time)
```

**Output:**
```sh
('Time at noon is', datetime.time(12, 0))
```

midnight_time 并没有被输出.

#### 💡 说明:

在Python 3.5之前, 如果 `datetime.time` 对象存储的UTC的午夜时间(译: 就是 `00:00`), 那么它的布尔值会被认为是 `False`. 当使用 `if obj:` 语句来检查 `obj` 是否为 `null` 或者某些“空”值的时候, 很容易出错.

---

### > What's wrong with booleans?/布尔你咋了?

1\.
```py
# 一个简单的例子, 统计下面可迭代对象中的布尔型值的个数和整型值的个数
mixed_list = [False, 1.0, "some_string", 3, True, [], False]
integers_found_so_far = 0
booleans_found_so_far = 0

for item in mixed_list:
    if isinstance(item, int):
        integers_found_so_far += 1
    elif isinstance(item, bool):
        booleans_found_so_far += 1
```

**Output:**
```py
>>> booleans_found_so_far
0
>>> integers_found_so_far
4
```

2\.
```py
another_dict = {}
another_dict[True] = "JavaScript"
another_dict[1] = "Ruby"
another_dict[1.0] = "Python"
```

**Output:**
```py
>>> another_dict[True]
"Python"
```

3\.
```py
>>> some_bool = True
>>> "wtf"*some_bool
'wtf'
>>> some_bool = False
>>> "wtf"*some_bool
''
```

#### 💡 说明:

* 布尔值是 `int` 的子类
  ```py
  >>> isinstance(True, int)
  True
  >>> isinstance(False, int)
  True
  ```

* 所以 `True` 的整数值是 `1`, 而 `False` 的整数值是 `0`.
  ```py
  >>> True == 1 == 1.0 and False == 0 == 0.0
  True
  ```

* 关于其背后的原理, 请看这个 StackOverflow 的[回答](https://stackoverflow.com/a/8169049/4354153).

---

### > Class attributes and instance attributes/类属性和实例属性

1\.
```py
class A:
    x = 1

class B(A):
    pass

class C(A):
    pass
```

**Ouptut:**
```py
>>> A.x, B.x, C.x
(1, 1, 1)
>>> B.x = 2
>>> A.x, B.x, C.x
(1, 2, 1)
>>> A.x = 3
>>> A.x, B.x, C.x
(3, 2, 3)
>>> a = A()
>>> a.x, A.x
(3, 3)
>>> a.x += 1
>>> a.x, A.x
(4, 3)
```

2\.
```py
class SomeClass:
    some_var = 15
    some_list = [5]
    another_list = [5]
    def __init__(self, x):
        self.some_var = x + 1
        self.some_list = self.some_list + [x]
        self.another_list += [x]
```

**Output:**

```py
>>> some_obj = SomeClass(420)
>>> some_obj.some_list
[5, 420]
>>> some_obj.another_list
[5, 420]
>>> another_obj = SomeClass(111)
>>> another_obj.some_list
[5, 111]
>>> another_obj.another_list
[5, 420, 111]
>>> another_obj.another_list is SomeClass.another_list
True
>>> another_obj.another_list is some_obj.another_list
True
```

#### 💡 说明:

* 类变量和实例变量在内部是通过类对象的字典来处理(译: 就是 `__dict__` 属性). 如果在当前类的字典中找不到的话就去它的父类中寻找.
* `+=` 运算符会在原地修改可变对象, 而不是创建新对象. 因此, 修改一个实例的属性会影响其他实例和类属性.

---

### > yielding None/生成 None

```py
some_iterable = ('a', 'b')

def some_func(val):
    return "something"
```

**Output:**
```py
>>> [x for x in some_iterable]
['a', 'b']
>>> [(yield x) for x in some_iterable]
<generator object <listcomp> at 0x7f70b0a4ad58>
>>> list([(yield x) for x in some_iterable])
['a', 'b']
>>> list((yield x) for x in some_iterable)
['a', None, 'b', None]
>>> list(some_func((yield x)) for x in some_iterable)
['a', 'something', 'b', 'something']
```

#### 💡 说明:
- 来源和解释可以在这里找到: https://stackoverflow.com/questions/32139885/yield-in-list-comprehensions-and-generator-expressions
- 相关错误报告: http://bugs.python.org/issue10544

---

### > Mutating the immutable!/强人所难

```py
some_tuple = ("A", "tuple", "with", "values")
another_tuple = ([1, 2], [3, 4], [5, 6])
```

**Output:**
```py
>>> some_tuple[2] = "change this"
TypeError: 'tuple' object does not support item assignment
>>> another_tuple[2].append(1000) # 这里不出现错误
>>> another_tuple
([1, 2], [3, 4], [5, 6, 1000])
>>> another_tuple[2] += [99, 999]
TypeError: 'tuple' object does not support item assignment
>>> another_tuple
([1, 2], [3, 4], [5, 6, 1000, 99, 999])
```

我还以为元组是不可变的呢...

#### 💡 说明:

* 引用 https://docs.python.org/2/reference/datamodel.html

    > 不可变序列
        不可变序列的对象一旦创建就不能再改变. (如果对象包含对其他对象的引用，则这些其他对象可能是可变的并且可能会被修改; 但是，由不可变对象直接引用的对象集合不能更改.)

* `+=` 操作符在原地修改了列表. 元素赋值操作并不工作, 但是当异常抛出时, 元素已经在原地被修改了.

(译: 对于不可变对象, 这里指tuple, `+=` 并不是原子操作, 而是 `extend` 和 `=` 两个动作, 这里 `=` 操作虽然会抛出异常, 但 `extend` 操作已经修改成功了. 详细解释可以看[这里](https://segmentfault.com/a/1190000010767068))

---

### > The disappearing variable from outer scope/消失的外部变量

```py
e = 7
try:
    raise Exception()
except Exception as e:
    pass
```

**Output (Python 2.x):**
```py
>>> print(e)
# prints nothing
```

**Output (Python 3.x):**
```py
>>> print(e)
NameError: name 'e' is not defined
```

#### 💡 说明:

* 出处: https://docs.python.org/3/reference/compound_stmts.html#except

  当使用 `as` 为目标分配异常的时候, 将在except子句的末尾清除该异常.

  这就好像

  ```py
  except E as N:
      foo
  ```

  会被翻译成

  ```py
  except E as N:
      try:
          foo
      finally:
          del N
  ```

  这意味着异常必须在被赋值给其他变量才能在 `except` 子句之后引用它. 而异常之所以会被清除, 则是由于上面附加的回溯信息(trackback)会和栈帧(stack frame)形成循环引用, 使得该栈帧中的所有本地变量在下一次垃圾回收发生之前都处于活动状态.(译: 也就是说不会被回收)

* 子句在 Python 中并没有独立的作用域. 示例中的所有内容都处于同一作用域内, 所以变量 `e` 会由于执行了 `except` 子句而被删除. 而对于有独立的内部作用域的函数来说情况就不一样了. 下面的例子说明了这一点:

     ```py
     def f(x):
         del(x)
         print(x)

     x = 5
     y = [5, 4, 3]
     ```

     **Output:**
     ```py
     >>>f(x)
     UnboundLocalError: local variable 'x' referenced before assignment
     >>>f(y)
     UnboundLocalError: local variable 'x' referenced before assignment
     >>> x
     5
     >>> y
     [5, 4, 3]
     ```

* 在 Python 2.x 中, `Exception()` 实例被赋值给了变量 `e`, 所以当你尝试打印结果的时候, 它的输出为空.（译: 正常的Exception实例打印出来就是空）

    **Output (Python 2.x):**
    ```py
    >>> e
    Exception()
    >>> print e
    # 没有打印任何内容!
    ```

---

### > When True is actually False/真亦假

```py
True = False
if True == False:
    print("I've lost faith in truth!")
```

**Output:**
```
I've lost faith in truth!
```

#### 💡 说明:

- 最初, Python 并没有 `bool` 型 (人们用0表示假值, 用非零值比如1作为真值). 后来他们添加了 `True`, `False`, 和 `bool` 型, 但是, 为了向后兼容, 他们没法把 `True` 和 `False` 设置为常量, 只是设置成了内置变量.
- Python 3 由于不再需要向后兼容, 终于可以修复这个问题了, 所以这个例子无法在 Python 3.x 中执行!

---

### > From filled to None in one instruction.../从有到无...

```py
some_list = [1, 2, 3]
some_dict = {
  "key_1": 1,
  "key_2": 2,
  "key_3": 3
}

some_list = some_list.append(4)
some_dict = some_dict.update({"key_4": 4})
```

**Output:**
```py
>>> print(some_list)
None
>>> print(some_dict)
None
```

#### 💡 说明:

大多数修改序列/映射对象的方法, 比如 `list.append`, `dict.update`, `list.sort` 等等. 都是原地修改对象并返回 `None`. 这样做的理由是, 如果操作可以原地完成, 就可以避免创建对象的副本来提高性能. (参考[这里](http://docs.python.org/2/faq/design.html#why-doesn-t-list-sort-return-the-sorted-list))

---

### > Subclass relationships/子类关系 *

**Output:**
```py
>>> from collections import Hashable
>>> issubclass(list, object)
True
>>> issubclass(object, Hashable)
True
>>> issubclass(list, Hashable)
False
```

子类关系应该是可传递的, 对吧? (即, 如果 `A` 是 `B` 的子类, `B` 是 `C` 的子类, 那么 `A` _应该_ 是 `C` 的子类.)

#### 💡 说明:

* Python 中的子类关系并不必须是传递的. 任何人都可以在元类中随意定义 `__subclasscheck__`.
* 当 `issubclass(cls, Hashable)` 被调用时, 它只是在 `cls` 中寻找 "`__hash__`" 方法或继承自"`__hash__`"的方法.
* 由于 `object` is 可散列的(hashable), 但是 `list` 是不可散列的, 所以它打破了这种传递关系.
* 在[这里](https://www.naftaliharris.com/blog/python-subclass-intransitivity/)可以找到更详细的解释.

---

### > The mysterious key type conversion/神秘的键型转换 *

```py
class SomeClass(str):
    pass

some_dict = {'s':42}
```

**Output:**
```py
>>> type(list(some_dict.keys())[0])
str
>>> s = SomeClass('s')
>>> some_dict[s] = 40
>>> some_dict # 预期: 两个不同的键值对
{'s': 40}
>>> type(list(some_dict.keys())[0])
str
```

#### 💡 说明:

* 由于 `SomeClass` 会从 `str` 自动继承 `__hash__` 方法, 所以 `s` 对象和 `"s"` 字符串的哈希值是相同的.
* 而 `SomeClass("s") == "s"` 为 `True` 是因为 `SomeClass` 也继承了 `str` 类 `__eq__` 方法.
* 由于两者的哈希值相同且相等, 所以它们在字典中表示相同的键.
* 如果想要实现期望的功能, 我们可以重定义 `SomeClass` 的 `__eq__` 方法.
  ```py
  class SomeClass(str):
    def __eq__(self, other):
        return (
            type(self) is SomeClass
            and type(other) is SomeClass
            and super().__eq__(other)
        )

    # 当我们自定义 __eq__ 方法时, Python 不会再自动继承 __hash__ 方法
    # 所以我们也需要定义它
    __hash__ = str.__hash__

  some_dict = {'s':42}
  ```

  **Output:**
  ```py
  >>> s = SomeClass('s')
  >>> some_dict[s] = 40
  >>> some_dict
  {'s': 40, 's': 42}
  >>> keys = list(some_dict.keys())
  >>> type(keys[0]), type(keys[1])
  (__main__.SomeClass, str)
  ```

---

### > Let's see if you can guess this?/看看你能否猜到这一点?

```py
a, b = a[b] = {}, 5
```

**Output:**
```py
>>> a
{5: ({...}, 5)}
```

#### 💡 说明:

* 根据 [Python 语言参考](https://docs.python.org/2/reference/simple_stmts.html#assignment-statements), 赋值语句的形式如下
  ```
  (target_list "=")+ (expression_list | yield_expression)
  ```

  > 赋值语句计算表达式列表(expression list)(牢记 这可以是单个表达式或以逗号分隔的列表, 后者返回元组)并将单个结果对象从左到右分配给目标列表中的每一项.

*  `(target_list "=")+` 中的 `+` 意味着可以有**一个或多个**目标列表. 在这个例子中, 目标列表是 `a, b` 和 `a[b]` (注意表达式列表只能有一个, 在我们的例子中是 `{}, 5`).

* 表达式列表计算结束后, 将其值自动解包后**从左到右**分配给目标列表(target list). 因此, 在我们的例子中, 首先将 `{}, 5` 元祖并赋值给 `a, b`, 然后我们就可以得到 `a = {}` 且 `b = 5`.

* `a` 被赋值的 `{}` 是可变对象.

* 第二个目标列表是 `a[b]` (你可能觉得这里会报错, 因为在之前的语句中 `a` 和 `b` 都还没有被定义. 但是别忘了, 我们刚刚将 `a` 赋值 `{}` 且将 `b` 赋值为 `5`).

* 现在, 我们将通过将字典中键 `5` 的值设置为元祖 `({}, 5)` 来创建循环引用 (输出中的 `{...}` 指与 `a` 引用了相同的对象). 下面是一个更简单的循环引用的例子
  ```py
  >>> some_list = some_list[0] = [0]
  >>> some_list
  [[...]]
  >>> some_list[0]
  [[...]]
  >>> some_list is some_list[0]
  True
  >>> some_list[0][0][0][0][0][0] == some_list
  True
  ```
  我们的例子就是这种情况 (`a[b][0]` 与 `a` 是相同的对象)

* 总结一下, 你也可以把例子拆成
  ```py
  a, b = {}, 5
  a[b] = a, b
  ```
  并且可以通过 `a[b][0]` 与 `a` 是相同的对象来证明是循环引用
  ```py
  >>> a[b][0] is a
  True
  ```

---

---

## Section: Appearances are deceptive!

### > Skipping lines?/跳过一行?

**Output:**
```py
>>> value = 11
>>> valuе = 32
>>> value
11
```

什么鬼?

**注意:** 如果你想要重现的话最简单的方法是直接复制上面的代码片段到你的文件或命令行里.

#### 💡 说明:

一些非西方字符虽然看起来和英语字母相同, 但会被解释器识别为不同的字母.

```py
>>> ord('е') # 西里尔语的 'e' (Ye)
1077
>>> ord('e') # 拉丁语的 'e', 用于英文并使用标准键盘输入
101
>>> 'е' == 'e'
False

>>> value = 42 # 拉丁语 e
>>> valuе = 23 # 西里尔语 'e', Python 2.x 的解释器在这会抛出 `SyntaxError` 异常
>>> value
42
```

内置的 `ord()` 函数可以返回一个字符的 Unicode [代码点](https://en.wikipedia.org/wiki/Code_point), 这里西里尔语 'e' 和拉丁语 'e' 的代码点不同证实了上述例子.

---

### > Teleportation/空间移动 *

```py
import numpy as np

def energy_send(x):
    # 初始化一个 numpy 数组
    np.array([float(x)])

def energy_receive():
    # 返回一个空的 numpy 数组
    return np.empty((), dtype=np.float).tolist()
```

**Output:**
```py
>>> energy_send(123.456)
>>> energy_receive()
123.456
```

谁来给我发个诺贝尔奖?

#### 💡 说明:

* 注意在 `energy_send` 函数中创建的 numpy 数组并没有返回, 因此内存空间被释放并可以被重新分配.
* `numpy.empty()` 直接返回下一段空闲内存，而不重新初始化. 而这个内存点恰好就是刚刚释放的那个(通常情况下, 并不绝对).

---

### > Well, something is fishy.../嗯，有些可疑...

```py
def square(x):
    """
    一个通过加法计算平方的简单函数.
    """
    sum_so_far = 0
    for counter in range(x):
        sum_so_far = sum_so_far + x
  return sum_so_far
```

**Output (Python 2.x):**

```py
>>> square(10)
10
```

难道不应该是100吗?

**注意:** 如果你无法重现, 可以尝试运行这个文件[mixed_tabs_and_spaces.py](/mixed_tabs_and_spaces.py).

#### 💡 说明:

* **不要混用制表符(tab)和空格(space)!** 在上面的例子中, return 的前面是"1个制表符", 而其他部分的代码前面是 "4个空格".
* Python是这么处理制表符的:
  > 首先, 制表符会从左到右依次被替换成8个空格, 直到被替换后的字符总数是八的倍数 <...>
* 因此, `square` 函数最后一行的制表符会被替换成8个空格, 导致return语句进入循环语句里面.
* Python 3 很友好, 在这种情况下会自动抛出错误.

    **Output (Python 3.x):**
    ```py
    TabError: inconsistent use of tabs and spaces in indentation
    ```

---

---

## Section: Watch out for the landmines!


### > Modifying a dictionary while iterating over it/迭代字典时的修改

```py
x = {0: None}

for i in x:
    del x[i]
    x[i+1] = None
    print(i)
```

**Output (Python 2.7- Python 3.5):**

```
0
1
2
3
4
5
6
7
```

是的, 它运行了**八次**然后才停下来.

#### 💡 说明:

* Python不支持对字典进行迭代的同时修改它.
* 它之所以运行8次, 是因为字典会自动扩容以容纳更多键值(我们有8次删除记录, 因此需要扩容). 这实际上是一个实现细节. (译: 应该是因为字典的初始最小值是8, 扩容会导致散列表地址发生变化而中断循环.)
* 在不同的Python实现中删除键的处理方式以及调整大小的时间可能会有所不同.(译: 就是说什么时候扩容在不同版本中可能是不同的, 在3.6及3.7的版本中到[5](https://github.com/python/cpython/blob/v3.6.1/Objects/dictobject.c#L103-L110)就会自动扩容了. 以后也有可能再次发生变化. 顺带一提,后面两次扩容会扩展为32和256. 8->32->256)
* 更多的信息, 你可以参考这个StackOverflow的[回答](https://stackoverflow.com/questions/44763802/bug-in-python-dict), 它详细的解释一个类似的例子.

---

### > Stubborn `del` operator/坚强的 `del` *

```py
class SomeClass:
    def __del__(self):
        print("Deleted!")
```

**Output:**
1\.
```py
>>> x = SomeClass()
>>> y = x
>>> del x # 这里应该会输出 "Deleted!"
>>> del y
Deleted!
```

唷, 终于删除了. 你可能已经猜到了在我们第一次尝试删除 `x` 时是什么让 `__del__` 免于被调用的. 那让我们给这个例子增加点难度.

2\.
```py
>>> x = SomeClass()
>>> y = x
>>> del x
>>> y # 检查一下y是否存在
<__main__.SomeClass instance at 0x7f98a1a67fc8>
>>> del y # 像之前一样, 这里应该会输出 "Deleted!"
>>> globals() # 好吧, 并没有. 让我们看一下所有的全局变量
Deleted!
{'__builtins__': <module '__builtin__' (built-in)>, 'SomeClass': <class __main__.SomeClass at 0x7f98a1a5f668>, '__package__': None, '__name__': '__main__', '__doc__': None}
```

好了，现在它被删除了 :confused:

#### 💡 说明:
+ `del x` 并不会立刻调用 `x.__del__()`.
+ 每当遇到 `del x`, Python 会将 `x` 的引用数减1, 当 `x` 的引用数减到0时就会调用 `x.__del__()`.
+ 在第二个例子中, `y.__del__()` 之所以未被调用, 是因为前一条语句 (`>>> y`) 对同一对象创建了另一个引用, 从而防止在执行 `del y` 后对象的引用数变为0.
+ 调用 `globals` 导致引用被销毁, 因此我们可以看到 "Deleted!" 终于被输出了.
+ (译: 这其实是 Python 交互解释器的特性, 它会自动让 `_` 保存上一个表达式输出的值, 详细可以看[这里](https://www.cnblogs.com/leisurelylicht/p/diao-pi-de-kong-zhi-tai.html).)

---

### > Deleting a list item while iterating/迭代列表时删除元素

```py
list_1 = [1, 2, 3, 4]
list_2 = [1, 2, 3, 4]
list_3 = [1, 2, 3, 4]
list_4 = [1, 2, 3, 4]

for idx, item in enumerate(list_1):
    del item

for idx, item in enumerate(list_2):
    list_2.remove(item)

for idx, item in enumerate(list_3[:]):
    list_3.remove(item)

for idx, item in enumerate(list_4):
    list_4.pop(idx)
```

**Output:**
```py
>>> list_1
[1, 2, 3, 4]
>>> list_2
[2, 4]
>>> list_3
[]
>>> list_4
[2, 4]
```

你能猜到为什么输出是 `[2, 4]` 吗?

#### 💡 说明:

* 在迭代时修改对象是一个很愚蠢的主意. 正确的做法是迭代对象的副本, `list_3[:]` 就是这么做的.

     ```py
     >>> some_list = [1, 2, 3, 4]
     >>> id(some_list)
     139798789457608
     >>> id(some_list[:]) # 注意python为切片列表创建了新对象.
     139798779601192
     ```

**`del`, `remove` 和 `pop` 的不同:**
* `del var_name` 只是从本地或全局命名空间中删除了 `var_name` (这就是为什么 `list_1` 没有受到影响).
* `remove` 会删除第一个匹配到的指定值, 而不是特定的索引, 如果找不到值则抛出 `ValueError` 异常.
* `pop` 则会删除指定索引处的元素并返回它, 如果指定了无效的索引则抛出 `IndexError` 异常.

**为什么输出是 `[2, 4]`?**
- 列表迭代是按索引进行的, 所以当我们从 `list_2` 或 `list_4` 中删除 `1` 时, 列表的内容就变成了 `[2, 3, 4]`. 剩余元素会依次位移, 也就是说, `2` 的索引会变为 0, `3` 会变为 1. 由于下一次迭代将获取索引为 1 的元素 (即 `3`), 因此 `2` 将被彻底的跳过. 类似的情况会交替发生在列表中的每个元素上.

* 参考这个StackOverflow的[回答](https://stackoverflow.com/questions/45946228/what-happens-when-you-try-to-delete-a-list-element-while-iterating-over-it)来解释这个例子
* 关于Python中字典的类似例子, 可以参考这个Stackoverflow的[回答](https://stackoverflow.com/questions/45877614/how-to-change-all-the-dictionary-keys-in-a-for-loop-with-d-items).

---

### > Loop variables leaking out!/循环变量泄漏!

1\.
```py
for x in range(7):
    if x == 6:
        print(x, ': for x inside loop')
print(x, ': x in global')
```

**Output:**
```py
6 : for x inside loop
6 : x in global
```

但是 `x` 从未在循环外被定义...

2\.
```py
# 这次我们先初始化x
x = -1
for x in range(7):
    if x == 6:
        print(x, ': for x inside loop')
print(x, ': x in global')
```

**Output:**
```py
6 : for x inside loop
6 : x in global
```

3\.
```
x = 1
print([x for x in range(5)])
print(x, ': x in global')
```

**Output (on Python 2.x):**
```
[0, 1, 2, 3, 4]
(4, ': x in global')
```

**Output (on Python 3.x):**
```
[0, 1, 2, 3, 4]
1 : x in global
```

#### 💡 说明:

- 在 Python 中, for 循环使用所在作用域并在结束后保留定义的循环变量. 如果我们曾在全局命名空间中定义过循环变量. 在这种情况下, 它会重新绑定现有变量.

- Python 2.x 和 Python 3.x 解释器在列表推导式示例中的输出差异, 在文档 [What’s New In Python 3.0](https://docs.python.org/3/whatsnew/3.0.html) 中可以找到相关的解释:

    > "列表推导不再支持句法形式 `[... for var in item1, item2, ...]`. 取而代之的是 `[... for var in (item1, item2, ...)]`. 另外, 注意列表推导具有不同的语义: 它们更接近于 `list()` 构造函数中生成器表达式的语法糖(译: 这一句我也不是很明白), 特别是循环控制变量不再泄漏到周围的作用域中."

---

### > Beware of default mutable arguments!/当心默认的可变参数!

```py
def some_func(default_arg=[]):
    default_arg.append("some_string")
    return default_arg
```

**Output:**
```py
>>> some_func()
['some_string']
>>> some_func()
['some_string', 'some_string']
>>> some_func([])
['some_string']
>>> some_func()
['some_string', 'some_string', 'some_string']
```

#### 💡 说明:

- Python中函数的默认可变参数并不是每次调用该函数时都会被初始化. 相反, 它们会使用最近分配的值作为默认值. 当我们明确的将 `[]` 作为参数传递给 `some_func` 的时候, 就不会使用 `default_arg` 的默认值, 所以函数会返回我们所期望的结果.

    ```py
    def some_func(default_arg=[]):
        default_arg.append("some_string")
        return default_arg
    ```

    **Output:**
    ```py
    >>> some_func.__defaults__ # 这里会显示函数的默认参数的值
    ([],)
    >>> some_func()
    >>> some_func.__defaults__
    (['some_string'],)
    >>> some_func()
    >>> some_func.__defaults__
    (['some_string', 'some_string'],)
    >>> some_func([])
    >>> some_func.__defaults__
    (['some_string', 'some_string'],)
    ```

- 避免可变参数导致的错误的常见做法是将 `None` 指定为参数的默认值, 然后检查是否有值传给对应的参数. 例:

    ```py
    def some_func(default_arg=None):
        if not default_arg:
            default_arg = []
        default_arg.append("some_string")
        return default_arg
    ```

---

### > Catching the Exceptions

```py
some_list = [1, 2, 3]
try:
    # This should raise an ``IndexError``
    print(some_list[4])
except IndexError, ValueError:
    print("Caught!")

try:
    # This should raise a ``ValueError``
    some_list.remove(4)
except IndexError, ValueError:
    print("Caught again!")
```

**Output (Python 2.x):**
```py
Caught!

ValueError: list.remove(x): x not in list
```

**Output (Python 3.x):**
```py
  File "<input>", line 3
    except IndexError, ValueError:
                     ^
SyntaxError: invalid syntax
```

#### 💡 Explanation

* To add multiple Exceptions to the except clause, you need to pass them as parenthesized tuple as the first argument. The second argument is an optional name, which when supplied will bind the Exception instance that has been raised. Example,
  ```py
  some_list = [1, 2, 3]
  try:
     # This should raise a ``ValueError``
     some_list.remove(4)
  except (IndexError, ValueError), e:
     print("Caught again!")
     print(e)
  ```
  **Output (Python 2.x):**
  ```
  Caught again!
  list.remove(x): x not in list
  ```
  **Output (Python 3.x):**
  ```py
    File "<input>", line 4
      except (IndexError, ValueError), e:
                                       ^
  IndentationError: unindent does not match any outer indentation level
  ```

* Separating the exception from the variable with a comma is deprecated and does not work in Python 3; the correct way is to use `as`. Example,
  ```py
  some_list = [1, 2, 3]
  try:
      some_list.remove(4)

  except (IndexError, ValueError) as e:
      print("Caught again!")
      print(e)
  ```
  **Output:**
  ```
  Caught again!
  list.remove(x): x not in list
  ```

---

### > Same operands, different story!

1\.
```py
a = [1, 2, 3, 4]
b = a
a = a + [5, 6, 7, 8]
```

**Output:**
```py
>>> a
[1, 2, 3, 4, 5, 6, 7, 8]
>>> b
[1, 2, 3, 4]
```

2\.
```py
a = [1, 2, 3, 4]
b = a
a += [5, 6, 7, 8]
```

**Output:**
```py
>>> a
[1, 2, 3, 4, 5, 6, 7, 8]
>>> b
[1, 2, 3, 4, 5, 6, 7, 8]
```

#### 💡 Explanation:

*  `a += b` doesn't always behave the same way as `a = a + b`.  Classes *may* implement the *`op=`* operators differently, and lists do this.

* The expression `a = a + [5,6,7,8]` generates a new list and sets `a`'s reference to that new list, leaving `b` unchanged.

* The expression `a += [5,6,7,8]` is actually mapped to an "extend" function that operates on the list such that `a` and `b` still point to the same list that has been modified in-place.

---

### > The out of scope variable

```py
a = 1
def some_func():
    return a

def another_func():
    a += 1
    return a
```

**Output:**
```py
>>> some_func()
1
>>> another_func()
UnboundLocalError: local variable 'a' referenced before assignment
```

#### 💡 Explanation:
* When you make an assignment to a variable in scope, it becomes local to that scope. So `a` becomes local to the scope of `another_func`,  but it has not been initialized previously in the same scope which throws an error.
* Read [this](http://sebastianraschka.com/Articles/2014_python_scope_and_namespaces.html) short but an awesome guide to learn more about how namespaces and scope resolution works in Python.
* To modify the outer scope variable `a` in `another_func`, use `global` keyword.
  ```py
  def another_func()
      global a
      a += 1
      return a
  ```

  **Output:**
  ```py
  >>> another_func()
  2
  ```

---

### > Be careful with chained operations

```py
>>> (False == False) in [False] # makes sense
False
>>> False == (False in [False]) # makes sense
False
>>> False == False in [False] # now what?
True

>>> True is False == False
False
>>> False is False is False
True

>>> 1 > 0 < 1
True
>>> (1 > 0) < 1
False
>>> 1 > (0 < 1)
False
```

#### 💡 Explanation:

As per https://docs.python.org/2/reference/expressions.html#not-in

> Formally, if a, b, c, ..., y, z are expressions and op1, op2, ..., opN are comparison operators, then a op1 b op2 c ... y opN z is equivalent to a op1 b and b op2 c and ... y opN z, except that each expression is evaluated at most once.

While such behavior might seem silly to you in the above examples, it's fantastic with stuff like `a == b == c` and `0 <= x <= 100`.

* `False is False is False` is equivalent to `(False is False) and (False is False)`
* `True is False == False` is equivalent to `True is False and False == False` and since the first part of the statement (`True is False`) evaluates to `False`, the overall expression evaluates to `False`.
* `1 > 0 < 1` is equivalent to `1 > 0 and 0 < 1` which evaluates to `True`.
* The expression `(1 > 0) < 1` is equivalent to `True < 1` and
  ```py
  >>> int(True)
  1
  >>> True + 1 #not relevant for this example, but just for fun
  2
  ```
  So, `1 < 1` evaluates to `False`

---

### > Name resolution ignoring class scope

1\.
```py
x = 5
class SomeClass:
    x = 17
    y = (x for i in range(10))
```

**Output:**
```py
>>> list(SomeClass.y)[0]
5
```

2\.
```py
x = 5
class SomeClass:
    x = 17
    y = [x for i in range(10)]
```

**Output (Python 2.x):**
```py
>>> SomeClass.y[0]
17
```

**Output (Python 3.x):**
```py
>>> SomeClass.y[0]
5
```

#### 💡 Explanation
- Scopes nested inside class definition ignore names bound at the class level.
- A generator expression has its own scope.
- Starting from Python 3.X, list comprehensions also have their own scope.

---

### > Needle in a Haystack

1\.
```py
x, y = (0, 1) if True else None, None
```

**Output:**
```
>>> x, y  # expected (0, 1)
((0, 1), None)
```

Almost every Python programmer has faced a similar situation.

2\.
```py
t = ('one', 'two')
for i in t:
    print(i)

t = ('one')
for i in t:
    print(i)

t = ()
print(t)
```

**Output:**
```py
one
two
o
n
e
tuple()
```

#### 💡 Explanation:
* For 1, the correct statement for expected behavior is `x, y = (0, 1) if True else (None, None)`.
* For 2, the correct statement for expected behavior is `t = ('one',)` or `t = 'one',` (missing comma) otherwise the interpreter considers `t` to be a `str` and iterates over it character by character.
* `()` is a special token and denotes empty `tuple`.

---

---


## Section: The Hidden treasures!

This section contains few of the lesser-known interesting things about Python that most beginners like me are unaware of (well, not anymore).

### > Okay Python, Can you make me fly? *

Well, here you go

```py
import antigravity
```

**Output:**
Sshh.. It's a super secret.

#### 💡 Explanation:
+ `antigravity` module is one of the few easter eggs released by Python developers.
+ `import antigravity` opens up a web browser pointing to the [classic XKCD comic](http://xkcd.com/353/) about Python.
+ Well, there's more to it. There's **another easter egg inside the easter egg**. If you look at the [code](https://github.com/python/cpython/blob/master/Lib/antigravity.py#L7-L17), there's a function defined that purports to implement the [XKCD's geohashing algorithm](https://xkcd.com/426/).

---

### > `goto`, but why? *

```py
from goto import goto, label
for i in range(9):
    for j in range(9):
        for k in range(9):
            print("I'm trapped, please rescue!")
            if k == 2:
                goto .breakout # breaking out from a deeply nested loop
label .breakout
print("Freedom!")
```

**Output (Python 2.3):**
```py
I'm trapped, please rescue!
I'm trapped, please rescue!
Freedom!
```

#### 💡 Explanation:
- A working version of `goto` in Python was [announced](https://mail.python.org/pipermail/python-announce-list/2004-April/002982.html) as an April Fool's joke on 1st April 2004.
- Current versions of Python do not have this module.
- Although it works, but please don't use it. Here's the [reason](https://docs.python.org/3/faq/design.html#why-is-there-no-goto) to why `goto` is not present in Python.

---

### > Brace yourself! *

If you are one of the people who doesn't like using whitespace in Python to denote scopes, you can use the C-style {} by importing,

```py
from __future__ import braces
```

**Output:**
```py
  File "some_file.py", line 1
    from __future__ import braces
SyntaxError: not a chance
```

Braces? No way! If you think that's disappointing, use Java.

#### 💡 Explanation:
+ The `__future__` module is normally used to provide features from future versions of Python. The "future" here is however ironic.
+ This is an easter egg concerned with the community's feelings on this issue.

---

### > Let's meet Friendly Language Uncle For Life *

**Output (Python 3.x)**
```py
>>> from __future__ import barry_as_FLUFL
>>> "Ruby" != "Python" # there's no doubt about it
  File "some_file.py", line 1
    "Ruby" != "Python"
              ^
SyntaxError: invalid syntax

>>> "Ruby" <> "Python"
True
```

There we go.

#### 💡 Explanation:
- This is relevant to [PEP-401](https://www.python.org/dev/peps/pep-0401/) released on April 1, 2009 (now you know, what it means).
- Quoting from the PEP-401
  > Recognized that the != inequality operator in Python 3.0 was a horrible, finger pain inducing mistake, the FLUFL reinstates the <> diamond operator as the sole spelling.
- There were more things that Uncle Barry had to share in the PEP; you can read them [here](https://www.python.org/dev/peps/pep-0401/).

---

### > Even Python understands that love is complicated *

```py
import this
```

Wait, what's **this**? `this` is love :heart:

**Output:**
```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

It's the Zen of Python!

```py
>>> love = this
>>> this is love
True
>>> love is True
False
>>> love is False
False
>>> love is not True or False
True
>>> love is not True or False; love is love  # Love is complicated
True
```

#### 💡 Explanation:

* `this` module in Python is an easter egg for The Zen Of Python ([PEP 20](https://www.python.org/dev/peps/pep-0020)).
* And if you think that's already interesting enough, check out the implementation of [this.py](https://hg.python.org/cpython/file/c3896275c0f6/Lib/this.py). Interestingly, the code for the Zen violates itself (and that's probably the only place where this happens).
* Regarding the statement `love is not True or False; love is love`, ironic but it's self-explanatory.

---

### > Yes, it exists!

**The `else` clause for loops.** One typical example might be:

```py
  def does_exists_num(l, to_find):
      for num in l:
          if num == to_find:
              print("Exists!")
              break
      else:
          print("Does not exist")
```

**Output:**
```py
>>> some_list = [1, 2, 3, 4, 5]
>>> does_exists_num(some_list, 4)
Exists!
>>> does_exists_num(some_list, -1)
Does not exist
```

**The `else` clause in exception handling.** An example,

```py
try:
    pass
except:
    print("Exception occurred!!!")
else:
    print("Try block executed successfully...")
```

**Output:**
```py
Try block executed successfully...
```

#### 💡 Explanation:
- The `else` clause after a loop is executed only when there's no explicit `break` after all the iterations.
- `else` clause after try block is also called "completion clause" as reaching the `else` clause in a `try` statement means that the try block actually completed successfully.

---

### > Inpinity *

The spelling is intended. Please, don't submit a patch for this.

**Output (Python 3.x):**
```py
>>> infinity = float('infinity')
>>> hash(infinity)
314159
>>> hash(float('-inf'))
-314159
```

#### 💡 Explanation:
- Hash of infinity is 10⁵ x π.
- Interestingly, the hash of `float('-inf')` is "-10⁵ x π" in Python 3, whereas "-10⁵ x e" in Python 2.

---

### > Mangling time! *

```py
class Yo(object):
    def __init__(self):
        self.__honey = True
        self.bitch = True
```

**Output:**
```py
>>> Yo().bitch
True
>>> Yo().__honey
AttributeError: 'Yo' object has no attribute '__honey'
>>> Yo()._Yo__honey
True
```

Why did `Yo()._Yo__honey` work? Only Indian readers would understand.

#### 💡 Explanation:

* [Name Mangling](https://en.wikipedia.org/wiki/Name_mangling) is used to avoid naming collisions between different namespaces.
* In Python, the interpreter modifies (mangles) the class member names starting with `__` (double underscore) and not ending with more than one trailing underscore by adding `_NameOfTheClass` in front.
* So, to access `__honey` attribute, we are required to append `_Yo` to the front which would prevent conflicts with the same name attribute defined in any other class.

---

---

## Section: Miscellaneous


### > `+=` is faster

```py
# using "+", three strings:
>>> timeit.timeit("s1 = s1 + s2 + s3", setup="s1 = ' ' * 100000; s2 = ' ' * 100000; s3 = ' ' * 100000", number=100)
0.25748300552368164
# using "+=", three strings:
>>> timeit.timeit("s1 += s2 + s3", setup="s1 = ' ' * 100000; s2 = ' ' * 100000; s3 = ' ' * 100000", number=100)
0.012188911437988281
```

#### 💡 Explanation:
+ `+=` is faster than `+` for concatenating more than two strings because the first string (example, `s1` for `s1 += s2 + s3`) is not destroyed while calculating the complete string.

---

### > Let's make a giant string!

```py
def add_string_with_plus(iters):
    s = ""
    for i in range(iters):
        s += "xyz"
    assert len(s) == 3*iters

def add_bytes_with_plus(iters):
    s = b""
    for i in range(iters):
        s += b"xyz"
    assert len(s) == 3*iters

def add_string_with_format(iters):
    fs = "{}"*iters
    s = fs.format(*(["xyz"]*iters))
    assert len(s) == 3*iters

def add_string_with_join(iters):
    l = []
    for i in range(iters):
        l.append("xyz")
    s = "".join(l)
    assert len(s) == 3*iters

def convert_list_to_string(l, iters):
    s = "".join(l)
    assert len(s) == 3*iters
```

**Output:**
```py
>>> timeit(add_string_with_plus(10000))
1000 loops, best of 3: 972 µs per loop
>>> timeit(add_bytes_with_plus(10000))
1000 loops, best of 3: 815 µs per loop
>>> timeit(add_string_with_format(10000))
1000 loops, best of 3: 508 µs per loop
>>> timeit(add_string_with_join(10000))
1000 loops, best of 3: 878 µs per loop
>>> l = ["xyz"]*10000
>>> timeit(convert_list_to_string(l, 10000))
10000 loops, best of 3: 80 µs per loop
```

Let's increase the number of iterations by a factor of 10.

```py
>>> timeit(add_string_with_plus(100000)) # Linear increase in execution time
100 loops, best of 3: 9.75 ms per loop
>>> timeit(add_bytes_with_plus(100000)) # Quadratic increase
1000 loops, best of 3: 974 ms per loop
>>> timeit(add_string_with_format(100000)) # Linear increase
100 loops, best of 3: 5.25 ms per loop
>>> timeit(add_string_with_join(100000)) # Linear increase
100 loops, best of 3: 9.85 ms per loop
>>> l = ["xyz"]*100000
>>> timeit(convert_list_to_string(l, 100000)) # Linear increase
1000 loops, best of 3: 723 µs per loop
```

#### 💡 Explanation
- You can read more about [timeit](https://docs.python.org/3/library/timeit.html) from here. It is generally used to measure the execution time of snippets.
- Don't use `+` for generating long strings — In Python, `str` is immutable, so the left and right strings have to be copied into the new string for every pair of concatenations. If you concatenate four strings of length 10, you'll be copying (10+10) + ((10+10)+10) + (((10+10)+10)+10) = 90 characters instead of just 40 characters. Things get quadratically worse as the number and size of the string increases (justified with the execution times of `add_bytes_with_plus` function)
- Therefore, it's advised to use `.format.` or `%` syntax (however, they are slightly slower than `+` for short strings).
- Or better, if already you've contents available in the form of an iterable object, then use `''.join(iterable_object)` which is much faster.
- `add_string_with_plus` didn't show a quadratic increase in execution time unlike `add_bytes_with_plus` because of the `+=` optimizations discussed in the previous example. Had the statement been `s = s + "x" + "y" + "z"` instead of `s += "xyz"`, the increase would have been quadratic.
  ```py
  def add_string_with_plus(iters):
      s = ""
      for i in range(iters):
          s = s + "x" + "y" + "z"
      assert len(s) == 3*iters

  >>> timeit(add_string_with_plus(10000))
  100 loops, best of 3: 9.87 ms per loop
  >>> timeit(add_string_with_plus(100000)) # Quadratic increase in execution time
  1 loops, best of 3: 1.09 s per loop
  ```

---

### > Explicit typecast of strings

```py
a = float('inf')
b = float('nan')
c = float('-iNf')  #These strings are case-insensitive
d = float('nan')
```

**Output:**
```py
>>> a
inf
>>> b
nan
>>> c
-inf
>>> float('some_other_string')
ValueError: could not convert string to float: some_other_string
>>> a == -c #inf==inf
True
>>> None == None # None==None
True
>>> b == d #but nan!=nan
False
>>> 50/a
0.0
>>> a/a
nan
>>> 23 + b
nan
```

#### 💡 Explanation:

`'inf'` and `'nan'` are special strings (case-insensitive), which when explicitly typecasted to `float` type, are used to represent mathematical "infinity" and "not a number" respectively.

---

### > Minor Ones

* `join()` is a string operation instead of list operation. (sort of counter-intuitive at first usage)

  **💡 Explanation:**
  If `join()` is a method on a string then it can operate on any iterable (list, tuple, iterators). If it were a method on a list, it'd have to be implemented separately by every type. Also, it doesn't make much sense to put a string-specific method on a generic `list` object API.

* Few weird looking but semantically correct statements:
  + `[] = ()` is a semantically correct statement (unpacking an empty `tuple` into an empty `list`)
  + `'a'[0][0][0][0][0]` is also a semantically correct statement as strings are [sequences](https://docs.python.org/3/glossary.html#term-sequence)(iterables supporting element access using integer indices) in Python.
  + `3 --0-- 5 == 8` and `--5 == 5` are both semantically correct statements and evaluate to `True`.

* Given that `a` is a number, `++a` and `--a` are both valid Python statements but don't behave the same way as compared with similar statements in languages like C, C++ or Java.
  ```py
  >>> a = 5
  >>> a
  5
  >>> ++a
  5
  >>> --a
  5
  ```

  **💡 Explanation:**
  + There is no `++` operator in Python grammar. It is actually two `+` operators.
  + `++a` parses as `+(+a)` which translates to `a`. Similarly, the output of the statement `--a` can be justified.
  + This StackOverflow [thread](https://stackoverflow.com/questions/3654830/why-are-there-no-and-operators-in-python) discusses the rationale behind the absence of increment and decrement operators in Python.

* Python uses 2 bytes for local variable storage in functions. In theory, this means that only 65536 variables can be defined in a function. However, python has a handy solution built in that can be used to store more than 2^16 variable names. The following code demonstrates what happens in the stack when more than 65536 local variables are defined (Warning: This code prints around 2^18 lines of text, so be prepared!):
     ```py
     import dis
     exec("""
     def f():
         """ + """
         """.join(["X"+str(x)+"=" + str(x) for x in range(65539)]))

     f()

     print(dis.dis(f))
     ```

* Multiple Python threads won't run your *Python code* concurrently (yes you heard it right!). It may seem intuitive to spawn several threads and let them execute your Python code concurrently, but, because of the [Global Interpreter Lock](https://wiki.python.org/moin/GlobalInterpreterLock) in Python, all you're doing is making your threads execute on the same core turn by turn. Python threads are good for IO-bound tasks, but to achieve actual parallelization in Python for CPU-bound tasks, you might want to use the Python [multiprocessing](https://docs.python.org/2/library/multiprocessing.html) module.

* List slicing with out of the bounds indices throws no errors
  ```py
  >>> some_list = [1, 2, 3, 4, 5]
  >>> some_list[111:]
  []
  ```

* `int('١٢٣٤٥٦٧٨٩')` returns `123456789` in Python 3. In Python, Decimal characters include digit characters, and all characters that can be used to form decimal-radix numbers, e.g. U+0660, ARABIC-INDIC DIGIT ZERO. Here's an [interesting story](http://chris.improbable.org/2014/8/25/adventures-in-unicode-digits/) related to this behavior of Python.

* `'abc'.count('') == 4`. Here's an approximate implementation of `count` method, which would make the things more clear
  ```py
  def count(s, sub):
      result = 0
      for i in range(len(s) + 1 - len(sub)):
          result += (s[i:i + len(sub)] == sub)
      return result
  ```
  The behavior is due to the matching of empty substring(`''`) with slices of length 0 in the original string.

---

# Contributing

All patches are Welcome! Please see [CONTRIBUTING.md](/CONTRIBUTING.md) for further details.

For discussions, you can either create a new [issue](https://github.com/satwikkansal/wtfpython/issues/new) or ping on the Gitter [channel](https://gitter.im/wtfpython/Lobby)

# Acknowledgements

The idea and design for this collection were initially inspired by Denys Dovhan's awesome project [wtfjs](https://github.com/denysdovhan/wtfjs). The overwhelming support by the community gave it the shape it is in right now.

#### Some nice Links!
* https://www.youtube.com/watch?v=sH4XF6pKKmk
* https://www.reddit.com/r/Python/comments/3cu6ej/what_are_some_wtf_things_about_python
* https://sopython.com/wiki/Common_Gotchas_In_Python
* https://stackoverflow.com/questions/530530/python-2-x-gotchas-and-landmines
* https://stackoverflow.com/questions/1011431/common-pitfalls-in-python
* https://www.python.org/doc/humor/
* https://www.satwikkansal.xyz/archives/posts/python/My-Python-archives/

# 🎓 License

[![CC 4.0][license-image]][license-url]

&copy; [Satwik Kansal](https://satwikkansal.xyz)

[license-url]: http://www.wtfpl.net
[license-image]: https://img.shields.io/badge/License-WTFPL%202.0-lightgrey.svg?style=flat-square

## Help

If you have any wtfs, ideas or suggestions, please share.

## Want to surprise your geeky pythonist friends?

You can recommend wtfpython to your friends on Twitter and Linkedin by using these quick links,

[Twitter](https://twitter.com/intent/tweet?url=https://github.com/satwikkansal/wtfpython&hastags=python,wtfpython)
 | [Linkedin](https://www.linkedin.com/shareArticle?url=https://github.com/satwikkansal&title=What%20the%20f*ck%20Python!&summary=An%20interesting%20collection%20of%20subtle%20and%20tricky%20Python%20snippets.)

## Need a pdf version?

I've received a few requests for the pdf version of wtfpython. You can add your details [here](https://satwikkansal.xyz/wtfpython-pdf/) to get the pdf as soon as it is finished.

## Follow Commit

[![Commit id][commit-image]][commit-url]

[commit-url]: https://github.com/satwikkansal/wtfpython/commit/145a194c8b138ee0f71593fef63290df601df8fb
[commit-image]: https://img.shields.io/badge/Commit-145a194-yellow.svg
