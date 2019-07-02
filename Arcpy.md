介绍一些arcpy脚本。

arcpy入门知识可参见 <http://desktop.arcgis.com/zh-cn/arcmap/10.3/analyze/arcpy/what-is-arcpy-.htm>



### 沿线创建点

参考链接	<https://gis.stackovernet.com/cn/q/33181>

```python
points = []
for row in arcpy.da.SearchCursor('C:/Temp/line.shp', ["SHAPE@"]): # change this to your source line layer
       length = int(row[0].length)
       for i in xrange(0, length + 10, 10): # assuming units are in meters for feature spatial reference
           point = row[0].positionAlongLine(i)
           points.append(point)    
arcpy.CopyFeatures_management(points, 'C:/Temp/points.shp') # change this to wherever you want this layer stored
```

