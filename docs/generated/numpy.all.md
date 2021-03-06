# numpy.all

## 调用概览

```python
numpy.all(a, axis=None, out=None, keepdims=<no value>)
```

## 方法说明

测试沿给定轴的所有数组元素是否为真。

- **参数**: 
    - **a : 类数组类型**
        输入数组或可转换为数组的对象。
    - **axis : None或int或tuple of ints，可选**
        沿一个或多个轴执行逻辑AND规约。 默认值（axis = None）是对输入数组的所有维度执行逻辑AND。轴可以是负数，这种情况下，它从最后一个轴开始索引。
        *版本1.7.0中的新功能。*
        如果这是一个整数元组，则在多个轴上进行规约操作，而不是像以前那样在单个轴或所有轴上进行行规约操作。
    - **out : ndarray, 可选**
        用于存放输出结果的备用输出数组。它必须具有与预期输出相同的形状，并保留其类型。
    - **keepdims : bool, 可选**
        如果将其设置为True，则缩小的轴将作为尺寸为1的尺寸保留在结果中。 使用此选项，结果将针对输入数组正确广播。
        如果传递了默认值，则keepdims将不会传递给[ndarray](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.html#numpy.ndarray)的所有子类方法，但是任何非默认值都将是。 如果子类的方法没有实现keepdims，则会引发任何异常。
- **返回**:
    - **all : ndarray, bool**
        除非指定out，否则返回一个新的布尔值或数组，在这种情况下返回对out的引用。

## 另见

- [ndarray.all](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.all.html#numpy.ndarray.all) 等效方法
- [any](https://docs.scipy.org/doc/numpy/reference/generated/numpy.any.html#numpy.any) 测试沿给定轴的任何元素是否为True。

## 注意

非数字（Not a Number，NaN）、正无穷和负无穷被视为真，因为它们不等于零。

## 例子

```python
>>> np.all([[True,False],[True,True]])
False
```

```python
>>> np.all([[True,False],[True,True]], axis=0)
array([ True, False])
```

```python
>>> np.all([-1, 4, 5])
True
```

```python
>>> np.all([1.0, np.nan])
True
```

```python
>>> o=np.array([False])
>>> z=np.all([-1, 4, 5], out=o)
>>> id(z), id(o), z                             
(28293632, 28293632, array([ True]))
```