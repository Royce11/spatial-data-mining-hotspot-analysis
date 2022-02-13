# Geospatial Hotspot Analysis

## About

Geospatial Hotspot Analysis is about two different hot spot analysis tasks:

### Hot zone analysis
In this analysis, a range join operation is performed on a rectangle datasets and a point dataset. For each rectangle, the number of points located within the rectangle will be obtained. The rectangle that includes more points is known as a hot rectangle. So the outcome of this analysis is to determine the hotness of all the rectangles.

### Hot cell analysis
In this analysis, the concepts of Spatial Statistics is applied on spatio-temporal big data in order to identify statistically significant spatial hotspots.The topic of this task is from ACM SIGSPATIAL GISCUP 2016.
The Problem Definition page is here: http://sigspatial2016.sigspatial.org/giscup2016/problem
The Submit Format page is here: http://sigspatial2016.sigspatial.org/giscup2016/submit

## Input Output Specification

### Input parameters

1. Output path (Mandatory)
2. Task name: "hotzoneanalysis" or "hotcellanalysis"
3. Task parameters: (1) Hot zone (2 parameters): nyc taxi data path, zone path(2) Hot cell (1 parameter): nyc taxi data path

spark-submit parameters example:
```
test/output hotzoneanalysis src/resources/point-hotzone.csv src/resources/zone-hotzone.csv hotcellanalysis src/resources/yellow_trip_sample_100000.csv
```

Note: 

1. The number/order of tasks do not matter.
2. But, the first 7 of our final test cases will be hot zone analysis, the last 8 will be hot cell analysis.

### Input data format
The main function/entrace is "cse512.Entrance" scala file.

1. Point data: the input point dataset is the pickup point of New York Taxi trip datasets. The data format of this phase is the original format of NYC taxi trip which is different from the previous phase. But the coding template already parsed it for you. Find the data from our asu google drive shared folder: [https://drive.google.com/drive/folders/1W4GLKNsGlgXp7fHtDlhHEBdLVw_IuAXh?usp=sharing](https://drive.google.com/drive/folders/1W4GLKNsGlgXp7fHtDlhHEBdLVw_IuAXh?usp=sharing)

2. Zone data (only for hot zone analysis): at "src/resources/zone-hotzone" of the template

#### Hot zone analysis
The input point data can be any small subset of NYC taxi dataset.

#### Hot cell analysis
The input point data is a monthly NYC taxi trip dataset (2009-2012) like "yellow\_tripdata\_2009-01\_point.csv"

### Output data format

#### Hot zone analysis
All zones with their count, sorted by "rectangle" string in an ascending order. 

```
"-73.795658,40.743334,-73.753772,40.779114",1
"-73.797297,40.738291,-73.775740,40.770411",1
"-73.832707,40.620010,-73.746541,40.665414",20
```


#### Hot cell analysis
The coordinates of top 50 hotest cells sorted by their G score in a descending order.

```
-7399,4075,15
-7399,4075,29
-7399,4075,22
```