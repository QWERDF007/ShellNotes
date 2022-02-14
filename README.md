# ShellNotes
## 分割文件

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

## 查看文件夹大小

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

## 杀进程

- 杀掉进程号 20045 的进程

  ```shell
  kill -9 20045
  ```

- 杀掉包含指定内容的进程

  ```shell
  ps aux | grep "content" | awk '{print $2}' | xargs -I {} kill -9 {}
  ```
