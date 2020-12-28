# temp

### git提交pdf文件问题

> 错误信息：
>
> the remote end hung up unexpectedly Everything up-to-date

原因是curl的postBuffer 默认值较小的原因，文件过大导致的上传失败了。

### 解决方法：

默认 Git 设置 http post 的缓存为 1MB，使用命令将git的缓存设为500M，重新配置一下postBuffer值

**方法1**：命令行输入

```
$ git config --global http.postBuffer 524288000
```

**方法2**：直接在配置文件中添加参数即可

**windows:**

在 **.git/config** 文件中加入

```
[http]
postBuffer = 524288000
```

**linux:**

```
$ git config http.postBuffer 524288000
```