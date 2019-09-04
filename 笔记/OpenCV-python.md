绘制矩形

```python
draw_img=cv2.rectangle(draw_img, (x1,y1),(x2,y2), color,thick)
plt.imshow(draw_img)
```

 

模板匹配

```python
result=cv2.matchTemplate(imcopy, temp,method=cv2.TM_CCOEFF_NORMED)
(minVal, maxVal, minLoc, maxLoc)=cv2.minMaxLoc(result)

fig = plt.figure(figsize=(12,3))
plt.subplot(131)
plt.bar(bincen, rh[0])
plt.xlim(0, 256)
plt.title('R Histogram')
```

 

色彩直方图

```python
rhist = np.histogram(img[:,:,0],bins=nbins,range=bins_range)
#转换色彩空间
img_small_RGB = cv2.cvtColor(img_small, cv2.COLOR_BGR2RGB) 
img_small_HSV = cv2.cvtColor(img_small, cv2.COLOR_BGR2HSV)
```

色彩空间：RGB、LUV、HSV/HSL

*Hue, Saturation, Value/Lightness*

 

```python
#resize() 调整尺寸
#ravel()  降维
features = cv2.resize(feature_image, size).ravel() 
```

 

经研究发现，采用无向的梯度和9个直方图通道，能在行人检测试验中取得最佳的效果。

 

hog函数

[https://scikit-image.org/docs/dev/api/skimage.feature.html?highlight=feature%20hog#skimage.feature.hog](https://scikit-image.org/docs/dev/api/skimage.feature.html?highlight=feature hog#skimage.feature.hog)

每一个cell计算梯度，以block为单位表示特征。

```python
skimage.feature.hog(image, orientations=9, pixels_per_cell=(8, 8), cells_per_block=(3, 3), block_norm='L2-Hys', visualize=False, transform_sqrt=False, feature_vector=True, multichannel=None)
```

 

```python
np.vstack()  #按垂直向堆叠
np.hstack()  #按水平向堆叠
#数据标准化
X_scaler = StandardScaler().fit(X)
scaled_X = X_scaler.transform(X)
```

 

SVM

```python
parameters = {'kernel':('linear', 'rbf'), 'C':[1, 10]}
svr = svm.SVC()
clf = grid_search.GridSearchCV(svr, parameters)
#RandomizedSearchCV
clf.fit(iris.data, iris.target)
clf.best_params_
```

 

数据分组。random_state为随机数种子，种子不同，产生不同的随机数；种子相同，即使实例不同也产生相同的随机数。填0或不填，每次都会不一样。

```python
X_train, X_test, y_train, y_test = train_test_split(
    scaled_X, y, test_size=0.2, random_state=rand_state)
```
