
# 理解算法复杂度和大O表示法的一种简单方式

## 理解使用大O表示法描述算法的时间和空间复杂度

 大O表示法是用来描述算法复杂度(即，算法的执行时间或是在运行过程中占用的内存或磁盘的大小)的一种应用最为广泛的方法。通常在面试或考试时，你会被问及一些关于算法复杂度的问题，比如：一个算法使用了大小为n的数据结构，那么这个算法的时间和空间的复杂度是多少？对于这一类问题的回答，通常使用大O表示法，比如：`O(1)`, `O(n)`, `O(n^2)`或者`O(log(n))`。

## 使用大O表示法描述时间复杂度

在这里，我们不想使用数学的方式来讨论大O的问题，基本上，当分析一个算法的时间赋值度时，我们使用大O表示法粗略的估计了完成这个算法所需要的“步骤”，来看下面的例子：

```
void fun(int n) {

    // part 1
    doSomething();

    // part 2
    for (int j = 0; j < n; j++) {
        doSomething();
    }

    // part 3
    for (int i = 0; i< n; i++) {
        for (int j = 0; j < n; j++) {
            doSomething();
        }
    }

    // part 4
    return ;
}
```

在这我们假设要完成`doSomething`需要`C`步。整个方法拥有 4 部分，对于不同的参数`n`，每个部分的时间复杂度是多少呢？

对于第一步：它只是执行了`doSomething()`，因此，它需要`C`步，这里的`C`是独立于`n`的。当时间复杂的独立于参数是，我们使用`O(1)`来表示。

对于第二步：它执行了`n`次`doSomething()`，每次执行`doSomething()`需要`C`步，因此，总的它需要`C * n`步来完成此步骤。正如上面提到的，我们使用`O(1)`表示完成`C`步。那么对于`C * n`，复杂度就变成了`n * O(1)`。这里有个重要的规则就是`a * O(n) = O(an)`。在这种情况下，`n * O(1) = O(n)`，因此第二步的时间复杂度就是`O(n)`。

对于第三步：它拥有两个循环，内层的循环和第二步是一模一样的。外层循环又执行了第二步的`n`倍，因此，第三步的时间复杂度是`n * O(n)`，也就是`O(n^2)`。

对于第四步：它就执行了`1`步就返回了，因此，时间复杂度是`O(1)`。

所以，整个方法的的总的时间复杂度是多少呢？很简单，我们只需把4部分的时间复杂度加起来就可以了：

`O(1) + O(n) + O(n^2) + O(1)`

现在，我们假设`n`变得非常非常大，对于第一步和第四步，它们依旧执行`C + 1`(常量)步，所以，它们运行的时间可以被第二步和第三步忽略掉，因为第三步和第四步要比第一步和第四步执行更长的时间。现在，我们来比较一下第二步和第三步，当`n = 1`时，步骤二和步骤三都执行`C`步；当`n = 3`时，步骤二需要执行`3C`步，而步骤三则需要执行`9C`步；当`n = 1000`时，步骤二需要`1000C`步，但是步骤三却需要`1000000C`步！随着`n`的增加，步骤三的时间复杂度增加的步骤二要快的多。当`n`变得非常非常极限大时，步骤二的耗时就可以被步骤三的耗时忽略掉了。

因此，我们又得出了另一条规则，当增加大O表示法中的符号时，增长速度慢的符号可以被增长速度快的符号忽略掉。正如我们看到的，`O(1)`不会增长，所以它就可以被`O(n)`忽略掉，`O(n)`的增长速度慢于`O(n^2)`,所以`O(n)`就可以被`O(n^2)`忽略掉，因此整个`fun(n)`算法的时间复杂度就是`O(n^2)`。

## 大O表示法的规则总结

由以上的例子，我们可以总结出一下几条规则：
对于两个大O符号`O(A) O(B)`相乘，结果是`O(AB)`，例如：
`O(1) * O(n) = O(n)`
`O(n) * O(n) = O(n^2)`
`O(1) + O(n) = O(n)`
`O(n) + O(n^2) = O(n^2)`
`O(1) + O(n) + O(n^2) = O(n^2)`

下面是不同大O符号的增长速度的比较：
`O(1) < O(log(n)) < O(n) < O(nlog(n)) < O(n^2)`

## 怎样使用大O表达式比较算法的复杂度，为什么？

### 实在是不理解，有大神看到可以给翻译一下！！！

When comparing different algorithms，we often say the one with a “smaller” big O notation is more efficient. However, there are situations that algorithms with “smaller” big O is faster. For example, there are two algorithms `f1(n)` and `f2(n)`. `f1(n)` takes `100` steps and `f2(n)` takes `n` steps so `f1(n)` is `O(1)` and `f2(n)` is `O(n)`. When `n` is less than `100`, `f1(n)` is more efficient than `f2(n)`. However, big O compares when `n` goes to extremely(or infinite) large. When `n` goes up to `10000`, `f2(n)` becomes way more efficient. As the nature of large scale data in computer engineering, it makes more sense to compare algotithms in the cases that the data is very large. 

##  使用大O表示法描述空间复杂度

使用大O表示法估计时间复杂度是很好理解的，因为它更具体。例如，在一个算法中，在我们得出具体结果之前，需要创建一个大小为`n`的数组来存储临时结果。如果我们假设数组中元素的大小是一个常量`C`，并且这个常量是独立于`n`，那么这个数组的空间复杂度就是`Cn`，也就是`O(n) * O(C) = O(n) * O(1) = O(n)`。

当比较不同的算法时，我们经常会比较需要多少额外的空间复杂度才能解决这个问题。举个例子，一个需要额外大小为`n`的数组的算法并不比一个只需要两个变量的算法好，`O(1)`表示的空间复杂度比`O(n)`表示的有效率多了。
