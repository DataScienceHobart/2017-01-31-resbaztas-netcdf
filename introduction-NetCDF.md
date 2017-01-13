## NetCDF general concepts

* **Variables** this is the bulk data, stored in *arrays*
* **Dimensions** these define the *shape* and *size* of the **variable**
* **Attributes** these store *metadata* that give *meaning* to the **variables** and their **dimensions**

### Don't read this out, open Panoply and describe it directly: 

```
A specific example could be a map of sea surface temperature, for the entire globe at 1-degree resolution. 

* the variable is the 360x180x1 temperature values in a matrix/array
* the dimensions are "longitude" (with length 360) and "latitude" (with length 180) and a single time step (we know when we measured the values)
* the attributes store the extra details we need to find the values for each step in the dimensions, the units of the temperature measurement, the units of the dimension values, and **global** metadata about who measured it and how. 
```

Technical advanced features, see Unidata blog for tips and tricks

NetCDF automatically deals with

* different data types
* memory handling, scaling up to large 
* compact transmission (compression)
* performance f
* cross-platform, cross-language
* Compression
* Tiling (called chunking)
* Full metadata
* Scaleability
* Web serving/ Partial access


## Programming languages

* start with ncdump
* then show bare minimum with Python, R, Matlab and show that they all utilize the engine behind ncdump to do stuff




## Scope and generality of what NetCDF can deal with is HUUUUGE

It's all defined by the **CF Conventions** [link] etc. 

This covers a big range of kinds of files and kinds of data. 

* Terrestrial and marine remote sensing
* non-spatial multi-dimensional, structured data
* Model output
* Multiple variables
* Regular grids, curvilinear grids
* Time series across files

## Specific tools

* ncdump -h
* nco, cdo, ...
* Python and the libs, Dr. Climate on the Python stack: https://drclimate.wordpress.com/2016/10/04/the-weatherclimate-python-stack/
* R and ncdf4, raster
* GDAL
* Matlab

