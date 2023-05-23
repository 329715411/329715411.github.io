---
title: python分享
excerpt: 1
comments: false
abbrlink: ee4374b7
date: 2023-05-14 15:30:16
tags:
---

猜数字小游戏

```javascript
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
