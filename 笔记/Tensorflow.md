models/samples/core/get_started/premade_estimator.py

`tf.keras.utils.get_file()` 该函数会将远程 CSV 文件复制到本地文件系统。

Pandas DataFrame 是一个包含已命名列标头和已编号行的表格。

调用 `tf.feature_column`模块中的函数来构建 `feature_column` 对象列表

一个预创建的 Estimator（名为`tf.estimator.DNNClassifier`）

```
 classifier = tf.estimator.DNNClassifier(
        feature_columns=my_feature_columns,
        hidden_units=[10, 10],
        n_classes=3)
```

`tf.Estimator.DNNClassifier` 的构造函数采用名为 `optimizer` 的可选参数，但我们的示例代码选择不指定该参数(优化器、学习速率)

调用 Estimator 对象的 `train` 方法。`args.train_steps` 的默认值是 1000。

```
 classifier.train(
        input_fn=lambda:train_input_fn(train_feature, train_label, args.batch_size),
        steps=args.train_steps)
```

将输入特征和标签转换为 `tf.data.Dataset` 对象

```
 dataset = tf.data.Dataset.from_tensor_slices((dict(features), labels))
```

`tf.dataset` 类提供很多用于准备训练样本的实用函数。以下行调用了三个此类函数，样本随机化处理（batch_size>样本数）：

```
    dataset = dataset.shuffle(buffer_size=1000).repeat(count=None).batch(batch_size)
```

```
return dataset.make_one_shot_iterator().get_next()  返回一批样本
```

评估模型，从测试集中取数据

```
eval_result = classifier.evaluate(
    input_fn=lambda:eval_input_fn(test_x, test_y, args.batch_size))
```
