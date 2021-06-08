---
layout: page
title: 6.策略模式
group: group-snippet
order: 6
sidebar:
  - group-snippet
  - blogger
  - toc
date: 2021-06-08 21:58:59
---
python3策略模式
<!-- more -->

## 类方式实现策略模式(静态策略)
```python
class StrategyExecutor():

    def __init__(self, func=None):
        if func is not None:
            self.execute = func
    
    def execute(self, *args):
        print("Strategy not implemented")
    
    def strategy_addition(arg1, arg2):
        print(arg1 + arg2)
    
    def strategy_subtraction(arg1, arg2):
        print(arg1 - arg2)

def main():
    no_strategy = StrategyExecutor()
    addition strategy - Strategyexecutor (strategy_addition)
    subtraction_strategy = StrategyExecutor (strategy_subtraction) no_strategy.execute(4, 6)
    addition_strategy,execute(4, 6) subtraction_strategy.execute(4, 6)

if __name__ == "__main__":
    main()
```

## 函数嵌套方式实现策略模式(动态策略)
```python
def executor(arg1, arg2, func=None):

    if func is None:
      return "Strategy not implemented"

    return func(arg1, arg2)

def strategy_1(arg1, arg2):
    return f_1(arg1, arg2)

def strategy_2(arg1, arg2):
    return f_2(arg1, arg2)
```
