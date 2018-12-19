# 批量删除远程分支

```
  git fetch --prune 
  git branch -r --merged |
  grep origin |
  grep -v '>' | 
  grep -v master | 
  xargs -L1 | 
  awk '{split($0,a,"/"); print a[2]}' | 
  xargs git push origin --delete
```

# 参考
- [https://gist.github.com/schacon/942899](https://gist.github.com/schacon/942899)