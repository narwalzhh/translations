## Linked Lists

单链表是一种关于节点的数据结构，在单链表中，每前一个节点相关都有都有一个指向后一个节点的引用。下面是Java中单链表的简单实现：

```java
class Node {
    Node next = null;
    int data;

    public Node(int val) {
        data = val;
    }
}

class LinkedList {
    Node head = null;

    ...

    public append(int val) {
        if (head == null) {
            head = new Node(val);    
        } else {
            Node n = head;
            while(n.next != null) {
                n = n.next; 
            } 

            n.next = new Node(val);
        }
    }
}
``` 

在上述的实现中，它仅仅追踪了链表中的头节点。因此，无论什么时候我们想要增加节点，我们需要遍历整个链表才能获取最后的节点（尾节点），而且，它花费了`O(n)`的时间。为了减少追加元素所需时间，我们增加了一个尾节点，这个尾节点指向链表中的最后一个节点，这样就将时间复杂度减少到了`O(1)`。

```java
// LinkedList with tail reference
class LinkedList {
    Node head = null;
    Node tail = null;

    ...

    public append(int val) {
        if (tail == null) {
            head = new Node(val);
            tial = head;
        } else {
            tail.next = new Node(val); 
            tail = tail.next;
        }
    }
}
```

然而，如果我们想要在某个节点后插入节点，我们仍旧需要花费`O(n)`的时间来寻找这个节点。

```java
class LinkedList {

    ...

    public void insertAfter(Node node, int val) {

        if (head == null) {
            return;
        }

        Node n = head;
        wile(n.next != null) {
            if (n == node) {
               /* Node newNode = new Node(val);
                newNode.next = n.next;
                n.next = newNode; */

                Node oldNext = n.next;
                Node newNode = new Node(val);
                n.next = newNode;
                newNode.next = oldNext;

                if (newNode.next == null) {
                    tail = newNode;
                }
                break;
            }
            n = n.next;
        }
    } 
}
```

删除一个节点和插入一个节点相似。在删除一个节点后，我们需要将前一个节点的`next`和删除节点的`next`连接起来（将前一个节点和后一个节点连接起来）。为了获取前一个节点，我们需要从头开始搜索，因为没有引用指向这个节点。

## 双链表（双向链表）

双链表能够很容易的解决上面的问题。对于每一个节点，除了拥有下一个节点的引用外，还会有指向上一个节点的引用。

```java
class Node {
    Node next = null;
    Node previous = null; 
    int data;

    public Node(int val) {
        data = val;
    }
}

public DoubleLinkedList {

    ...

    public class insertAfter(Node node, int val) {

        if (node == null) {
            return;
        }

        Node newNode = new Node(val);

        node.next.previous = newNode; // app上没有这一行，估计是差错
        newNode.next = node.next;
        newNode.previous = node;
        node.next = newNode;
    }

    public void delete(Node node) {
        if (node == null) {
            return;
        }

        // if the node is head 
        if (node.previous == null) {
            head = node.next;
        }

        // if the node is the tail
        if (node.next == null) {
            tail = node.previous;
        }

        if (node.previous != null) {
            node.previous.next = node.next;
        }
        if (node.next != null) {
            node.next.previous = node.previous
        }
    }
}
```

显然，`delete`和`insetAfter`都拥有`O(1)`的性能表现，总的来说，双链表比单链表更加灵活。
