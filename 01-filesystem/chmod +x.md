`chmod +x` 的作用是：

> 给文件增加“可执行（execute）”权限。

例如：

```bash
chmod +x start.sh
```

执行后：

```bash
./start.sh
```

就可以直接运行脚本了。

---

### `+x` 是什么意思

权限分为：

- `r`：读（read）
- `w`：写（write）
- `x`：执行（execute）

例如：

```bash
-rw-r--r--
```

表示：

- 文件所有者：可读可写
- 同组用户：只读
- 其他用户：只读

执行：

```bash
chmod +x test.sh
```

后可能变成：

```bash
-rwxr-xr-x
```

增加了执行权限。

---

### 可以接多个文件吗？

可以。

```bash
chmod +x file1.sh file2.sh file3.sh
```

一次给多个文件增加执行权限。

---

### 可以接目录吗？

也可以。

```bash
chmod +x mydir
```

对于目录来说：

- `r`：可以查看目录内容（`ls`）
- `w`：可以创建、删除文件
- `x`：可以进入目录（`cd`）

例如：

```bash
chmod +x mydir
```

允许进入目录：

```bash
cd mydir
```

但如果没有 `r` 权限：

```bash
ls mydir
```

可能会报权限不足。

---

### 递归处理整个目录

给目录下所有文件和子目录增加执行权限：

```bash
chmod -R +x scripts/
```

不过通常不建议这样做，因为：

```text
普通文件 ≠ 可执行文件
```

例如：

```text
README.md
data.json
image.png
```

被加上 `x` 权限也没意义。

更常见的是：

```bash
find scripts -type f -name "*.sh" -exec chmod +x {} \;
```

只给 `.sh` 脚本增加执行权限。

---

### 查看权限

```bash
ls -l
```

例如：

```bash
-rwxr-xr-x 1 user staff 1234 Jun 3 start.sh
```

其中：

```text
rwx  所有者
r-x  用户组
r-x  其他用户
```

表示该文件可执行。

---

另外，`chmod +x` 是一种**符号模式（symbolic mode）**写法，对应的数字模式写法常见有：

```bash
chmod 755 start.sh
```

等价于：

```bash
rwxr-xr-x
```

这是 Linux/macOS 项目里最常见的可执行脚本权限设置。


给多个脚本添加权限：
```bash
chmod +x *.sh
```

