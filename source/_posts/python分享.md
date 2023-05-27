---
title: python分享
description: 一些有趣的Python代码
comments: false
abbrlink: ee4374b7
date: 2023-05-14 15:30:16
tags:
---

猜数字小游戏

``` Python
from random import randint

def guess(maxValue = 100,maxTimes = 5):
    value = randint(1, maxValue)
    for i in range(maxTimes):
        prompt = 'Start to GUESS:' if i == 0 else 'Guess again:'
        try:
            x = int(input(prompt))
            assert 1<x<100
        except:
            print('Must input an integer between 1 and ', maxValue)
        else:
            if x == value:
                print('Congratulations!')
                break
            elif x > value:
                print('Too big')
            else:
                print('Too little')
    else:
        print('Game over. FAIL.')
        print('The value is ', value)
guess(maxValue=100,maxTimes=5)
```

自除数判断

描述

编写一个 Python 函数程序，获取用户输入检查是否是自除数。

自除数自除数 是指可以被它包含的每一位数除尽的数。

例如，128 是一个自除数，因为 128 % 1 == 0，128 % 2 == 0，128 % 8 == 0。

还有，自除数不允许包含 0 

``` Python
def checkN(N):
    n = int(N)
    o = 10
    count = 0
    while True:
        # TODO: write code...
        if(n % o): 
            count = count + 1
            o = o*10
            if (n % o == n):
                count = count + 1
                break
    return count

def zichuN(count):
    u = 10
    y = 1
    alist = []
    for i in range(count):
        alist.append(int(M / y) % u)
        y = y*10
    return alist
    
def zichuM(alist):
    turecount = 0
    falsecount = 0
    for i in range(len(alist)):
        if M % alist[i] == 0:
            turecount = turecount + 1
        else:
            falsecount = falsecount + 1
    if(turecount):
        if(falsecount):
            return False
        else:
            return True
M = int(input())
print(zichuM(zichuN(checkN(M))))
```