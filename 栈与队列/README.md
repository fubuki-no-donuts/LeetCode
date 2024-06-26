
# 队列

FIFO 类型的容器

## `std::queue` in CPP

- [参考链接](https://cplusplus.com/reference/queue/)

默认以 deque 为底层容器实现，所以队列是一个容器适配器 container adaptor

一些常用成员函数：

```cpp
std::queue<type> que;

que.empty();
que.size();

que.front(); // the oldest element
que.back();  // the newest element

que.push();  // insert element at the end
que.pop();   // 最老元素出队
```

# 栈

LIFO 类型的容器

## `std::stack` in CPP

- [参考链接](https://cplusplus.com/reference/stack/stack/?kw=stack)

栈是基于 `deque` 实现的一个模板类，stack 中的元素存放容器底层实现是一个 `deque`
```cpp
template <class T, class Container = deque<T> > class stack;
```

```cpp
std::stack<type> stk;

stk.empty(); // bool empty const; 当stk.size()为0，返回true
stk.size(); // size_type size() const;返回的是底层容器即deque的size
stk.top(); // reference top(); const_reference top() const; 返回顶层元素的引用，调用的是deque的back()
stk.push(value); // void push(const value_type& val); void push(value_type&& val); 新元素是形参val的拷贝，底层调用为deque的push_back()
stk.emplace(value); // template<class... Args> void emplace(Args&&... args); 利用传入的args作为元素构造函数的参数进行新元素构造，底层调用为deque的emplace_back()
stk.pop(); // void pop(); 移除stack的top元素并size-1，这里的top元素为最新的元素，底层调用为deque的pop_back()
stk.swap(other_stk); // void swap(stack& x) noexcept(/*告诉编译期这个函数不会抛出异常，从而进行某些优化*/);函数将*this和传入的x进行交换
```

- 栈内元素必须符合 LIFO 规则，所以**栈不提供走访功能，也没有迭代器**
- 栈的功能，都通过底层容器来实现，并且可以自行指定底层容器，因此**栈一般不被归类为容器，而被归类为 container adapter 容器适配器**
- 

