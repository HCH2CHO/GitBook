# Arcpy

介绍一些arcpy脚本。

arcpy入门知识可参见

Desktop：[http://desktop.arcgis.com/zh-cn/arcmap/10.3/analyze/arcpy/what-is-arcpy-.htm](http://desktop.arcgis.com/zh-cn/arcmap/10.3/analyze/arcpy/what-is-arcpy-.htm)

Pro：[https://pro.arcgis.com/zh-cn/pro-app/arcpy/get-started/what-is-arcpy-.htm](https://pro.arcgis.com/zh-cn/pro-app/arcpy/get-started/what-is-arcpy-.htm)

## 创建空的shp文件

```python
arcpy.CreateFeatureclass_management(r"C:\Users\HCHO\Documents\ArcGIS\ZXKJ","point.shp", "POINT")
geometry_type可选POINT,MULTIPOINT,POLYGON,POLYLINE
```

## 沿线创建点

参考链接 [https://gis.stackovernet.com/cn/q/33181](https://gis.stackovernet.com/cn/q/33181)

```python
import arcpy
points = []
for row in arcpy.da.SearchCursor(r'C:\Users\HCHO\Documents\ArcGIS\ZXKJ\car_line.shp', ["OBJECTID","SHAPE@"]): # change this to your source line layer
       length = int(row[1].length)
       for i in xrange(0, length + 10, 10): # assuming units are in meters for feature spatial reference
           point = row[1].positionAlongLine(i)
           point.ID=row[0]
           points.append(point)    
arcpy.CopyFeatures_management(points, r'C:\Users\HCHO\Documents\ArcGIS\ZXKJ\points.shp') # change this to wherever you want this layer stored
```

沿要素创建点，并添加其他字段

```python
import arcpy
fields = ['id', 'SHAPE@XY']
shppath = r'C:/Users/HCHO/Documents/ArcGIS/ZXKJ/point.shp'
cursor = arcpy.da.InsertCursor(shppath,fields)
for row in arcpy.da.SearchCursor('C:/Users/HCHO/Documents/ArcGIS/ZXKJ/car_line.shp', ["OBJECTID","SHAPE@"]):
        length = int(row[1].length)
        for i in xrange(0, length + 1, 1): 
            point = row[1].positionAlongLine(i)
            cursor.insertRow((row[0],point))
```

## shp文件添加字段、赋值

参考链接[https://blog.csdn.net/imxiezy/article/details/88698846](https://blog.csdn.net/imxiezy/article/details/88698846)

```text
#加入字段
arcpy.AddField_management(filepath,"landId","TEXT",field_length=12)

#给字段赋值
cursor = arcpy.UpdateCursor(path)
for row in cursor:
    row.setValue("landId",value)
```

