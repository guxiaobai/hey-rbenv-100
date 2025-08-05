# YJIT（Yet another Just-in-Time compiler）



## 🛠 启用 YJIT 的方式

**编译 Ruby 时启用：**

YJIT 默认已启用（Ruby 3.2+）：

```bash
./configure --enable-yjit
```

 **运行时启用：**

```bash
ruby --yjit my_app.rb
```

也可用环境变量：

```bash
RUBYOPT="--yjit" ruby app.rb
````

**查看是否启用成功：**

```bash
RUBYOPT="--yjit" ruby -v
ruby --yjit -v
# => ruby 3.3.8 (2025-04-09 revision b200bad6cd) +YJIT [x86_64-linux]
```



## 验证 YJIT 是否启用的方法

**✅ 方法一：运行时显示 YJIT 状态（最推荐）**

```bash
ruby --yjit -e "puts RubyVM::YJIT.enabled?"
```

输出为：

- `true` → 说明 YJIT 成功启用。
- `false` → 说明 YJIT 支持但当前未启用。
- 报错 → 说明 YJIT 编译时未包含在 Ruby 中。

------

**✅ 方法二：查看是否包含 `RubyVM::YJIT` 模块**

```bash
ruby -e "puts defined?(RubyVM::YJIT)"
```

- 输出 `"constant"` → 编译时包含了 YJIT。
- 输出 `nil` → 当前 Ruby 不支持 YJIT（可能是没启用或编译时未包含）。

------

**✅ 方法三：检查 Ruby 编译配置** 🌹🌹

```bash
ruby -rrbconfig -e "puts RbConfig::CONFIG.select { |k, _| k.include?('YJIT') }"
```



## 💣编译错误

```bash
make: *** [yjit/yjit.mk:26: yjit/target/release/libyjit.a] Killed
```

通常意味着 **编译进程被系统杀死**，常见原因是 **内存不足（OOM - Out Of Memory）**。


### ✅ 解决方法建议：

**1. 确认内存是否不足**

* 编译 Ruby 的 YJIT 模块会使用较多内存（Rust 编译器 cargo 在构建时开很多线程）。
* 执行以下命令查看最近的内核日志是否有 OOM：

```bash
dmesg | tail -n 50
```

看是否有类似：

```bash
Out of memory: Kill process 12345 (rustc) score 1234 or sacrifice child
```





## Ref



* <https://github.com/Shopify/yjit>
* <https://docs.ruby-lang.org/en/3.4/yjit/yjit_md.html>
