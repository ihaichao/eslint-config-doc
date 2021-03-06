# for-direction
> 禁止 for 循环出现方向错误的循环，比如 `for (i = 0; i < 10; i--)`

# getter-return
> getter 必须有返回值，并且禁止返回空，比如 `return`;

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
> 禁止将 `await` 写在循环里，因为这样就无法同时发送多个异步请求了  
> @off 要求太严格了，有时需要在循环中写 `await`

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
> 禁止使用 `console`  
> @off `console` 的使用很常见

# no-debugger
> @fixable 禁止使用 `debugger`

# no-dupe-args
> 禁止在函数参数中出现重复名称的参数

# no-dupe-keys
> 禁止在对象字面量中出现重复名称的键名

# no-duplicate-case
> 禁止在 `switch` 语句中出现重复测试表达式的 case

# no-empty
> 禁止出现空代码块，允许 `catch` 为空代码块

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
> @fixable 禁止不必要的布尔类型转换，比如 !! 或 `Boolean`

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
> @fixable 禁止函数表达式中出现多余的括号，比如 `let foo = (function () { return 1 })`

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
> @fixable 禁止出现多余的分号

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
> 禁止在 `RegExp` 构造函数中出现非法的正则表达式

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
> 禁止将 `Math`, `JSON` 或 `Reflect` 直接作为函数调用

# no-prototype-builtins
> 禁止使用 `hasOwnProperty`, `isPrototypeOf` 或 `propertyIsEnumerable`  
> @off `hasOwnProperty` 比较常用

# no-regex-spaces
> @fixable 禁止在正则表达式中出现连续的空格，必须使用 `/foo {3}bar/` 代替

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
> 禁止在数组中出现连续的逗号，如 `let foo = [,,]`

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
> 禁止在 `return`, `throw`, `break` 或 `continue` 之后还有代码

# no-unsafe-finally
> 禁止在 `finally` 中出现 `return`, `throw`, `break` 或 `continue`

# no-unsafe-negation
> @fixable 禁止在 `in` 或 `instanceof` 操作符的左侧使用感叹号

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
> 使用 `isNaN(foo)` 而不是 `foo === NaN`

# valid-jsdoc
> 注释必须符合 jsdoc 的规范  
> @off jsdoc 要求太严格

# valid-typeof
> typeof 表达式比较的对象必须是 'undefined', 'object', 'boolean', 'number', 'string', 'function' 或 'symbol'

# accessor-pairs
> `setter` 必须有对应的 `getter`，`getter` 可以没有对应的 `setter`

# array-callback-return
> 数组的方法除了 `forEach` 之外，回调函数必须有返回值

# block-scoped-var
> 将 `var` 定义的变量视为块作用域，禁止在块外使用

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
> 在类的非静态方法中，必须存在对 `this` 的引用  
> @off 太严格了

# complexity
> 禁止函数的[循环复杂度](https://en.wikipedia.org/wiki/Cyclomatic_complexity)超过 20

# consistent-return
> 禁止函数在不同分支返回不同类型的值  
> @off 太严格了

# curly
> @fixable if 后面必须要有 {，除非是单行 if

# default-case
> `switch` 语句必须有 `default`  
> @off 太严格了

# dot-location
> @fixable 链式调用的时候，点号必须放在第二行开头处，禁止放在第一行结尾处

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
> 禁止出现 `foo['bar']`，必须写成 `foo.bar`  
> @off 两种写法都可以

# eqeqeq
> 必须使用 === 或 !==，禁止使用 == 或 !=，与 `null` 比较时除外

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
> `for in` 内部必须有 `hasOwnProperty`  
> @off `for in` 内部不是必须要有 `hasOwnProperty` 

# no-alert
> 禁止使用 `alert`  
> @off `alert` 很常用

# no-caller
> 禁止使用 `caller` 或 `callee`

# no-case-declarations
> switch 的 `case` 内有变量定义的时候，必须使用大括号将 `case` 内变成一个代码块

# no-div-regex
> 禁止在正则表达式中出现形似除法操作符的开头，如 `let a = /=foo/`  
> @off 有代码高亮的话，在阅读这种代码时，也完全不会产生歧义或理解上的困难

# no-else-return
> @fixable 禁止在 `else` 内使用 `return`，必须改为提前结束  
> @off `else` 中使用 `return` 可以接受

# no-empty-function
> 不允许有空函数，除非是将一个空函数设置为某个项的默认值

# no-empty-pattern
> 禁止解构中出现空 {} 或 []

# no-eq-null
> 禁止使用 foo == null 或 foo != null，必须使用 foo === null 或 foo !== null  
> @off foo == null 用于判断 foo 不是 undefined 并且不是 null，比较常用，故允许此写法

#no-eval
> 禁止使用 `eval`

#no-extend-native
> 禁止修改原生对象

#no-extra-bind
> @fixable 禁止出现没必要的 `bind`

#no-extra-label
> @fixable 禁止出现没必要的 `label`

#no-fallthrough
> `switch` 的 `case` 内必须有 `break`, `return` 或 `throw`

#no-floating-decimal
> @fixable 表示小数时，禁止省略 0，比如 .5

#no-global-assign
> 禁止对全局变量赋值

# no-implicit-coercion
> @fixable 禁止使用 !! ~ 等难以理解的运算符, 仅允许使用 !!

错误示例：
```javascript
// bad 使用了 ~ 等难以理解的运算符
let b = ~foo.indexOf('.');
let n = +foo;
let n = 1 * foo;
let s = '' + foo;
foo += ``;
```

正确示例：
```javascript
// good 不使用 ~ 等难以理解的运算符
let b2 = foo.indexOf('.') !== -1;
let n = Number(foo);
let n2 = Number(foo);
let s = String(foo);
foo = String(foo);

// good 可以使用 !!
let b = !!foo;
```

# no-implicit-globals
> 禁止在全局作用域下定义变量或申明函数

# no-implied-eval
> 禁止在 `setTimeout` 或 `setInterval` 中传入字符串，如 `setTimeout('alert("Hi!")', 100)`;

# no-invalid-this
> 禁止在类之外的地方使用 `this`
> @off `this` 的使用很灵活，事件回调中可以表示当前元素，函数也可以先用 `this`，等以后被调用的时候再 `call`

# no-iterator
> 禁止使用 `__iterator__`

# no-labels
> 禁止使用 `label`

# no-lone-blocks
> 禁止使用没必要的 {} 作为代码块

# no-loop-func
> 禁止在循环内的函数中出现循环体条件语句中定义的变量，比如：
> @off 循环内经常使用循环体定义的变量

# no-magic-numbers
> 禁止使用 magic numbers  
> @off 太严格了

# no-multi-spaces
> @fixable 禁止出现连续的多个空格，除非是注释前，或对齐对象的属性、变量定义、`import` 等

# no-multi-str
> 禁止使用 \ 来换行字符串

# no-new
> 禁止直接 `new` 一个类而不赋值

# no-new-func
> 禁止使用 `new Function`，比如 `let x = new Function("a", "b", "return a + b")`;

# no-new-wrappers
> 禁止使用 `new` 来生成 `String`, `Number` 或 `Boolean`

# no-octal
> 禁止使用 0 开头的数字表示八进制数

# no-octal-escape
> 禁止使用八进制的转义符

# no-param-reassign
> 禁止对函数的参数重新赋值

# no-proto
> 禁止使用 __proto__

# no-redeclare
> 禁止重复定义变量

# no-restricted-properties
> 禁止使用指定的对象属性

# no-return-assign
> 禁止在 `return` 语句里赋值

# no-return-await
> 禁止在 `return` 语句里使用 `await`

# no-script-url
> 禁止出现 `location.href = 'javascript:void(0)'`;

# no-self-assign
> 禁止将自己赋值给自己

# no-self-compare
> 禁止将自己与自己比较

# no-sequences
> 禁止使用逗号操作符

# no-throw-literal
> 禁止 `throw` 字面量，必须 `throw` 一个 `Error` 对象

# no-unmodified-loop-condition
> 循环内必须对循环条件的变量有修改

# no-unused-expressions
> 禁止无用的表达式

# no-unused-labels
> @fixable 禁止出现没用的 `label`

# no-useless-call
> 禁止出现没必要的 `call` 或 `apply`

# no-useless-concat
> 禁止出现没必要的字符串连接

# no-useless-escape
> 禁止出现没必要的转义 
> @off 转义可以使代码更易懂

# no-useless-return
> @fixable 禁止没必要的 `return`  
> @off 没必要限制 `return`

# no-void
> 禁止使用 `void`

# no-warning-comments
> 禁止注释中出现 TODO 和 FIXME  
> @off TODO 很常用

# no-with
> 禁止使用 `with`

# prefer-promise-reject-errors
> `Promise` 的 `reject` 中必须传入 `Error` 对象，而不是字面量

# radix
> `parseInt` 必须传入第二个参数

# require-await
> `async` 函数中必须存在 `await` 语句  
> @off `async function` 中没有 `await` 的写法很常见，比如 `koa` 的示例中就有这种用法

# vars-on-top
> `var` 必须在作用域的最前面  
> @off `var` 不在最前面也是很常见的用法

# wrap-iife
> @fixable 立即执行的函数必须符合如下格式 `(function () { alert('Hello') })()`

# yoda
> @fixable 必须使用 `if (foo === 5)` 而不是 `if (5 === foo)`

# strict
> @fixable 禁止使用 'strict';

# init-declarations
> 变量必须在定义的时候赋值  
> @off 先定义后赋值很常见

# no-catch-shadow
>禁止 `catch` 的参数名与定义过的变量重复  
> @off 太严格了

# no-delete-var
> 禁止使用 `delete`  
> @off 太严格了

# no-label-var
> 禁止 label 名称与定义过的变量重复

# no-restricted-globals
> 禁止使用指定的全局变量  
> @off 它用于限制某个具体的变量名不能使用

# no-shadow
> 禁止变量名与上层作用域内的定义过的变量重复  
> @off 很多时候函数的形参和传参是同名的

# no-shadow-restricted-names
> 禁止使用保留字作为变量名

# no-undef
> 禁止使用未定义的变量

# no-undef-init
> @fixable 禁止将 `undefined` 赋值给变量

# no-undefined
> 禁止对 `undefined` 重新赋值

# no-unused-vars
> 定义过的变量必须使用

# no-use-before-define
> 变量必须先定义后使用

# callback-return
> `callback` 之后必须立即 `return`  
> @off 太严格了

# global-require
> `require` 必须在全局作用域下  
> @off 条件加载很常见

# handle-callback-err
> `callback` 中的 `error` 必须被处理

# no-buffer-constructor
> 禁止直接使用 `Buffer`

# no-mixed-requires
> 相同类型的 `require` 必须放在一起  
> @off 太严格了

# no-new-require
> 禁止直接 `new require('foo')`

# no-path-concat
> 禁止对 `__dirname` 或 `__filename` 使用字符串连接

# no-process-env
> 禁止使用 `process.env.NODE_ENV  `
> @off 使用很常见

# no-process-exit
> 禁止使用 `process.exit(0)`  
> @off 使用很常见

# no-restricted-modules
> 禁止使用指定的模块
> @off 它用于限制某个具体的模块不能使用

# no-sync
> 禁止使用 node 中的同步的方法，比如 `fs.readFileSync`
> @off 使用很常见

# array-bracket-newline
> @fixable 配置数组的中括号内前后的换行格式  
> @off 配置项无法配制成想要的样子

# array-bracket-spacing
> @fixable 数组的括号内的前后禁止有空格

# array-element-newline
> @fixable 配置数组的元素之间的换行格式  
> @off 允许一行包含多个元素，方便大数量的数组的书写

# block-spacing
> @fixable 代码块如果在一行内，那么大括号内的首尾必须有空格，比如 `function () { alert('Hello') }`

# brace-style
> @fixable `if` 与 `else` 的大括号风格必须一致  
> @off `else` 代码块可能前面需要有一行注释

# camelcase
> 变量名必须是 `camelcase` 风格的  
> @off 很多 api 或文件名都不是 `camelcase`

# capitalized-comments
> @fixable 注释的首字母必须大写  
> @off 没必要限制

# comma-dangle
> @fixable 对象的最后一个属性末尾必须有逗号  
> @off 没必要限制

# comma-spacing
> @fixable 逗号前禁止有空格，逗号后必须要有空格

# comma-style
> @fixable 禁止在行首写逗号

# computed-property-spacing
> @fixable 用作对象的计算属性时，中括号内的首尾禁止有空格

# consistent-this
> 限制 `this` 的别名  
> @off 没必要限制

# eol-last
> @fixable 文件最后一行必须有一个空行  
> @off 没必要限制

# func-call-spacing
> @fixable 函数名和执行它的括号之间禁止有空格

# func-name-matching
> 函数赋值给变量的时候，函数名必须与变量名一致

# func-names
> 函数必须有名字  
> @off 没必要限制

# func-style
> 必须只使用函数声明或只使用函数表达式  
> @off 没必要限制

# id-blacklist
> 禁止使用指定的标识符  
> @off 它用于限制某个具体的标识符不能使用

# id-length
> 限制变量名长度  
> @off 没必要限制变量名长度

# id-match
> 限制变量名必须匹配指定的正则表达式  
> @off 没必要限制变量名

# indent
> @fixable 一个缩进必须用四个空格替代

# jsx-quotes
> @fixable jsx 中的属性必须用双引号

# key-spacing
> @fixable 对象字面量中冒号前面禁止有空格，后面必须有空格

# keyword-spacing
> @fixable 关键字前后必须有空格

# line-comment-position
> 单行注释必须写在上一行  
> @off 没必要限制

# linebreak-style
> @fixable 限制换行符为 LF 或 CRLF  
> @off 没必要限制

# lines-around-comment
> @fixable 注释前后必须有空行  
> @off 没必要限制

# max-depth
> 代码块嵌套的深度禁止超过 5 层

# max-len
> 限制一行的长度  
> @off 现在编辑器已经很智能了，不需要限制一行的长度

# max-lines
> 限制一个文件最多的行数  
> @off 没必要限制

# max-nested-callbacks
> 回调函数嵌套禁止超过 3 层，多了请用 `async` `await` 替代

# max-params
> 函数的参数禁止超过 7 个

# max-statements
> 限制函数块中的语句数量  
> @off 没必要限制

# max-statements-per-line
> 限制一行中的语句数量  
> @off 没必要限制

# multiline-ternary
> 三元表达式必须得换行  
> @off 三元表达式可以随意使用

# new-cap
> `new` 后面的类名必须首字母大写

# new-parens
> @fixable `new` 后面的类必须有小括号

# newline-per-chained-call
> 链式调用必须换行  
> @off 没必要限制

# no-array-constructor
> 禁止使用 `Array` 构造函数

# no-bitwise
> 禁止使用位运算  
> @off 位运算很常见

# no-continue
> 禁止使用 `continue`  
> @off `continue` 很常用

# no-inline-comments
> 禁止在代码后添加内联注释  
> @off 内联注释很常用

# no-lonely-if
> @fixable 禁止 `else` 中只有一个单独的 `if`  
> @off 单独的 `if` 可以把逻辑表达的更清楚

# no-mixed-operators
> 禁止混用不同的操作符，比如 `let foo = a && b < 0 || c > 0 || d + 1 === 0`  
> @off 太严格了，可以由使用者自己去判断如何混用操作符

# no-mixed-spaces-and-tabs
> 禁止混用空格和缩进

# no-multi-assign
> 禁止连续赋值，比如 `a = b = c = 5`  
> @off 没必要限制

# no-multiple-empty-lines
> @fixable 禁止出现超过三行的连续空行

# no-negated-condition
> 禁止 if 里面有否定的表达式  
> @off 否定的表达式可以把逻辑表达的更清楚

# no-nested-ternary
> 禁止使用嵌套的三元表达式，比如 `a ? b : c ? d : e`   
> @off 没必要限制

# no-new-object
> 禁止直接 new Object

# no-plusplus
> 禁止使用 ++ 或 --  
> @off 没必要限制

# no-restricted-syntax
> 禁止使用特定的语法  
> @off 它用于限制某个具体的语法不能使用

# no-tabs
> 禁止使用 tabs

# no-ternary
> 禁止使用三元表达式  
> @off 三元表达式很常用

# no-trailing-spaces
> @fixable 禁止行尾有空格

# no-underscore-dangle
> 禁止变量名出现下划线  
> @off 下划线在变量名中很常用

# no-unneeded-ternary
> @fixable 必须使用 `!a` 替代 `a ? false : true`  
> @off 后者表达的更清晰

# no-whitespace-before-property
> @fixable 禁止属性前有空格，比如 `foo. bar()`

# nonblock-statement-body-position
> @fixable 禁止 if 后面不加大括号而写两行代码

# object-curly-newline
> @fixable 大括号内的首尾必须有换行

# object-curly-spacing
> @fixable 对象字面量只有一行时，大括号内的首尾必须有空格

# object-property-newline
> @fixable 对象字面量内的属性每行必须只有一个
> @off 没必要限制

# one-var
> 禁止变量申明时用逗号一次申明多个

# one-var-declaration-per-line
> @fixable 变量申明必须每行一个

# operator-assignment
> @fixable 必须使用 `x = x + y` 而不是 `x += y`  
@off 没必要限制

# operator-linebreak
> @fixable 需要换行的时候，操作符必须放在行末，比如：   
> @off 有时放在第二行开始处更易读

# padded-blocks
> @fixable 代码块首尾必须要空行
> @off 没必要限制

# padding-line-between-statements
> @fixable 限制语句之间的空行规则，比如变量定义完之后必须要空行
> @off 没必要限制

# quote-props
> @fixable 对象字面量的键名禁止用引号括起来
> @off 没必要限制

# quotes
> @fixable 必须使用单引号，禁止使用双引号

# require-jsdoc
> 必须使用 jsdoc 风格的注释  
> @off 太严格了

# semi
> @fixable 结尾必须有分号  
> @off 没有分号更简洁

# semi-spacing
> @fixable 一行有多个语句时，分号前面禁止有空格，分号后面必须有空格

# semi-style
> @fixable 分号必须写在行尾，禁止在行首出现

# sort-keys
> 对象字面量的键名必须排好序  
> @off 没必要限制

# sort-vars
> 变量申明必须排好序  
> @off 没必要限制

# space-before-blocks
> @fixable `if`, `function` 等的大括号之前必须要有空格，比如 `if (a) {`

# space-before-function-paren
> @fixable `function` 的小括号之前必须要有空格

错误示例：
```javascript
@fixable function 的小括号之前必须要有空格

// bad 函数名称后禁止有空格
function foo () {
    console.log('foo');
}

// bad 箭头函数的箭头前后必须有空格
let bar = ()=>{
    console.log('bar');
};
```

```javascript
// good 函数名称后禁止有空格
function foo() {
    console.log('foo');
}

// good 箭头函数的箭头前后必须有空格
let bar = () => {
    console.log('bar');
};

// good 匿名函数的 function 后面不限制有没有空格
bar = function () {
};
bar = function() {
};
```

# space-in-parens
> @fixable 小括号内的首尾禁止有空格

# space-infix-ops
> @fixable 操作符左右必须有空格，比如 `let sum = 1 + 2`;

# space-unary-ops
> @fixable `new`, `typeof` 等后面必须有空格，++, -- 等禁止有空格

# spaced-comment
> @fixable 注释的斜线或 * 后必须有空格

# switch-colon-spacing
> @fixable `case` 的冒号前禁止有空格，冒号后必须有空格

# template-tag-spacing
> @fixable 模版字符串的 tag 之后禁止有空格，比如 tag`Hello World`

# unicode-bom
> @fixable 文件开头禁止有 BOM

# wrap-regex
> @fixable 正则表达式必须有括号包起来  
> @off 没必要限制

# arrow-body-style
> @fixable 箭头函数能够省略 `return` 的时候，必须省略，比如必须写成 `() => 0`，禁止写成 `() => { return 0 }` 
> @off 箭头函数的返回值，应该允许灵活设置

# arrow-parens
> @fixable 箭头函数只有一个参数的时候，必须加括号  
> @off 应该允许灵活设置

# arrow-spacing
> @fixable 箭头函数的箭头前后必须有空格

# constructor-super
> `constructor` 中必须有 `super`

# generator-star-spacing
> @fixable `generator` 的 * 前面禁止有空格，后面必须有空格

# no-class-assign
> 禁止对定义过的 `class` 重新赋值

# no-confusing-arrow
> @fixable 禁止出现难以理解的箭头函数，比如 `let x = a => 1 ? 2 : 3`

# no-const-assign
> 禁止对使用 `const` 定义的常量重新赋值

# no-dupe-class-members
> 禁止重复定义类

# no-duplicate-imports
> 禁止重复 `import` 模块

# no-new-symbol
> 禁止使用 `new` 来生成 `Symbol`

# no-restricted-imports
> 禁止 `import` 指定的模块  
> @off 它用于限制某个具体的模块不能使用

# no-this-before-super
> 禁止在 `super` 被调用之前使用 `this` 或 `super`

# no-useless-computed-key
> @fixable 禁止出现没必要的计算键名，比如 `let a = { ['0']: 0 }`;

# no-useless-constructor
> 禁止出现没必要的 `constructor`，比如 `constructor(value) { super(value) }`

# no-useless-rename
> @fixable 禁止解构时出现同样名字的的重命名，比如 `let { foo: foo } = bar`;

# no-var
> @fixable 禁止使用 `var`

# object-shorthand
> @fixable 必须使用 `a = {b}` 而不是 `a = {b: b}`  
> @off 没必要强制要求

# prefer-arrow-callback
> @fixable 必须使用箭头函数作为回调  
> @off 没必要强制要求

# prefer-const
> @fixable 申明后不再被修改的变量必须使用 `const` 来申明  
> @off 没必要强制要求

# prefer-destructuring
> 必须使用解构  
> @off 没必要强制要求

# prefer-numeric-literals
> @fixable 必须使用 0b11111011 而不是 `parseInt('111110111', 2) ` 
> @off 没必要强制要求

# prefer-rest-params
> 必须使用 `...args` 而不是 `arguments`  
> @off 没必要强制要求

# prefer-spread
> @fixable 必须使用 ... 而不是 `apply`，比如 `foo(...args)`  
> @off `apply` 很常用

# prefer-template
> @fixable 必须使用模版字符串而不是字符串连接  
> @off 字符串连接很常用

# require-yield
> `generator` 函数内必须有 `yield`

# rest-spread-spacing
> @fixable ... 的后面禁止有空格

# sort-imports
> @fixable `import` 必须按规则排序  
> @off 没必要强制要求

# symbol-description
> 创建 `Symbol` 时必须传入参数

# template-curly-spacing
> @fixable `${name}` 内的首尾禁止有空格

# yield-star-spacing
> @fixable `yield*` 后面必须要有空格