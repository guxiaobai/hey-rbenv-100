# 全局安装



>  经过多次尝试在服务器上用全局的方式安装, 想让每个用户创建之后就自动拥有一个可以直接运行的Ruby环境。



```
/usr/local/rbenv
```

* https://github.com/zzet/rbenv/blob/master/templates/rbenv_system.sh.j2

---

> * rbenv install 命令找不到(直接安装ruby-build)
>
> * rbenv-china-mirror 未生效(更多plugins测试)

* https://github.com/rbenv/rbenv/blob/0f65ff72b2e6be9468b0321175f7d658751b746b/libexec/rbenv#L80

---

查看源码`RBENV_HOOK_PATH` 变量测试



## Ref

* <https://github.com/zzet/rbenv>