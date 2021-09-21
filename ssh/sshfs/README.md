## Mount EOS

```
sshfs -o allow_other,kernel_cache,auto_cache,no_readahead,ServerAliveInterval=15,ServerAliveCountMax=2 adlintul@lxplus.cern.ch:/eos/user/a/adlintul eos_mount
```

You need `allow_other` to mount folder to a Docker container.