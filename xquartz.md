# XQuartz

当在 `vagrant` 中运行 `bocsh` 使用 `x11` 转发时。会提示一些错误。使用如下配置可以解决。

> 配置当中似乎少了`--no-rehash`。目前使用频率和方案都有变化，暂时也不深入了

```bash
if which rbenv > /dev/null
    rbenv init - fish | source
end
```

