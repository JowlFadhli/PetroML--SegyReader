# SegyReader
Using paid software such as Petrel to view and analyze segy data might be a pain in the neck. With SegySak library, users would be able to have a quick glance of the seismic data and conducted analysis on the file easily.

# Segysak library?
Extracted from https://segysak.readthedocs.io/en/latest/why-segysak.html.

Segysak is a library for loading and manipulating seg-y data with python. Improved using segyio and xarray, Segysak helps to improve accessibility of seismic data for geoscientists using Python. Currently SEGY-SAK can load 2D, 2D gathers, 3D and 3D gathers into a common format stable format called seisnc that you can use faithfully in your downstream applications.egysak package has enhancements to xarray that reduce complexity for common seismic related tasks to extracting information from seismic such as arbitrary line, well-deviation or horizon extraction.

## What is the difference between xarray and regular array?
Read more at https://github.com/pydata/xarray.git and https://bit.ly/3v91MU4. 
Xarray is a python package that helps to handle labeled multi-dimensional (N-dimensional/ND) arrays which heavily inspired by Pandas. The things when handling seg-y file is when dealing with null or NAn value. Apart from that, seg-y data often comes in multi-dimensional (2d/3d). 

Difference between numpy array and xarray includes
1. Xarray used named dimensions instead of axis labels used by numpy as data selection would be easier and operations can be applied over various dimensions.
2. Xarray can handle heterogenous data in an ND array which helps easier NaN value handling whereas Numpy only have one data type

# Getting started (2D SEG-Y data)

### 1. Importing necessary library
Necessary library to conduct this analysis includes matplotlib, pathlib and numpy. 

```
import matplotlib.pyplot as plt 
import pathlib
import numpy as np

```
### 2. Reading seg-y data

For data reading, simply pass the file location by replacing the "filepath" with appropriate path. 
 ```
 path = pathlib.Path("filepath")
 ```
 
 ### 3. Importing necessary package from segy-sak library
 
 i. To observe the properties and metadata of the file by observing the header , simply use:
 
```
from segysak.segy import get_segy_texthead
head=get_segy_texthead(path)
```
Running the code will give gives the details of the header. From the header, we can obtain necessary information about the seg-y data and the metadata can be extracted for further data management. 

<img width="287" alt="image" src="https://user-images.githubusercontent.com/93107581/162869424-32757585-d673-4cd5-ac8b-ba11b43583a7.png">

ii. Next step involves deeper trace header data investigation and the code below can be use to give basic statistics of each byte position in a pandas.dataframe format. 

```
from segysak.segy import segy_header_scan

scan2D = segy_header_scan(path)
scan2D

```


