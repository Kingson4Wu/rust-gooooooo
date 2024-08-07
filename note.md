### install
+ `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

### cmd
<pre>
build your project with cargo build
run your project with cargo run
test your project with cargo test
build documentation for your project with cargo doc
publish a library to crates.io with cargo publish
</pre>

+ Rust 还具有一个称为 Cargo 的构建系统和软件包管理器。Cargo 处理许多任务，例如构建代码、下载库或依赖项等等。这两者捆绑在一起，因此在安装 Rust 时会得到 Cargo。

### Generating a new project

+ `cargo new hello-rust`

+ `cargo build`
+ `cargo run`
+ `cargo release`
+ `cargo update`

---

### cargo.lock

Ensuring Reproducible Builds with the Cargo.lock File
Cargo has a mechanism that ensures you can rebuild the same artifact every time you or anyone else builds your code: Cargo will use only the versions of the dependencies you specified until you indicate otherwise. For example, say that next week version 0.8.4 of the rand crate comes out, and that version contains an important bug fix, but it also contains a regression that will break your code. To handle this, Rust creates the Cargo.lock file the first time you run cargo build, so we now have this in the guessing_game directory.

When you build a project for the first time, Cargo figures out all the versions of the dependencies that fit the criteria and then writes them to the Cargo.lock file. When you build your project in the future, Cargo will see that the Cargo.lock file exists and use the versions specified there rather than doing all the work of figuring out versions again. This lets you have a reproducible build automatically. In other words, your project will remain at 0.8.3 until you explicitly upgrade, thanks to the Cargo.lock file.

---


+ 连续6年最受欢迎的语言当然不是浪得虚名。 无GC、效率高、工程性强、强安全性以及能同时得到工程派和学院派认可, 这些令Rust拥有了自己的特色和生存空间，社区的友善，生态的快速发展，大公司的重仓跟进，一切的一切都在说明Rust的未来。
+ Rust 是一种系统编程语言，旨在取代 C 和 C++ 开发。Rust 提供了和 C 和 C++ 匹敌的性能，但是使用起来更加友好。
+ Rust在运行性能上各个方面的性能都要比Go好不少，Rust也没有GC，所以不存在Stop the world`问题，再加上Rust更容易做一些底层优化：
+ 运行快Rust速度惊人且内存利用率极高。Rust没有运行时，没有垃圾收集器，有很快的运行速度可以在嵌入式设备上运行，还能轻松和其他语言集成。

+ 学习Rust，目的并不是为了写web，而是为了写桌面（哪怕是命令行工具）、写系统应用，看中的是Rust的跨平台和性能优势，同样也是看中了能够绕过C和C++的学习成本。！！！


+ https://blog.csdn.net/kenkao/article/details/111039693
+ Rust语言的一个重要特点就是没有一个厚重的运行时，所以也就没有GC这样的运行时的设施。坏处是我们得花精力学习在无GC情况下的设计，就是我们这一讲想做到的事情。好处是，轻量，可以用于系统编程，代码可以跑在裸机上，而不是一套运行时环境上。这样，理论上，Rust编译的代码可以像C和C++语言一样轻，可以用于嵌入式系统级软件开发，比如IoT设备上。做为对比的是Go语言，它有一个运行时，写应用的话Go很可能会胜出，但是在写系统级软件时，这个运行时环境可能就不是最理想的基础设施了。

+ Rust同C++一样，存储空间既有堆，也有栈。对象放在栈上，可以复制，也可以随着退栈而被自动销毁掉。在C引入malloc之前，要么是静态分配，要么是在栈上分配，并没有复杂的堆上内存泄漏的难题。而以Java为代表的一类语言，默认都是在堆上分配对象，所以需要GC来实现堆上的管理。

+ rust 所宣称的没有运行时（“without runtime”）的理解应该是没有单独的运行时环境。可以理解为内存的管理在编译期就已经确定。
+ go这样实现了协程的语言也有对应的运行时，语言需要负责协程的调度以及IO事件的管理。

### Rust之ownership
+ 一些语言中（如JAVA）具有垃圾回收机制，在程序运行时不断地寻找不再使用的内存；在另一些语言（如C）中，程序员必须亲自分配和释放内存。Rust 则选择了第三种方式：通过ownership系统管理内存，编译器在编译时会根据一系列的规则进行检查。在运行时，ownership（所有权）系统的任何功能都不会减慢程序。

+ 什么是ownership？有什么特征？（所有权规则）
Rust 中的每一个值都有一个被称为其所有者（owner）的变量
值有且只有一个所有者
当所有者（变量）离开作用域，这个值将被丢弃
很显然，这里就是回收的触发点


作者：躺在家里干活
链接：https://www.jianshu.com/p/dd6b67df9202
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

### 所有权与借用 + 生命周期
Rust是通过什么手段回收已经不再使用的内存呢？
那就是所有权机制，和借用规则，并将这种机制和规则在编译期就检测出来。

除了生命周期以外，还有变量的作用域生命周期，通过let这个操作符，可以直接开辟一个当前变量的作用域，该变量只能存活在这个作用域里，除了let，还有其他的一些操作符，都可以单独开辟一个作用域，所有的代码都是有作用域的，都是有生命周期的，Rust统一了变量的生命周期。


---


+ 基于 Rust 编写的实用命令行工具：<https://juejin.cn/post/6937929298913263646>
+ https://lib.rs/command-line-utilities

---

https://zhuanlan.zhihu.com/p/110379613

Rust 编译缓慢的根由在于语言的设计。
我的意思并非是此乃 Rust 语言的设计目标。正如语言设计者们相互争论时经常说的那样，编程语言的设计总是充满了各种权衡。其中最主要的权衡就是：运行时性能和编译时性能。而 Rust 团队几乎总是选择运行时而非编译时。

因此，Rust 编译时间很慢。这有点让人恼火，因为 Rust 在其他方面的表现都非常好，唯独 Rust 编译时间却表现如此糟糕。

---

Rust 学习资料、书籍分享 
原创roseduan roseduan写字的地方 
Rust 是近些年来非常火热的语言之一了，但也是公认的上手难，为了帮助一些想要学习的同学，这里分享一些我在学习 Rust 的过程当中，接触到的一些不错的资料。
* 官方的 rust book https://doc.rust-lang.org/book/title-page.html
* 官方 rust 死灵书 https://doc.rust-lang.org/nomicon/intro.html
* 通过例子学 Rust https://rustwiki.org/zh-CN/rust-by-example/index.html
* 官方 rustlings 小练习 https://rustlings.cool/
* Rust 语言圣经 https://course.rs/basic/intro.html
* Google 出的 Rust 教程 https://google.github.io/comprehensive-rust/welcome.html
* Rust 程序设计语言 https://kaisery.github.io/trpl-zh-cn/title-page.html
* Rust 原子操作和锁 https://marabos.nl/atomics/
* Rust 原子和锁—中文翻译 https://atomics.rs/about-book.html
* Awesome-rust rust 相关资料、第三方库列表 https://github.com/rust-unofficial/awesome-rust
* Learn Rust Easy 一本中文入门书 https://rustycab.github.io/LearnRustEasy/
* 书籍、博客、视频
    * 《Rust 编程之道》
    * 《Rust 权威指南》
    * 《Rust 程序设计·第二版》
    * 《深入理解 Rust 并发编程》
    * 《Rust 实战》
    * 《The Rust Programming Language》
    * 《Rust For Rustaceans》
    * 《Programming Rust—Fast, Safe Systems Development》
    * 《Command-Line Rust》
    * 《Rust Crash Course》
    * 《Systems Programming Rust》
    * 《Rust Atomics and Locks》
    * The Week in Rust https://this-week-in-rust.org/
    * Rust 语言中文社区 https://rustcc.cn/

以上书籍可以在公众号领取，后台回复关键字「rust」即可。
ps. 最近在 B 站发布了我的第一个露脸的视频，欢迎各位捧个场点个赞，今年会继续在视频领域持续创作（公众号当然也不会落下）。

我的 B 站主页：
https://space.bilibili.com/26194591
