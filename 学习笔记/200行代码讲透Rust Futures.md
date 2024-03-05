# 200行代码讲透Rust Futures

对于并发编程, 有很多解决方案, 常见的方案如下:

- Thread
    - 需要操作系统支持
    - 占内存
    - 有可能不支持
    - 慢
        ```rust
        use std::thread;

        fn main() {
            let handle = thread::spawn(move || {
                // sth
            });
            handle.join().unwrap();
        }
        ```

- Green Thread
    - 调度器是核心(注意, 调度器不是操作系统的一部分, 是我们实现运行时的一部分)
    - 类似rRore的`task`实现

- Callback
    - 所有权问题导致很难编写

- Promise
    - 改进版本的回调

## `Future`

