## String 和 StringBuffer

在Java中，string 是另一种数组，下面的代码：  

```java
String s = "abc";
```

实际上是定义了一个大小为`4`的数组。每个元素的值为：`'a', 'b', 'c', '\0'(string的结束标志)`。

现在思考一下，我们需要将 string 的 list 串联起来。使用符号`+`，我们能够做到以下：

```java
String concatenate(String[] words) }{
    String sentence = ""; 
    for (String w : words) {
        sentence = sentence + w;
    }
    return sentence;
}
```

所以，上面代码的时间复杂度是多少呢？

在每一次串联过程中，当前 string 的一个新的拷贝就被创建出来，并且两个 string 以字符接字符的形式被拷贝到一起。我们假设每个 string 拥有 `x` 个字符，第一次循环需要拷贝`x`个字符，第二次需要拷贝`2x`个字符，在第`n`次的拷贝中，需要拷贝`nx`个字符，所以，整个代码的时间复杂度是：`O(x + 2x + ... + nx) = O((n(n+1)x)/2) = O((n^2)x) = O(n^2)`。

这绝对不是优化过的解决方案，理想情况下，所有的 string 应该在需要的时候一次性的连接在一起，没有临时的拷贝生成。实现这个想法需要我们要将 string 临时的缓存下来，并在需要的时候将他们拷贝到一个新的 string 中，这就是 string buffer 工作的原理。

下面就是java中 StringBuffer 中的例子：
```java
String concatenate(String[] words) {

    StringBuffer sentence = new StringBuffer();

    for (String w : words) {
        // only add the string to the buffer no string copy will be creted
        sentence.append(w);
    }

    // create only on copy and put all the characters to the new string copy. 
    // the time complexity is 
    // O(numbers of all the characters of all the string)

    return sentence.toString();
}
```




