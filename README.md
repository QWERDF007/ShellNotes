# ShellNotes
## split 

### 分割文件

- 将文件排序后分割 5 份

  ```shell
  sort $FILE | split -n 5

- 将文件分割成 10 份

  ```shell
  split -n 10 $FILE
  ```

- 将文件按每 2 行分割一份

  ```shell
  split -l 2 $FILE
  ```

- 将文件按每 2 MB 分割一份

  ```shell
  split -b 2M  $FILE
  split -b 2MB $FILE
  ```

- 将文件按每 4 KB 分割一份，维持每行的完整性

  ```shell
  split -C 4K   $FILE
  split -C 4096 $FILE
  ```

## du 

### 查看文件夹大小

- 查看当前目录下文件夹大小，深度 1

  ```shell
  du -hd1 .
  ```

- 查看当前目录下文件夹大小，深度 1，从小到大排序

  ```shell
  du -hd1 . | sort -h
  ```

- 查看当前目录下文件夹大小，深度 1，从大到小排序

  ```shell
  du -hd1 . | sort -hr
  ```

## kill 杀进程

- 杀掉进程号 20045 的进程

  ```shell
  kill -9 20045
  ```

- 杀掉包含指定内容的进程

  ```shell
  ps aux | grep "content" | awk '{print $2}' | xargs -I {} kill -9 {}
  ```

## unzip 

### 解压zip文件

- 解压到指定目录

  ```shell
  unzip $XFILE -d $EXDIR
  ```

## sed

### 输出文件指定行

-n 参数仅显示结果

-e 表示执行脚本，可加可不加，不加，脚本要用引号包起来

- 输出文件第 10 行

  ```shell
  sed -n "10p" $FILE
  ```

- 管道符，输出第 20 行

  ```shell
  cat $FILE | sed -n "20p"
  ```

### 删除文件指定行

- 删除文件第 2 到 5 行

  ```shell
  sed '2,5d' $FILE
  ```

- 删除文件第 2 行到最后

  ```shell
  sed '2,$d' $FILE
  ```

- 删除文件中包含 abc 的行

  ```shell
  sed '/abc/d' $FILE
  ```

### 在文件指定行前后添加内容

- 在第 2 行前加入 abc

  ```shell
  sed '2i abc'
  ```

- 在第 3 行后加入 efg

  ```shell
  sed '2aefg'
  ```

### 替换文件指定行

- 替换文件第 2 行为 abc

  ```shell
  sed '2c abc'
  ```

- 替换文件第 2 到第 5 行为 no 2,5，只留下一行 no 2,5

  ```shell
  sed '2,5c no 2,5'
  ```

### 查找内容

- 查找包含 123 的行，仅输出结果

  ```shell
  sed -n '/123/p' $FILE
  ```

- 查找包含 abc 的行，仅输出结果

  ```shell
  sed -n '/abc/p' $FILE
  ```

### 正则匹配

- ls 结果开头加入 pwd

  ```shell
  ls | sed "s:^:`pwd`/:"
  ```

- 替换文件内每行第一个数字为 0，会将连在一起的数字替换成一个 0

  ```shell
  sed "s:[0-9]*:0:" $FILE
  ```

- 替换文件内全部字母为 5

  ```shell
  sed "s:[a-z]:5:g" $FILE
  ```

  

## find

### 查找小于指定大小的文件

- 查找小于 5k 的文件

  ```bash
  find ./ -size -5k
  ```

- 查找大于 5M 的文件

  ```bash
  find ./ -size +5M
  ```

- 查找小于 10k 的文件并删除

  ```bash
  find ./ -size -10k -exec rm {} \;
  ```

  
