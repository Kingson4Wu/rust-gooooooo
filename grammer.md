+ <https://www.rust-lang.org/learn> !!!
+ <https://doc.rust-lang.org/book/>

+ <https://doc.rust-lang.org/stable/rust-by-example/>
+ <https://rust-cli.github.io/book/index.html>
+ <https://doc.rust-lang.org/cargo/index.html> 先学cargo？？？

+ <https://github.com/sunface/rust-course> !!! 
+ https://course.rs/about-book.html

+ 学习 Rust 你需要一个认知框架:<https://zhuanlan.zhihu.com/p/494001676>

+ rust + bpf !!!
https://github.com/ihciah/clean-dns-bpf
https://www.cnblogs.com/jaciots/p/16155257.html todo!!

学习 Rust 你需要一个认知框架:
https://zhuanlan.zhihu.com/p/494001676 !!?

如何开始学习 Rust 语言? - 蒋古申 的回答 - 知乎
https://www.zhihu.com/answer/915365379


C++程序员视角下的Rust语言:<https://mp.weixin.qq.com/s/PqWeXi6ReYaI7W38fT7i4A>

---

Rust和C++一样，没有走内置垃圾回收机制的路子，而是从语言的内在机制上去解决C和C++内存安全和线程安全的痛点。

Rust通过更强大和完善的类型系统和所有权机制，引入了如下核心语言内在机制：

值的唯一所有权
默认内置基本类型的值拷贝语义
默认对象的移动语义（所有权转移）
默认不可变（只读）内存访问
所有权不可变引用
唯一所有权可变引用
跨函数引用的生命周期标注
不支持空指针

---

小结：
Clone用于堆上的类型，需要实现Drop；
Copy用于栈上的类型，复制开销低
数据在堆or栈，取决于是否动态分配（c语言基础）

---



