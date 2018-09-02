# for-direction

> 禁止 for 循环出现方向错误的循环，比如 for (i = 0; i < 10; i--)

# getter-return

> getter 必须有返回值，并且禁止返回空，比如 return;

错误示例：

```javascript
// bad getter 没有返回值，或返回空
let user = {
  get name() {
    // 无返回值
  }
}
class User {
  get name() {
    // 返回空
    return
  }
}
```

正确示例：

```javascript
// good getter 有返回值
let user = {
  get name() {
    return "Alex"
  }
}
class User {
  get name() {
    return this.name
  }
}
```

# no-await-in-loop

> 禁止将 await 写在循环里，因为这样就无法同时发送多个异步请求了  
> @off 要求太严格了，有时需要在循环中写 await

# no-cond-assign

> 禁止在测试表达式中使用赋值语句，除非这个赋值语句被括号包起来了

错误示例：

```javascript
// bad 测试表达式中使用了赋值语句
// 这可能是把 === 误写成了 =
if ((foo = 0)) {
  // do something
}
```

正确示例：

```javascript
// good 在测试表达式中使用 ===
if (foo === 0) {
  // do something
}

// good 使用括号将测试表达式中的赋值语句包起来了
if (bar === (foo = 0)) {
  // do something
}
```

# no-console

> 禁止使用 console  
> @off console 的使用很常见

# no-debugger

> 禁止使用 debugger  
> @fixable

# no-dupe-args

> 禁止在函数参数中出现重复名称的参数

# no-dupe-keys

> 禁止在对象字面量中出现重复名称的键名

# no-duplicate-case

> 禁止在 switch 语句中出现重复测试表达式的 case

# no-empty

> 禁止出现空代码块，允许 catch 为空代码块

错误示例：

```javascript
// bad 出现了空代码块
if (foo) {
}
```

正确示例：

```javascript
// good 空代码块中有注释
if (foo) {
  // do something
}
```

# no-empty-character-class

> 禁止在正则表达式中使用空的字符集 []

错误示例：

```javascript
// bad 正则表达式中使用了空的字符集 []
let reg = /abc[]/
```

正确示例：

```javascript
// good 正则表达式中的字符集不为空
let reg = /abc[a-z]/
```

# no-extra-boolean-cast

> 禁止不必要的布尔类型转换，比如 !! 或 Boolean  
> @fixable 

错误示例：

```javascript
// bad 在测试表达式中使用了 !!
if (!!foo) {
  // do something
}

// bad 在测试表达式中使用了 Boolean
if (Boolean(foo)) {
  // do something
}
```

正确示例：

```javascript
// good 测试表达式中没必要使用 !! 或 Boolean
if (foo) {
  // do something
}
```

# no-extra-parens
> 禁止函数表达式中出现多余的括号，比如 let foo = (function () { return 1 })  
> @fixable

错误示例：

```javascript
// bad 函数表达式中使用了多余的括号
let foo = (function () { return 1 });
```

正确示例：

```javascript
// good 函数表达式中不使用多余的括号
let foo = function () { return 1 };

// good 普通的表达式中允许出现多余的括号
let bar = (a * b) + c;
```

# no-extra-semi
> 禁止出现多余的分号  
> @fixable

错误示例：

```javascript
// bad 出现了多余的分号
let foo = 1;;
function bar() {
    // do something
};
```

正确示例：

```javascript
// good 没有多余的分号
let foo = 1;
function bar() {
    // do something
}
```

# no-func-assign
> 禁止将一个函数声明重新赋值

错误示例：

```javascript
// bad 函数声明被重新赋值了
function foo() {
    // do something
}
foo = 1;
```

正确示例：

```javascript
// good 函数表达式可以被重新赋值
let foo = function() {
    // do something
};
foo = 1;
```

# no-inner-declarations
> 禁止在 if 代码块内出现函数声明

错误示例：

```javascript
// bad if 代码块内出现了函数声明
if (foo) {
    function bar() {
        // do something
    }
}
```

正确示例：

```javascript
// good if 代码块内使用函数表达式而不是函数声明
if (foo) {
    let bar = function () {
        // do something
    };
}
```

# no-invalid-regexp
> 禁止在 RegExp 构造函数中出现非法的正则表达式

错误示例：

```javascript
// bad 在 RegExp 构造函数中出现了非法的正则表达式
let reg1 = new RegExp('[');
let reg2 = new RegExp('.', 'z');
```

正确示例：

```javascript
// good 在 RegExp 构造函数使用合法的正则表达式
let reg1 = new RegExp('[a-z]');
let reg2 = new RegExp('.', 'g');
```

# no-irregular-whitespace
> 禁止使用特殊空白符（比如全角空格），除非是出现在字符串、正则表达式或模版字符串中

# no-obj-calls
> 禁止将 Math, JSON 或 Reflect 直接作为函数调用

# no-prototype-builtins
> 禁止使用 hasOwnProperty, isPrototypeOf 或 propertyIsEnumerable  
> @off hasOwnProperty 比较常用

# no-regex-spaces
> 禁止在正则表达式中出现连续的空格，必须使用 /foo {3}bar/ 代替  
> @fixable

错误示例：

```javascript
// bad 正则表达式中出现了连续的空格
let reg1 = /foo   bar/;
let reg2 = new RegExp('foo   bar');
```

正确示例：

```javascript
// good 正则表达式中的连续空格使用一个空格加大括号来表示
let reg1 = /foo {3}bar/;
let reg2 = new RegExp('foo {3}bar');
```

# no-sparse-arrays
> 禁止在数组中出现连续的逗号，如 let foo = [,,]

# no-template-curly-in-string
> 禁止在普通字符串中出现模版字符串里的变量形式，如 'Hello ${name}!'

# no-unexpected-multiline
> 禁止出现难以理解的多行表达式

错误示例：

```javascript
// bad 出现了难以理解的多行表达式
let foo = bar
[1, 2, 3].forEach(baz);
```

正确示例：

```javascript
// good 避免多行表达式
let foo = bar[1].forEach(baz);

// good 使用分号分隔多行
let foo = bar;
[1, 2, 3].forEach(baz);
```

# no-unreachable
> 禁止在 return, throw, break 或 continue 之后还有代码

# no-unsafe-finally
> 禁止在 finally 中出现 return, throw, break 或 continue

# no-unsafe-negation
> 禁止在 in 或 instanceof 操作符的左侧使用感叹号  
> @fixable

错误示例：

```javascript
// bad 在 in 或 instanceof 操作符的左侧使用感叹号
if (!key in object) {
    // do something
}
if (!obj instanceof SomeClass) {
    // do something
}
```

正确示例：

```javascript
// good 在 in 或 instanceof 操作执行完之后再使用感叹号取非
if (!(key in object)) {
    // do something
}
if (!(obj instanceof SomeClass)) {
    // do something
}
```

# use-isnan
> 使用 isNaN(foo) 而不是 foo === NaN

# valid-jsdoc
> 注释必须符合 jsdoc 的规范  
> @off jsdoc 要求太严格

# valid-typeof
> typeof 表达式比较的对象必须是 'undefined', 'object', 'boolean', 'number', 'string', 'function' 或 'symbol'

# accessor-pairs
> setter 必须有对应的 getter，getter 可以没有对应的 setter

# array-callback-return
> 数组的方法除了 forEach 之外，回调函数必须有返回值

# block-scoped-var
> 将 var 定义的变量视为块作用域，禁止在块外使用

错误示例：

```javascript
// bad if 中定义的 var 在外面被使用了
if (foo) {
    var bar = 1;
}
console.log(bar);
```

正确示例：

```javascript
// good 使用 let 或 const 定义变量，不在 if 中定义变量
let bar;
if (foo) {
    bar = 1;
}
console.log(bar);
```

# class-methods-use-this
> 在类的非静态方法中，必须存在对 this 的引用  
> @off 太严格了

# complexity
> 禁止函数的[循环复杂度](https://en.wikipedia.org/wiki/Cyclomatic_complexity)超过 20

# consistent-return
> 禁止函数在不同分支返回不同类型的值  
> @off 太严格了

# curly
> if 后面必须要有 {，除非是单行 if  
> @fixable

# default-case
> switch 语句必须有 default  
> @off 太严格了

# dot-location
> 链式调用的时候，点号必须放在第二行开头处，禁止放在第一行结尾处  
> @fixable

错误示例：

```javascript
// bad 链式调用时，点号放在了行尾
foo().
    bar().
    baz();
```

正确示例：

```javascript
// good 链式调用时，点号放在了行首
foo()
    .bar()
    .baz();
```

# dot-notation
> 禁止出现 foo['bar']，必须写成 foo.bar  
> @off 两种写法都可以

# eqeqeq
> 必须使用 === 或 !==，禁止使用 == 或 !=，与 null 比较时除外

错误示例：

```javascript
// bad 使用了 ==
if (foo == 1) {
    console.log('foo is 1');
}
```

正确示例：

```javascript
// good 使用了 ===
if (foo === 1) {
    console.log('foo is 1');
}

// good 与 null 比较时，可以使用 == 或 !=
if (foo == null) {
    console.log('foo is null or undefined');
}
```

# guard-for-in
> for in 内部必须有 hasOwnProperty  
> @off for in 内部不是必须要有 hasOwnProperty 

# no-alert
> 禁止使用 alert  
> @off alert 很常用