# 文件查找与替换

- find 通过文件名查找

  ```bash
  find . -name abc.html  # 当前路径查找 abc.html
  ```
- grep 通过内容查找

  ```bash
  grep -rl aaabbb .   # 当前路径查找文件内容包含 aaabbb 的文件
  git grep -l aaabbb  # 用 git grep 命令查找
  ```
- sed 替换
  
  ```bash
  sed -i "" 's/aaabbb/aaabbb1/g' abc.html    # abc.html 中的 aaabbb 替换为 aaabbb1
  git grep -l aaabbb | xargs sed -i "" 's/aaabbb/aaabbb1/g'
  grep -rl aaabbb . | xargs sed -i "" 's/aaabbb/aaabbb1/g'
  ```
  
  > sed 在 macOS 中要加 ""
