---
title: 编写命令行工具
tags: argparse
categories: python
date: 2020-08-08 18:45:24
---
python使用argparse编写命令行工具
<!-- more -->
```python
def main():
    # 初始化命令行 自带 --help 参数 缩写为-h
    parser = argparse.ArgumentParser()

    # 必填参数positional arguments 位置参数
    parser.add_argument('param1', help='注释内容', type=int)  # 默认str类型，可变为type=int
    parser.add_argument('param2', help='注释内容', type=str)  # 默认str类型，可变为type=int

    # 可选参数           缩写    全拼
    parser.add_argument("-P", "--path", help="注释", type=str)

    # 获取命令行参数 parser.parse_args() 并赋值给args
    args = parser.parse_args()

    # 执行逻辑(根据参数执行对应逻辑)
    print(args)


if __name__ == "__main__":
    main()
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
