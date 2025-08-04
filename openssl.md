# ~~OpenSSL~~



本文用于记录变化的内容。随着软件的升级，现在已经可以自动检测



> It is no longer necessary to set RUBY_CONFIGURE_OPTS to explicitly link to Homebrew OpenSSL, since ruby-build will now automatically detect and link to a compatible OpenSSL version.

```bash
export RUBY_CONFIGURE_OPTS="--with-openssl-dir=$(brew --prefix openssl@1.1)"
```



## Ref

* [Revise instructions about openssl@1.1](https://github.com/rbenv/ruby-build/wiki/Home/_compare/6b6274ffa705c27876a3e2a00313dbdd975bfa09?diff=unified&w)
* [Setting RUBY_CONFIGURE_OPTS for OpenSSL no longer necessary](https://github.com/rbenv/ruby-build/wiki/Home/_compare/44fa8a1ede3aa4b0efbd6ae63acb6ef3cf0ffade?diff=split&w)
* [Add note about Ruby 3.1 and OpenSSL](https://github.com/rbenv/ruby-build/wiki/Home/_compare/a899debabdcae20e49b758ba90d6738bd518d70f?diff=split&w)