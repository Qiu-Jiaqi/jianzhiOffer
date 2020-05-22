## 题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

注意：保证测试中不会当栈为空的时候，对栈调用pop()或者min()或者top()方法。



## 题解

emmmmmm，我记得是用两个栈的方法，但是首先写了一个很奇怪的方法。

用 min 记录最小值，pop 出去后又重新找一次最小值。。。

```java
import java.util.Stack;

public class Solution {

    private Stack<Integer> stack = new Stack<>();
    private int min = Integer.MAX_VALUE;

    public void push(int node) {
        stack.push(node);
        if (node < min) {
            min = node;
        }
    }

    public void pop() {
        if (stack.pop() == min) {
            min = stack.peek();
            for (int node : stack) {
                if (node < min) {
                    min = node;
                }
            }
        }
    }

    public int top() {
        return stack.peek();
    }

    public int min() {
        return min;
    }
}
```



两个栈的方法：minStack 只存比当前栈顶值小的即可，取出时最小值的时候同时取出。

```java
import java.util.Stack;

public class Solution {

    private Stack<Integer> stack = new Stack<>();
    private Stack<Integer> minStack = new Stack<>();
    
    public void push(int node) {
        stack.push(node);
        if (minStack.isEmpty() || minStack.peek() >= node) {
            minStack.push(node);
        }
    }
    
    public void pop() {
        if (stack.pop() == minStack.peek()) {
            minStack.pop();
        }
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        return minStack.peek();
    }
}
```

