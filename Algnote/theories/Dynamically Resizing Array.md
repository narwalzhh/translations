## 动态大小数组

动态大小数组是一种能够重新改变大小的数组，同时也能够提供时间复杂度为`O(1)`的访问。基本的思想就是当这个数组满了，它会增加自己的大小，经常是增加到当前大小的两倍。Java拥有它自己的动态大小数组的实现，即`ArrayList`。

下面是动态大小数组的参考：
```java
// 仅供参考
public class DynamicArrayOfInt {
    private int[] data;

    public DynamicArrayOfInt() {
        data = new int[i]; 
    }

    public int get(int position) {
        return data[position];
    }

    public void put(int pos, int val) {
        if (pos >= data.length) {

            // if the positon esceeds th original size, set new size to be 
            // 2*positoin
            if (pos >= newSize) {
                newSize = 2*position;
            }

            // initialize a new array
            int[] newData = new int[newSizeo];

            // a method to copy the data in the original array to the new array
            System.arraycopy(data, 0, newData, data.length);

            data = newData;
        }
        data[pos] = val;
    }
}
```

每次将数组扩大为原来的两倍(同时拷贝原数组的数据至新的数组)时，都要花费`O(n)`的时间。但是在大多数情况下，`get/set`操作的时间复杂度依旧是`O(1)`，最坏的情况是内存空间的占用变成了`2n`，空间复杂度变成了`O(n)`。
