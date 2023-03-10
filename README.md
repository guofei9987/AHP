# AHP
层次分析法

## How to use

Install

`pip install ahp`


use

```python
from AHP import AHP
import numpy as np

# 准则重要性矩阵
criteria = np.array([[1, 2, 7, 5, 5],
                     [1 / 2, 1, 4, 3, 3],
                     [1 / 7, 1 / 4, 1, 1 / 2, 1 / 3],
                     [1 / 5, 1 / 3, 2, 1, 1],
                     [1 / 5, 1 / 3, 3, 1, 1]])

# 对每个准则，方案优劣排序
b1 = np.array([[1, 1 / 3, 1 / 8], [3, 1, 1 / 3], [8, 3, 1]])
b2 = np.array([[1, 2, 5], [1 / 2, 1, 2], [1 / 5, 1 / 2, 1]])
b3 = np.array([[1, 1, 3], [1, 1, 3], [1 / 3, 1 / 3, 1]])
b4 = np.array([[1, 3, 4], [1 / 3, 1, 1], [1 / 4, 1, 1]])
b5 = np.array([[1, 4, 1 / 2], [1 / 4, 1, 1 / 4], [2, 4, 1]])

b = [b1, b2, b3, b4, b5]
a = AHP(criteria, b).run()
```

打印：
```text
==========准则层==========
最大特征值5.072084,CR=0.014533,检验通过
准则层权重 = [0.47583538 0.26360349 0.0538146  0.09806829 0.10867824]

==========方案层==========
          方案0       方案1       方案2     最大特征值            CR  一致性检验
准则0  0.081935  0.236341  0.681725  3.001542  8.564584e-04   True
准则1  0.595379  0.276350  0.128271  3.005535  3.075062e-03   True
准则2  0.428571  0.428571  0.142857  3.000000 -4.934325e-16   True
准则3  0.633708  0.191921  0.174371  3.009203  5.112618e-03   True
准则4  0.344545  0.108525  0.546931  3.053622  2.978976e-02   True

==========目标层==========
[[0.318586   0.23898522 0.44242878]]
最优选择是方案2
```