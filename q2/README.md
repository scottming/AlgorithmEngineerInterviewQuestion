# 加法模型说明文档

## 数据的生成过程

主要采用 `numpy.random.randint` 随机生成，最后是采用的 50 万数据，然后用 sklearn 把数据切成训练集和测试集两份。

## 模型是如何设计的

最开始看到这个题目时，想的是用 CNN 来实现，但哪怕是 `+` 号左右两边是三位数，也需要分 1999 个类别，这会大大增加模型的复杂度，同时泛化能力很有限。

因为两边输入的都是字符串，但两边代表的意思是一样的，所以本质上我觉得是个翻译问题，而目前解决翻译问题的最适用的模型无疑是 seq2seq。

## 超参数是如何选择的

请查看代码里面的 [ChangeLog](q2.ipynb).

## 目标函数和优化方法如何选择

优化方法用的是 Adamoptimizer，相比 GradientDescentOptimizer cost 下降要快一些。

## 模型在测试集上的准确率是多少

* Cell: BasicRNNCell
* dataset size: 500000
* Epochs: 20001
* Learning_rate: 0.003
* Train/Test Acc: 0.941/0.940
* Final cost: 0.0394