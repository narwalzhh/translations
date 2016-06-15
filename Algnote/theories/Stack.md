## Stack

栈是一种对象的容器，它根据后进先出（last-in first-out : LIFO）的原则来插入或者删除元素。在栈中，只允许两种操作：元素的入栈和元素出栈。栈是访问受限的一种数据结构——只能在栈顶增加或者移除元素。`push`操作向栈顶增加一个元素，`pop`操作从栈顶移除一个元素。

这个wiki上的图片演示了LIFO操作（然而，我这里并没有图片！）

这里我们提供了一段简单的代码来实现什么叫栈：

```java
class Stack {
    Node top;
    
    Object pop() {
        if (top != null) {
            Object item = top.data;
            top = top.next;
            return item;
        } 
        return null;
    } 

    void push(Object item) {
        Node t = new Node(item);
        t.next = top;
        top = t;        
    }

    Object peek() {
        return top.data;
    }
}
```

上述实现使用的是链表。事实上，除了栈阻止了从栈顶以下获取元素，它们本质上是一种东西。对于所有的`pop`、`push`和`peek`方法，它们的时间复杂度为`O(1)`。
