---
title: python学习之call脚本
tags:
  - python
categories:
  - python学习
  - python小妙招
date: 2025-03-26 22:36:39
---

# 前言

最近在用python写一些工具tool，有时候想偷个懒，直接调用现在有的脚本，而不是自己重写，由于环境是windows，基本上调用的就 `.bat`文件，因此在这里记录一下，防丢~

# python 实例

```python
import subprocess

def run_bat_with_window(bat_path, *args):
    """
    直接弹出CMD窗口执行.bat脚本
    :param bat_path: .bat文件路径
    :param args: 可变参数，支持任意数量
    """
    try:
        # 构造命令列表（自动处理路径空格和参数转义）
        cmd = [bat_path]
        cmd.extend(str(arg) for arg in args)

        # 启动独立CMD窗口执行（仅Windows有效）
        subprocess.run(
            cmd,
            creationflags=subprocess.CREATE_NEW_CONSOLE,
            check=True
        )

    except subprocess.CalledProcessError as e:
        print(f"错误：脚本执行失败 (状态码 {e.returncode})")
    except FileNotFoundError:
        print(f"错误：找不到文件 '{bat_path}'")
    except Exception as e:
        print(f"未知错误：{str(e)}")


# 使用示例
if __name__ == "__main__":
    bat_file = r"F:\python_study\callbatDemo\example.bat"  # 包含空格的路径测试
    run_bat_with_window(bat_file, 2, 1, "hello world", "special&char!")
```



# bat脚本实例

```bash
@echo off
chcp 65001 > nul
title 参数过滤监控窗口
color 0A

echo [系统日志] 参数过滤器启动 > con
echo -----------------------------------
setlocal enabledelayedexpansion

set counter=0

:loop
set /a counter+=1
if "%~1"=="" goto done

if "%~1"=="1" (
    echo [成功] 参数!counter!: %~1
) else (
    echo [忽略] 参数!counter!: %~1
)

shift
goto loop

:done
echo -----------------------------------
echo 总计处理参数数: %counter%
pause
```

# 运行结果

运行后会叫起来一个cmd窗口，然后显示对应参数结果

![image-20250326231159267](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250326231159267.png)



# 小结

这里主要是使用了Python中的subprocess模块，该模块核心函数如下：

|         方法         |                        特点                        |           适用场景           |
| :------------------: | :------------------------------------------------: | :--------------------------: |
|  `subprocess.run()`  | 高级封装，自动等待完成，返回`CompletedProcess`对象 | 简单命令执行，需获取完整结果 |
| `subprocess.Popen()` |   底层接口，提供进程交互能力（输入/输出流控制）    |    需要实时交互或后台运行    |
| `subprocess.call()`  |  旧版方法，返回退出码（等同于`run().returncode`）  |          兼容旧代码          |

windows 批处理脚本中，是允许携带参数进入脚本的，其获取方式就是如下：

```
 `%0`：脚本自身名称（如 `my_script.bat`）
 `%1` ~ `%9`：第1到第9个传入参数
 `%*`：所有参数（`%1`及之后的所有内容）
```

其中：

```
保留引号：%1（直接获取原始值，包含引号）
去除引号：%~1（自动去除参数外层引号）
```

拓展：

| 修饰符 |         作用         | 示例（参数为 `"D:\Docs\file.txt"`） |
| :----: | :------------------: | :---------------------------------: |
| `%~f1` |       完整路径       |         `D:\Docs\file.txt`          |
| `%~d1` |       驱动器号       |                `D:`                 |
| `%~p1` |  路径（不含文件名）  |              `\Docs\`               |
| `%~n1` | 文件名（不含扩展名） |               `file`                |
| `%~x1` |        扩展名        |               `.txt`                |
| `%~s1` |  短路径（8.3格式）   |        `D:\DOCS~1\file.txt`         |
| `%~a1` |       文件属性       |             `--a------`             |
| `%~t1` |     最后修改时间     |         `2023-08-01 14:30`          |
| `%~z1` |   文件大小（字节）   |               `1024`                |
