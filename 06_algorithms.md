# SQLPython

### inner function

`is_integer()` 和 `isinstance(x, int)` 是 Python 中用于类型检查的两种不同方法，但它们的用途和应用场景有所不同。下面是它们的详细对比：

#### 1. **`is_integer()`**

- **用途**：用于检查一个浮点数是否是整数。
- **返回值**：如果一个浮点数的值是整数（例如 5.0），`is_integer()` 返回 `True`，否则返回 `False`。它的返回值是布尔值。
- **适用类型**：只适用于浮点数（`float`）。如果你对一个整数调用它，会引发 `AttributeError`。

##### 示例：

```python
x = 5.0
print(x.is_integer())  # True，因为 5.0 是一个整数

x = 5.5
print(x.is_integer())  # False，因为 5.5 不是一个整数

x = 5
# print(x.is_integer())  # 会引发 AttributeError，因为整数没有 is_integer 方法
```

#### 2. **`isinstance(x, int)`**

- **用途**：用于检查 `x` 是否是某个特定类型的实例，常用于判断一个对象是否是指定类（如 `int`）的实例。
- **返回值**：返回布尔值 `True` 或 `False`。如果 `x` 是 `int` 类型的实例，返回 `True`，否则返回 `False`。
- **适用类型**：适用于任何对象，`isinstance()` 可以用于判断对象是否属于特定类型或其子类。

##### 示例：

```python
x = 5
print(isinstance(x, int))  # True，因为 x 是整数

x = 5.0
print(isinstance(x, int))  # False，因为 x 是浮点数

x = "hello"
print(isinstance(x, int))  # False，因为 x 是字符串
```

#### 区别总结：

| **方法**             | **用途**                                | **适用类型**          | **返回值**                                         |
| -------------------- | --------------------------------------- | --------------------- | -------------------------------------------------- |
| `is_integer()`       | 检查浮点数是否是整数（例如 5.0）        | 只适用于 `float` 类型 | 如果是整数，则返回 `True`，否则返回 `False`        |
| `isinstance(x, int)` | 判断对象是否是 `int` 类型（包括其子类） | 适用于任何类型的对象  | 如果是 `int` 类型，则返回 `True`，否则返回 `False` |











# 递归 Recursion

### *Game: bean machine* 

![](assets\06_algorithms\001.png)

Balls are dropped from the opening of the board. Every time a ball hits a nail, it has a 50% chance of falling to the left or to the right. The piles of balls are accumulated in the slots at the bottom of the board.

Write a program that simulates the bean machine. Your program should prompt the user to enter the number of the balls and the number of the slots in the machine. 

Simulate the falling of each ball by printing its path. For example, the path for the ball in Figure 7.13b is LLRRLLR and the path for the ball in Figure 7.13c is RLRRLRR. Display the final build up of the balls in the slots in a histogram. Here is a sample run of the program:

```java
Enter the number of balls to drop: 5
Enter the number of slots in the bean machine: 8
LRLRLRR
RRLLLRR
LLRLLRR
RRLLLLL
LRLRRLR
    O
    O
  OOO
```



 (*Hint*: Create an array named **slots**. Each element in **slots** stores the number of balls in a slot. Each ball falls into a slot via a path. The number of Rs in a path is the position of the slot where the ball falls. For example, for the path LRLRLRR, the ball falls into **slots[4]**, and for the path is RRLLLLL, the ball falls into **slots[2]**.)

1. a 50% chance of falling to L or R:

   ```javascript
   int LR = (int) Math.random() * 2; //生成0, 1 随机数
   if (LR == 0) path[ballnum][i] = "L";
   else path[ballnum][i] = "R";
   ```

2. the number of slots

   ```java
   int slotNum; // the number of slots
   // 层数：slotNum - 1, 即每个小球循环slotNum - 1次
   ```

   

3. int[] bean(int[] a, int n)

   ```java
   int[] bean(int[] a,int n)
   {
       // Each ball falls into a slot via a path.
       // 创建char path[][]存储小球每次的LR
       for(int i = 0; i < n - 1; i++)
           1.
   }
   ```

   

4. 

5. 

6. 

7. 

8. 

9. 

10. 

11. 

12. 





format code: ctrl + alt + L

multiple cursors and selection: shift + alt + click



### 概念

1. 直接或间接调用自身的算法

2. ```
   P = if B then Q else β(S, P)
   ```

3. 每个递归函数都必须由非递归函数定义的初始值，否则无法计算



***



## EXAMPLES

每个递归函数都可拆分成以下三步：

1. 明确函数输入、返回

2. 明确终止条件

3. 寻找递归关系

   

#### 阶乘

input: 非负整数n
output: n!

```c++
int factorial(int n)
{
    if (n == 0) return 1; // 0!=1
    else return factorial(n - 1) * n;
}
```



#### Fibonacci

input: 非负整数n
output: 第n个Fibonacci数

```c++
int Fibonacci(int n)
{
    if (n <= 2) return 1;
    else return Fibonacci(n - 1) + Fibonacci(n - 2);
}
```



#### Hanoi 塔

input: 非负整数n
output: null, 仅实现将n个圆盘从一个塔座移动到另一塔座

```c++
void Hanoi(int n, int a, int b, int c)
{//将n个圆盘借助c, 从a移到b
    if(n > 0)
    {
        Hanoi(n-1, a, c, b);//将n-1个圆盘借助b, 从a移到c
        move(a, b);         //将第n个圆盘从a移到b
        Hanoi(n-1, c, b, a);//将n-1个圆盘借助a, 从c移到b
    }
}
```



#### 整数划分

input: 非负整数n
output: n所在数组的下标 

```c++
void Hanoi(int n, int a, int b, int c)
{//将n个圆盘借助c, 从a移到b
    if(n > 0)
    {
        Hanoi(n-1, a, c, b);//将n-1个圆盘借助b, 从a移到c
        move(a, b);         //将第n个圆盘从a移到b
        Hanoi(n-1, c, b, a);//将n-1个圆盘借助a, 从c移到b
    }
}
```



#### 整数划分

input: 正整数n，m
output: n的m划分数

```c++
void equation(int n, int m)
{//n的m划分的个数为f(n, m)
    if(n == 1 || m == 1) return 1;
    
}
```



#### 青蛙跳台阶

前提：青蛙可1次跳1级台阶或2级台阶

input: 非负整数n
output: n级台阶的跳法总数





# Coding Practices

## Deletion from a Circular Linked List

### 3 circumstances

1. head

   ```c++
   
   ```

   

2. last

   ```c++
   
   ```

   

3. specific

   ```c++
   
   ```



```c++
/*
Given a Circular Linked List. The task is to delete the given node, key in the circular linked list, and reverse the circular linked list.

Note:

You don't have to print anything, just return the head of the modified list in each function.
Nodes may consist of Duplicate values.
The key may or may not be present.
Examples:

Input: Linked List: 2->5->7->8->10, key = 8
Output: 10->7->5->2
Explanation: After deleting 8 from the given circular linked list, it has elements as 2, 5, 7, 10. Now, reversing this list will result in 10, 7, 5, 2 & the resultant list is also circular.*/

//{ Driver Code Starts
#include <bits/stdc++.h>
using namespace std;

// Structure for the linked list node
struct Node
{
    int data;
    struct Node *next;

    Node(int x)
    {
        data = x;
        next = NULL;
    }
};

// Function to print nodes in a given circular linked list
void printList(struct Node *head)
{
    if (head != NULL)
    {
        struct Node *temp = head;
        do
        {
            cout << temp->data << " ";
            temp = temp->next;
        } while (temp != head);
    }
    else
    {
        cout << "empty" << endl;
    }
    cout << endl;
}

// } Driver Code Ends
class Solution
{
public:
    // Function to reverse a circular linked list
    Node *reverse(Node *head)
    {
        // code here
        Node *p = head;
        while (p->next != NULL)
        {
            Node *tmp = p->next;
            p->next = p;
            p = tmp;
        }
        return p->next;
    }
    // Function to delete a node from the circular linked list
    Node *deleteNode(Node *head, int key)
    {
        // code here
        Node *p = head;
        // // delete head node
        // if (head->data == key)
        //     while (p->next == head)
        //     {
        //         p->next = NULL;
        //         Node *tmp = head->next;
        //         head->next = NULL;
        //         return tmp;
        //     }
        while (p->next != NULL)
        {
            if (p->next->data == key)
            {
                Node *tmp = p->next;
                p->next->next = NULL;
                p->next = tmp->next;
            }
            p = p->next;
        }
        return head;
    }
};
class Solution {
  public:
    // Function to reverse a circular linked list
    Node* reverse(Node* head) {
        if (head == NULL || head->next == head)
            return head;

        Node* prev = NULL;
        Node* current = head;
        Node* next;
        Node* init = head;

        do {
            next = current->next;
            current->next = prev;
            prev = current;
            current = next;
        } while (current != init);

        head->next = prev;
        head = prev;
        return head;
    }

    // Function to delete a node from the circular linked list
    Node* deleteNode(Node* head, int key) {
        if (head == NULL)
            return head;

        Node* current = head;
        Node* prev = NULL;

        // Finding the node to delete
        while (current->data != key) {
            if (current->next == head) {
                // Node with key not found in the list
                return head;
            }
            prev = current;
            current = current->next;
        }

        // Case 1: Only one node in the list
        if (current == head && current->next == head) {
            head = NULL;
            return head;
        }

        // Case 2: Deleting the head node
        if (current == head) {
            prev = head;
            while (prev->next != head) {
                prev = prev->next;
            }
            head = current->next;
            prev->next = head;
        }
        // Case 3: Deleting the last node
        else if (current->next == head) {
            prev->next = head;
        }
        // Case 4: Deleting a node in between
        else {
            prev->next = current->next;
        }

        return head;
    }
};

int main()
{
    int t;
    cin >> t;
    cin.ignore();

    while (t--)
    {
        vector<int> arr;
        string input;
        getline(cin, input);
        stringstream ss(input);
        int number;

        // Reading input into a vector
        while (ss >> number)
        {
            arr.push_back(number);
        }

        int key;
        cin >> key;
        cin.ignore();

        // Creating the circular linked list
        struct Node *head = new Node(arr[0]);
        struct Node *tail = head;
        for (int i = 1; i < arr.size(); ++i)
        {
            tail->next = new Node(arr[i]);
            tail = tail->next;
        }
        tail->next = head; // Make the list circular

        Solution ob;

        // Delete the node with the given key
        head = ob.deleteNode(head, key);

        // Reverse the circular linked list
        head = ob.reverse(head);

        // Print the modified list
        printList(head);
    }
    return 0;
}

// } Driver Code Ends
```



```c++
class Solution {
  public:
    // Function to reverse a circular linked list
    Node* reverse(Node* head) {
        Node *i=head;
        Node *nxt;
        Node *pre=NULL;
        do{
            nxt=i->next;
            i->next=pre;
            pre=i;
            i=nxt;
        } while(i!=head);
        i->next=pre;
        head=pre;
        return head;
    }

    // Function to delete a node from the circular linked list
    Node* deleteNode(Node* head, int key) {
        if(!head)return head;
        Node *i=head;
        while(i->data!=key){
            i=i->next;
            if(i==head)break;
        }
        if(i->data==key){
            i->data=i->next->data;
            i->next=i->next->next;
        }
        return head;
    }
};
```





## 007

#### `for ( : )` 

In the range-based for loop, you don't need to manually manage an index (like in a traditional `for` loop). Instead, you directly work with the elements of the container.

```cpp
for (data_type variable : container) {
    // code to process each element
}
```

Where:
- `data_type` is the type of elements in the container (in this case, `int` for `vector<int>`).
- `variable` is a reference to each element in the container during the loop iteration.
- `container` is the collection you want to iterate over, like a `vector<int>`.

##### example

```c++
vector<int> arr = {1, 2, 3, 4};
for (int i : arr)
	cout << i << endl;
```



### Heap Sort

[Heap Sort](https://www.geeksforgeeks.org/heap-sort/)

First convert the array into a [max heap](https://www.geeksforgeeks.org/introduction-to-max-heap-data-structure/) using ***heapify***, Please note that this happens in-place. The array elements are re-arranged to follow heap properties. Then one by one delete the root node of the Max-heap and replace it with the last node and ***heapify***. Repeat this process while size of heap is greater than 1.

- Rearrange array elements so that they form a Max Heap.
- Repeat the following steps until the heap contains only one element:
  - Swap the root element of the heap (which is the largest element in current heap) with the last element of the heap.
  - Remove the last element of the heap (which is now in the correct position). We mainly reduce heap size and do not remove element from the actual array.
  - Heapify the remaining elements of the heap.
- Finally we get sorted array.

### ***Detailed Working of Heap Sort***

#### Step 1: Treat the Array as a Complete Binary Tree

We first need to visualize the array as a ***complete binary tree***. For an array of size ***n***, the root is at index ***0***, the left child of an element at index ***i*** is at ***2i + 1***, and the right child is at ***2i + 2***.

#### Step 2: Build a Max Heap

#### Step 3: Sort the array by placing largest element at end of unsorted array.

In the illustration above, we have shown some steps to sort the array. We need to keep repeating these steps until there’s only one element left in the heap.

### Implementation of Heap Sort

```c++
// C++ program for implementation of Heap Sort using vector

#include <bits/stdc++.h>
using namespace std;

// To heapify a subtree rooted with node i
// which is an index in arr[].
void heapify(vector<int>& arr, int n, int i){

    // Initialize largest as root
    int largest = i;

    // left index = 2*i + 1
    int l = 2 * i + 1;

    // right index = 2*i + 2
    int r = 2 * i + 2;

    // If left child is larger than root
    if (l < n && arr[l] > arr[largest])
        largest = l;

    // If right child is larger than largest so far
    if (r < n && arr[r] > arr[largest])
        largest = r;

    // If largest is not root
    if (largest != i) {
        swap(arr[i], arr[largest]);

        // Recursively heapify the affected sub-tree
        heapify(arr, n, largest);
    }
}

// Main function to do heap sort
void heapSort(vector<int>& arr){
    int n = arr.size();

    // Build heap (rearrange vector)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // One by one extract an element from heap
    for (int i = n - 1; i > 0; i--) {

        // Move current root to end
        swap(arr[0], arr[i]);

        // Call max heapify on the reduced heap
        heapify(arr, i, 0);
    }
}

// A utility function to print vector of size n
void printArray(vector<int>& arr){
    for (int i = 0; i < arr.size(); ++i)
        cout << arr[i] << " ";
    cout << "\n";
}

// Driver's code
int main(){
    vector<int> arr = { 9, 4, 3, 8, 10, 2, 5 };

    // Function call
    heapSort(arr);

    cout << "Sorted array is \n";
    printArray(arr);
}
```

### 堆排序算法

首先使用 ***heapify*** 将数组转换为[最大堆](https://www.geeksforgeeks.org/introduction-to-max-heap-data-structure/)，注意，这个操作是**就地**完成的。数组元素将被重新排列以满足堆的性质。然后逐个删除最大堆的根节点，并用最后一个节点替换根节点，再进行 ***heapify***。在堆大小大于1时重复此过程。

- 重新排列数组元素使其形成最大堆。
- 当堆只剩一个元素时，重复以下步骤：
  - 将堆的根元素（即当前堆中的最大元素）与堆的最后一个元素交换。
  - 删除堆的最后一个元素（该元素现已处于正确位置）。此过程主要是减小堆的大小，而不是从数组中真正删除元素。
  - 对剩余的堆元素进行堆化操作。
- 最终得到的是一个已排序的数组。

### 堆排序的详细过程

#### 第一步：将数组视为完全二叉树

首先需要将数组可视化为一个***完全二叉树***。对于大小为 ***n*** 的数组，根节点位于索引 ***0***，索引 ***i*** 的元素的左子节点为 ***2i + 1***，右子节点为 ***2i + 2***。

#### 第二步：构建最大堆

#### 第三步：通过将最大元素放置在未排序数组的末尾来排序数组

在上述示例中，我们展示了一些排序数组的步骤。需要重复这些步骤，直到堆中只剩一个元素。

### 堆排序的实现

```c++
// 使用 vector 实现堆排序的 C++ 程序

#include <bits/stdc++.h>
using namespace std;

// 堆化以节点 i 为根的子树，i 是 arr[] 中的索引
void heapify(vector<int>& arr, int n, int i){

    // 初始化最大值为根
    int largest = i;

    // 左子节点索引 = 2*i + 1
    int l = 2 * i + 1;

    // 右子节点索引 = 2*i + 2
    int r = 2 * i + 2;

    // 如果左子节点大于根
    if (l < n && arr[l] > arr[largest])
        largest = l;

    // 如果右子节点大于目前的最大值
    if (r < n && arr[r] > arr[largest])
        largest = r;

    // 如果最大值不是根
    if (largest != i) {
        swap(arr[i], arr[largest]);

        // 递归堆化受影响的子树
        heapify(arr, n, largest);
    }
}

// 堆排序的主函数
void heapSort(vector<int>& arr){
    int n = arr.size();

    // 构建堆（重新排列 vector）
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // 逐个提取堆中的元素
    for (int i = n - 1; i > 0; i--) {

        // 将当前根移动到末尾
        swap(arr[0], arr[i]);

        // 对缩小后的堆进行最大堆化
        heapify(arr, i, 0);
    }
}

// 用于打印大小为 n 的 vector 的实用函数
void printArray(vector<int>& arr){
    for (int i = 0; i < arr.size(); ++i)
        cout << arr[i] << " ";
    cout << "\n";
}

// 主函数
int main(){
    vector<int> arr = { 9, 4, 3, 8, 10, 2, 5 };

    // 调用堆排序函数
    heapSort(arr);

    cout << "排序后的数组为 \n";
    printArray(arr);
}
```



### Complexity Analysis of ***Heap Sort***

***Time Complexity:*** O(n log n)
***Auxiliary Space:*** O(log n), due to the recursive call stack. However, auxiliary space can be O(1) for iterative implementation.

### ***Important points about Heap Sort***

- Heap sort is an in-place algorithm.
- Its typical implementation is not stable but can be made stable (See [this](https://www.geeksforgeeks.org/stability-in-sorting-algorithms/))
- Typically 2-3 times slower than well-implemented [QuickSort](http://www.geeksforgeeks.org/quick-sort/). The reason for slowness is a lack of locality of reference.

### ***Advantages of Heap Sort***

- ***Efficient Time Complexity:*** Heap Sort has a time complexity of O(n log n) in all cases. This makes it efficient for sorting large datasets. The ***log n*** factor comes from the height of the binary heap, and it ensures that the algorithm maintains good performance even with a large number of elements.
- ***Memory Usage:*** Memory usage can be minimal (by writing an iterative heapify() instead of a recursive one). So apart from what is necessary to hold the initial list of items to be sorted, it needs no additional memory space to work
- ***Simplicity:*** It is simpler to understand than other equally efficient sorting algorithms because it does not use advanced computer science concepts such as recursion.

### Disadvantages of Heap Sort

- ***Costly***: Heap sort is costly as the constants are higher compared to merge sort even if the time complexity is O(n Log n) for both.
- ***Unstable***: Heap sort is unstable. It might rearrange the relative order.
- ***Inefficient:*** Heap Sort is not very efficient because of the high constants in the time complexity.

### Frequently Asked Question (FAQs) on Heap Sort

#### *What are the two phases of Heap Sort?*

>  The heap sort algorithm consists of two phases. In the first phase, the array is converted into a max heap. And in the second phase, the highest element is removed (i.e., the one at the tree root) and the remaining elements are used to create a new max heap. 



## 011_Zero_Sum

要求查找动态数组内是否有能够使和为 0 的三元组，若有则按升序返回三元组的下标

```c++
class Solution {
  public:
    vector<vector<int>> findTriplets(vector<int> &arr) {
        // Code here
    }
};

// 返回一个动态数组型的动态数组
```



### 解题思路

1. 标答：使用 `unordered_map`, 存储每个和 (key) 及其对应计算数字下标 (value)
2. 参考：使用 `unordered_map`, 存储每个数字 (key) 及其对应下标 (value)

#### 哈希容器

> 基于**哈希表**实现的容器
>
> `unordered_map`: 存储键值对，类似于 `python` 字典。每个元素有一个唯一的键 (key) 和 值 (value) 组成
>
> `unordered_set`: 存储键，里面存储的每个元素都是唯一的，确保不会存储到重复元素

```c++
unordered_map<int, string> = map;
map[0] = "a", "aa";
map[1] = "b", "bb";

cout << map[0] << endl;
cout << map[0] << endl;
```



### Ans

#### 1. 标答

```c++
// User function Template for C++
class Solution {
  public:
    vector<vector<int>> findTriplets(vector<int> &arr) {
        // Set to handle duplicates
        set<vector<int>> resSet;
        int n = arr.size();
        unordered_map<int, vector<pair<int, int>>> mp;

        // Store sum of all the pairs with their indices
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++)
                mp[arr[i] + arr[j]].push_back({i, j});
        }

        for (int i = 0; i < n; i++) {
            // Find remaining value to get zero sum
            int rem = -arr[i];
            
            // 存在第三个数使得和为0，则进入if
            if (mp.find(rem) != mp.end()) {
                vector<pair<int, int>> pairs = mp[rem];
                
                // 对于条件中的和，遍历能够计算出该和的每一对下标
                for (auto p : pairs) {
                    // Ensure no two indices are same in triplet
                    // 这些下标不相等时，则加入到结果集合中
                    if (p.first != i && p.second != i) {
                        vector<int> curr = {i, p.first, p.second};
                        // 题目要求下标有序
                        sort(curr.begin(), curr.end());
                        resSet.insert(curr);
                    }
                }
            }
        }

        vector<vector<int>> res(resSet.begin(), resSet.end());
        return res;
    }
};
```



#### 2. 参考

无法分析出该算法的时间复杂度为 $O(n^2)$, 怎么看都是 $O(n^3)$

```c++
// User function Template for C++
class Solution {
  public:
    vector<vector<int>> findTriplets(vector<int> &arr) {
        // Code here
        // To store the result triplets
        vector<vector<int>> ans;
        // Hashmap to store each element and its indices
        unordered_map<int, vector<int>> mp;

        // Step 1: Populate the hashmap with each element and its corresponding index
        for(int i = 0; i < arr.size(); ++i) {
            mp[arr[i]].push_back(i);
        }

        // Step 2: Iterate through each pair (i, j) using two nested loops
        for(int i = 0; i < arr.size(); ++i) {
            for(int j = i + 1; j < arr.size(); ++j) {
                // Calculate the sum of the current pair
                int tt = arr[i] + arr[j];
                // Calculate the required third element to make the sum zero
                int req = -tt;

                // Check if the required element exists in the hashmap
                if(mp.find(req) != mp.end()) {
                    // Iterate over all indices of the required element
                    for(int x : mp[req]) { 
                        // Ensure that the indices satisfy i < j < k
                        // if(x != i && x != j && i < j && j < x) {
                        // just one constraintion is enough
                        if(j < x) {
                            // Form the triplet
                            vector<int> temp = {i, j, x};
                            // Add the triplet to the result
                            ans.push_back(temp);
                        }
                    }
                }
            }
        }

        return ans; // Return all the valid triplets
    }
};
```





## 012 Rotate

### my solution

```c++
void rotate(vector<vector<int>>& mat) {
    // Your code goes here
    int n = mat.size();
    for (int i = 0; i < n; i++) {
        for (int j = n - 1; j >= 0; j--) {
            // 每行从末尾 push 与行号相同的列元素
            mat[i].push_back(mat[j][i]);
        }
    }

    for (int i = 0; i < n; i++)
        mat[i].erase(mat[i].begin(), mat[i].begin()+n);
}
```



### reference

#### 01

```c++
void rotate(vector<vector<int> >& mat) {
    // Your code goes here
    // Reverse -> Transpose
    reverse(mat.begin(),mat.end()); // reverse
    // Transpose
    for(int i=0;i<mat.size()-1;i++){
        for(int j = i+1;j<mat.size();j++)
            swap(mat[i][j],mat[j][i]);
    }
}
```

![011](assets\06_algorithms\011.png)



02

```c++
void rotate(vector<vector<int> >& mat) {
       int n = mat.size();

    // Consider all cycles one by one
    for (int i = 0; i < n / 2; i++) {

        // Consider elements in group of 4 as P1, P2, P3 & P4 in current square
        for (int j = i; j < n - i - 1; j++) {

            // Swap elements in clockwise order
            int temp = mat[i][j];
            mat[i][j] = mat[n - 1 - j][i];                 // Move P4 to P1
            mat[n - 1 - j][i] = mat[n - 1 - i][n - 1 - j]; // Move P3 to P4
            mat[n - 1 - i][n - 1 - j] = mat[j][n - 1 - i]; // Move P2 to P3
            mat[j][n - 1 - i] = temp;                      // Move P1 to P2
        }
    }
}
```





## 013

### 1 my solution

貌似 **formal** 的 version 1

简化版

```c++
class Solution {
  public:
    int treePathsSum(Node *root) {
        // code here.
        return search_leaf(root, 0);
    }

    int search_leaf(Node *n, int sum) {
        sum = sum*10 + n->data;
        int l_sum = 0;
        int r_sum = 0;
        if(n->left) l_sum = search_leaf(n->left, sum);
        if(n->right) r_sum = search_leaf(n->right, sum);

        // 叶子结点时返回sum
        if(!l_sum && !r_sum) return sum;

        return l_sum + r_sum;
    }
};
```

冗余余余余余余余余余余余余版

```c++
class Solution {
  public:
    int treePathsSum(Node *root) {
        // code here.
        int sum = root->data;
        int l = 0;
        int r = 0;
        // 左右子树非空，则进入搜索
        if(root->left) l = search_leaf(root->left, sum);
        if(root->right) r = search_leaf(root->right, sum);

        return l+r;
    }

    int search_leaf(Node *n, int sum) {
        // 当前累计和
        sum = sum*10 + n->data;
        int l_sum = 0;
        int r_sum = 0;
        if(n->left) l_sum = search_leaf(n->left, sum);
        if(n->right) r_sum = search_leaf(n->right, sum);

        // 叶子结点时返回sum，因为此时 l_sum 和 r_sum 都为 0
        if(!l_sum && !r_sum) return sum;

        // 非叶子结点时返回左右子树累计和，不需要再＋到目前为止的和
        return l_sum + r_sum;
    }
};
```



### 2 formal

### 01

The idea is to do a **[preorder traversal](https://www.geeksforgeeks.org/preorder-traversal-of-binary-tree/)** of the tree. In the preorder traversal, keep track of the **value** calculated till the **current** node. For every node, we update the value as value 10 plus the node’s data. On reaching a **leaf node**, return the value calculated so far.

Below is the implementation of the above approach:

```c++
class Solution {
    // Helper function to calculate the sum of all root-to-leaf path numbers
    int treePathsSumUtil(Node *root, int val) {
        // Base case: if the current node is null, return 0
        if (root == NULL)
            return 0;

        // Update the current value by shifting the previous value (val)
        // one digit to the left and adding the current node's data
        val = (val * 10 + root->data);

        // If the current node is a leaf, return the accumulated value (a complete path
        // number)
        if (root->left == NULL && root->right == NULL)
            return val;

        // Recur for both left and right subtrees and sum the values
        return treePathsSumUtil(root->left, val) + treePathsSumUtil(root->right, val);
    }

  public:
    // Function to initiate the tree path sum calculation
    int treePathsSum(Node *root) {
        // Start with the root node and an initial value of 0
        return treePathsSumUtil(root, 0);
    }
};
```



```c++
class Solution {
  public:
    int treePathsSum(Node *root) {
        // code here.
        if (root == nullptr) return 0;
    
    // Store pair of node and value
    // associated with it.
    stack<pair<Node*,int>> st;
    st.push({root, 0});
    
    int ans = 0;
    
    while (!st.empty()) {
        pair<Node*,int> top = st.top();
        st.pop();
        Node* curr = top.first;
        int val = top.second;
        
        // update the value
        val = val*10 + curr->data;
        
        // if current node is leaf node, 
        // then add the value to result.
        if (curr->left == nullptr && curr->right == nullptr) {
            ans += val;  
            continue;
        }
        
        if (curr->right != nullptr) {
            st.push({curr->right, val});
        }
        
        if (curr->left != nullptr) {
            st.push({curr->left, val});
        }
    }
    
    return ans;
    }
};
```





# Merge Sort

1. **Divide**: Merge sort takes an array (or list of numbers) and **divides** it into two smaller halves, again and again, until each piece has only one number.
2. **Conquer (Merge)**: Then, it **merges** these smaller pieces back together, comparing the numbers and arranging them in the correct order.
3. **Combine**: After merging the pieces, the entire array is sorted.

Now, let’s think about how much time it takes for merge sort to complete, by calculating the time needed at each stage of dividing and merging.

### Step-by-Step Calculation of Time Complexity

#### 1. **Dividing the Array**
- **How many times do we divide the array?**
  
   - Imagine you have an array with `n` numbers (e.g., 8 numbers). The first step divides the array into **two halves** (4 numbers each), then those halves are divided into two again (2 numbers each), and this continues until each piece has just **1 number**.
   - If we keep cutting the array into halves, how many times do we have to do this? This is related to **logarithms**. The number of times you can divide something in half is the **logarithm** of `n` to the base 2, which is written as `log₂(n)`. But you don't need to worry too much about the math notation for now—just remember that dividing in half again and again happens around **log₂(n)** times.
   
   Example: For an array of 8 numbers, you divide:
   1. From 8 to two halves of 4.
   2. Then from 4 to two halves of 2.
   3. Then from 2 to two halves of 1.
   
   That’s **3 steps**, and the number of divisions is related to `log₂(n)`, where `n = 8` in this case.

#### 2. **Merging the Array**
- **How much time does merging take?**
   - After you have divided the array into single numbers, you start merging them back together. Every time you merge two small arrays (or halves), you are comparing the numbers and arranging them in order.
   - If you have `n` numbers in total, each time you merge two halves, you have to compare **all `n` numbers** once.
   - This happens at every level of dividing (or "cutting in half"). So if you divided the array 3 times (as in the example above), you also have to merge the numbers back together **3 times**, and each time it takes `n` comparisons.

#### 3. **Putting It Together**
- **Total work done by merge sort**:
   - In merge sort, the array is divided around **log₂(n)** times. Each time, merging takes **n** steps (because you're comparing all `n` numbers).
   - So, for each level of dividing the array, the merging part takes **n** steps. Since there are about **log₂(n)** levels of division, the total time is:
     \[
     \text{Total Time} = n \times \log₂(n)
     \]
   - This is where the time complexity of **O(n log n)** comes from. It means that merge sort grows **almost linearly** but a little slower than pure linear (O(n)) algorithms.

### Step-by-Step Example:
Let’s look at a concrete example to make this even clearer:

- **Example**: Suppose you have an array of **8 numbers**: `[38, 27, 43, 3, 9, 82, 10, 47]`.

#### 1. **Divide (Splitting the Array)**
   - First, you divide the array into halves:
     - `[38, 27, 43, 3]` and `[9, 82, 10, 47]`.
   - Then, divide these halves again:
     - `[38, 27]`, `[43, 3]`, `[9, 82]`, `[10, 47]`.
   - Finally, divide again until you have just single numbers:
     - `[38]`, `[27]`, `[43]`, `[3]`, `[9]`, `[82]`, `[10]`, `[47]`.

   **Number of divisions = 3 steps** (since `log₂(8) = 3`).

#### 2. **Conquer (Merging the Array)**
   - Now, you start merging:
     1. Merge `[38]` and `[27]` → `[27, 38]`
     2. Merge `[43]` and `[3]` → `[3, 43]`
     3. Merge `[9]` and `[82]` → `[9, 82]`
     4. Merge `[10]` and `[47]` → `[10, 47]`

   - Next, merge the next level:
     1. Merge `[27, 38]` and `[3, 43]` → `[3, 27, 38, 43]`
     2. Merge `[9, 82]` and `[10, 47]` → `[9, 10, 47, 82]`

   - Finally, merge the last two halves:
     - Merge `[3, 27, 38, 43]` and `[9, 10, 47, 82]` → `[3, 9, 10, 27, 38, 43, 47, 82]`.

#### 3. **Total Comparisons**:
   - At each level of merging, you are comparing and sorting **n = 8** numbers. There are 3 levels (since we divided 3 times), so the total number of comparisons is roughly `8 × 3 = 24`.

### Conclusion:
- **Dividing** takes about **log₂(n)** steps.
- **Merging** takes **n** steps at each level.
- Total time complexity = `O(n log n)`, which means that as the number of elements (`n`) grows, the time it takes grows **almost linearly**, but with a factor of `log n` due to the repeated divisions.

I hope this step-by-step explanation helps you understand the time complexity of merge sort! Let me know if you'd like further clarification.



# Bottom