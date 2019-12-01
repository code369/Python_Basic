Python一直强调PEP8优雅的代码，我觉得列表推导式就算优雅代码规范中的代表。列表推导式提供了从序列创建列表的简单途径。通常应用程序将一些操作应用于某个序列的每个元素，用其获得的结果作为生成新列表的元素，或者根据确定的判定条件创建子序列。每个列表推导式都在 for 之后跟一个表达式，然后有零到多个 for 或 if 子句。返回结果是一个根据表达从其后的 for 和 if 上下文环境中生成出来的列表。**如果希望表达式推导出一个元组，就必须使用括号。**

### 1.简单运用
 先定义一个简单列表
list1 = [2,4,6,3]

#####  (1)一维度
```python
# 这里我们将列表中每个数值乘三，获得一个新的列表：
list1 = [2,4,6,3]
list2 = [x*3 for x in list1]
print(list2)

运行结果：
[6, 12, 18, 9]
```
##### (2)二维
```python
list1 = [2,4,6,3]
list3 = [[x,x**2] for x in list1[0:3]]
print(list3)

运行结果：
[[2, 4], [4, 16], [6, 36]]
```
##### (3)和if结合
```python
list1 = [2,4,6,3]
list4 = [x*3 for x in list1 if x < 5]
print(list4)

运行结果：
[6, 12, 9]
```

### 2.双循环或多循环

```python
temp1= [1,2,3]
temp2 =[4,5,6]

temp3 = [x+y for x in temp1 for y in temp2]
print(temp3)

运行结果：
[5, 6, 7, 6, 7, 8, 7, 8, 9]

# 注意此时的temp3会有9个元素，因为第一个列表的元素需要分别和第二个列表每个元素相加
```

###  3.嵌套
 嵌套的方式在开发中用的比较多
##### (1) 简单嵌套

```python
# 用推导式控制小数点的位数
nest01 = [str(round(11/7,i))for i in range(1,6)]
print(nest01)

运行结果：
['1.6', '1.57', '1.571', '1.5714', '1.57143']
```

##### (2) 实现矩阵列表的转置运算

```python
# 定义一个3X4的矩阵列表：
nest02 = [[1,1,1,1],[2,2,2,2],[3,3,3,3]]

# 方式一：直接列表推导式
nest03 = [[row[i]for row in nest02]for i in range(4)]
print(nest03)

运行结果：
[[1, 2, 3], [1, 2, 3], [1, 2, 3], [1, 2, 3]]


# 方式二：空列表+遍历+append
nest04 = []
for i in range (4):
	nest04.append([row[i] for row in nest02])
print(nest04)

运行结果：
[[1, 2, 3], [1, 2, 3], [1, 2, 3], [1, 2, 3]]


# 方式三：空列表+双遍历+append
transposted = []
for i in range(4):
	transposted_row = []
	for row in nest02:
		transposted_row.append(row[i])
	transposted.append(transposted_row)
print(transposted)

运行结果：
[[1, 2, 3], [1, 2, 3], [1, 2, 3], [1, 2, 3]]

```


### 如果觉得博文有帮助欢迎点赞或留言，关于Python列表的其他使用，可参考博主博文《[Python基础入门_06列表](https://blog.csdn.net/ZZQHELLO2018/article/details/80866059)》

