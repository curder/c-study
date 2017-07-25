# 逻辑运算符

## 逻辑运算符概念
- 有时候，我们需要在多个条件同时成立的时候才能执行某段代码，比如：用户只有同时输入了QQ和密码，才能执行登录代码，如果只输入了QQ或者只输入了密码，就不能执行登录代码。这种情况下，我们就要借助于C语言提供的逻辑运算符。

- C语言中􏰀提供了三种逻辑运算符:
    + &&(与运算)
    + ||(或运算)
    + !(非运算)

> + 逻辑运算的结果只有2个：“真”为1，“假”为0


## 逻辑与

- 格式:
    + “条件A && 条件B”

- 运算结果:
    + 只有当条件A和条件B都成立时，结果才为1，也就是“真”；其余情况的结果都为0，也就是“假”。因此，条件A或条件B只要有一个不成立，结果都为0，也就是“假”
    + 口诀:一假则假

- 逻辑与运算过程
    + 总是先判断条件A是否成立
    + 如果条件A成立，接着再判断条件B是否成立：如果条件B成立，“条件A && 条件B”的结果就为1，即“真”，如果条件B不成立，结果就为0，即“假”
    + 如果条件A不成立，就不会再去判断条件B是否成立：因为条件A已经不成立了，不管条件B如何，“条件A && 条件B”的结果肯定是0，也就是“假”

- 运算过程示例:
    + 逻辑与的结合方向是**“从左至右”**。比如表达式 (a>3) && (a<5)
    + 若a的值是4：先判断a>3，成立；再判断a<5，也成立。因此结果为1
    + 若a的值是2：先判断a>3，不成立，停止判断。因此结果为0
    + 因此，如果a的值在(3, 5)这个范围内，结果就为1；否则，结果就为0

- 使用注意
    + 若想判断a的值是否在(3,5)范围内，千万不能写成 `3<a<5`因为关系运算符的结合方向为“从左往右”。
        *  例如a为2，它会先算3<a，也就是3<2，条件不成立，结果为0。
        *  再与5比较，即0<5，条件成立，结果为1。
        *  因此`3<a<5`的结果为1，条件成立，也就是说当a的值为2时，a的值是在(3,5)范围内的。
        *  这明显是不对的。正确的判断方法是：(a>3) && (a<5)
    + C语言规定：任何非0值都为“真”，只有0才为“假”。因此逻辑与也适用于数值。比如 5 && 4的结果是1，为“真”；-6 && 0的结果是0，为“假”

## 逻辑或

- 格式

    + “条件A || 条件B”

- 运算结果

    + 当条件A或条件B只要有一个成立时（也包括条件A和条件B都成立），结果就为1，也就是“真”；只有当条件A和条件B都不成立时，结果才为0，也就是“假”。

    + 口诀:一真为真

- 逻辑或运算过程

    + 总是先判断条件A是否成立

    + 如果条件A成立，就不会再去判断条件B是否成立：因为条件A已经成立了，不管条件B如何，“条件A || 条件B”的结果肯定是1，也就是“真”

    + 如果条件A不成立，接着再判断条件B是否成立：如果条件B成立，“条件A||条件B”的结果就为1，即“真”，如果条件B不成立，结果就为0，即“假”

- 运算过程示例

    + 逻辑或的结合方向是**“从左至右”**。比如表达式 (a<3) || (a>5)

    + 若a的值是4：先判断a<3，不成立；再判断a>5，也不成立。因此结果为0

    + 若a的值是2：先判断a<3，成立，停止判断。因此结果为1

    + 因此，如果a的值在(-∞, 3)或者(5, +∞)范围内，结果就为1；否则，结果就为0

- 使用注意

    + C语言规定：任何非0值都为“真”，只有0才为“假”。因此逻辑或也适用于数值。比如 5 || 4的结果是1，为“真”；-6 || 0的结果是1，为“真”；0 || 0的结果是0，为“假”


## 逻辑非

- 格式:
    + “! 条件A”


- 运算结果:
    + 其实就是对条件A进行取反：若条件A成立，结果就为0，即“假”；若条件A不成立，结果就为1，即“真”。也就是说：真的变假，假的变真。
    + 口诀:真变假,假变真

- 运算过程示例:
    + 逻辑非的结合方向是**“从右至左”**。比如表达式 ! (a>5)
    + 若a的值是6：先判断a>5，成立，再取反之后的结果为0
    + 若a的值是2：先判断a>3，不成立，再取反之后的结果为1
    + 因此，如果a的值大于5，结果就为0；否则，结果就为1

- 使用注意:
    + 可以多次连续使用逻辑非运算符：!(4>2)结果为0，是“假”，!!(4>2)结果为1，是“真”，!!!(4>2)结果为0，是“假”
    +C语言规定：任何非0值都为“真”，只有0才为“假”。因此，对非0值进行逻辑非!运算的结果都是0，对0值进行逻辑非!运算的结果为1。!5、!6.7、!-9的结果都为0，!0的结果为1
    
    
    
# 逻辑运算符结合性和优先级


## 优先级

```
!(非) // 注意
  ↑
算术运算符
  ↑
关系运算符
  ↑
&&和||  // 注意
  ↑
赋值运算符
```

- 逻辑非优先级

```
int result = !0 + 1;
printf("result = %d", result); // 输出结果: 2
```

>先计算!0等于1
>然后再用计算结果加上1

- 算术运算符与逻辑运算符优先级

```
int result = 3 + 3 && 0 + 1;
//          (3 + 3) && (0 + 1);
printf("result = %d", result); // 输出结果: 1

```
>先计算3+3和0+1等到6和1
>然后6&&1
- 关系运算符与逻辑运算符优先级

```
int result = 3>5 || 2<4 && 6<1;
//          (3>5) || (2<4) && (6<1)
//            0   ||   1   &&  0
//                     1 && 0
printf("result = %d", result); // 输出结果: 0

```

>先计算3>5,2<4,6<1得到结果0,1,0
>再进行逻辑运算0||1得到结果1
>再进行逻辑运算1&&0得到结果0

- 练习

```
3+2<5||6>3
4>3 && !-5>2
```

## 短路问题

- 与短路:&& 只要第一个条件表达为假那么后面的条件表达就不参与运算了

```
int a = 10;
int b = 20;
int result = (a > 19) && (b++ > 6);
printf("a = %d,b = %d, result = %d\n", a, b, result); // 输出结果:a = 10,b = 20, result = 0
```

- 或短路:|| 只要第一个条件表达式为真那么后面的条件表达式就不参与运算了

```
int a = 10;
int b = 20;
int result = (a > 19) || (b++ > 6);
printf("a = %d,b = %d, result = %d\n", a, b, result); // 输出结果:a = 10,b = 21, result = 1
```