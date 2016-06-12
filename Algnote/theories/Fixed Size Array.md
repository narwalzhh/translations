## 固定大小数组（定长数组）

如果你写代码，那么你对数组一定不会陌生。在许多编程语言中，例如：Java，数组经常是指定长数组，也就是为这个数组分配的空间是固定不变的。在Java中，可以使用以下方式初始化一个数组：
```java
// the following examples all initialize arrays with size of 3
int[] arr = new int[3];

// or (less preferred)
int arr[] = new int[3];

// or
int[] arr = {v0, v1, v2};

// or (less preferred)
int arr[] = {v0, v1, v2};

// int[] arr is more preferable than int arr[] is because that the we could
//tell that arr is an array type(int[]) directly. Otherwise, they hava no
//difference
```

下面是初始化二维数组的例子：
```java
// the following examples all initialize arrays with size of 3*2
int[][] arr = new int[3][2]

// or (less preferred)
int arr[][] = new int[3][2];

// or
int[][] arr = {{v01, v02}, {v11, v12}, {v21, v22}};

// or (less preferred)
int arr[][] = {{v01, v02}, {v11, v12}, {v21, v22}}; 
```

## 使用一维数组表示二维数组

我们可以通过一个一维数组来表示一个二维数组，对于一个大小为`3 * 4`的二维数组来说，我们可以初始化一个大小为12的一维数组来表示它。然后，我们能够使用一维数组的索引来计算二维数组的行索引和列索引。下面就是例子： 
```java
int[] nums1 = {0, 1, 2, 3, 4, 5};

// here we use a 1D array with size 6 to represent a 2D array of size 3*2 say 
//nums[3][2] = {{0, 1},
//              {2, 3},
//              {4, 5}};

// to get an item nums2[2][1] we could convert it to nums2[2*rowSize + 
// columnIndex] = nums1[2*2+1]  = nums1[5] = 5

int item = nums1[2*2+1];

// if we know the index of the item in the 1D array, we could get column and 
// row index by the following:

// nums1[i] = nums2[i/rowSize][i%rowSize]
// nums1[5] = nums2[5/2][5%2] = nums2[2][1]
```

## 性能

在大多数语言中，定长数组可能是速度最快的数据结构。对于像根据索引`getting/setting`值这样的操作，它能够在`O(1)`的时间内完成。

```java
// the following statements have O(1) time performance

// arr is an array of size 10
int i = arr[9];
arr[10] = 26;

// arr2 is a 2D array of size 6*6
arr2[4][5] = 9;
int j = arr2[4][5]
```

## 定长数组的缺点

定长数组的主要缺点是数组的大小需要预定义出来，因此如果数据的大小能够给发生改变，我们经常需要定义一个超出实际大小的数组，并且使用一个变量来获取当前数据集的长度。

下面的代码很烂，但是却能够给出在大多数情况下人们使用数组的方式，非常不幸：

```java
int[] arr = new Type[100000000];
arr[0] = 1;
int currentSize = 1;

// the array only has 1 useful value but the size is pre-defined as 10000000
// so it is very inefficient on memory space

// In Java, the length of an array cam simply be retrieved by arr.length
```

在下一节点中，我们将会介绍动态大小数组。它使用一种自适应的技巧来解决数组大小的限制。

维护数组中元素的位置是非常不灵活的，举个例子，如果要在数组中删除或插入值，那么它的时间复杂度是`O(n)`。

```java
// insert value 9 to the attr[19] spot of the array and keep the order of 
// other elements

// move all the later elements to one spot after. It takes up to O(n) time to 
// process this

for (int i = currentSize - 1; i >= 19; i--) {
    arr[i + 1] = arr[i];
}

// now set the value
arr[19] = 9;
```

