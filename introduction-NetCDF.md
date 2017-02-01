## NetCDF

Network Common Data Form

```
NetCDF is a set of software libraries and self-describing, machine-independent data formats that support the creation, access, and sharing of array-oriented scientific data.
```

## The scope of NetCDF is large

Very diverse range of data sources, organized with this file format. 

* Terrestrial and marine remote sensing
* Non-spatial multi-dimensional, structured data
* Model output - physical ocean models, ecosystem models
* Multiple variables - a few, or hundreds in one file
* Time series across files
* ...


![][Unidata]


[Unidata]: unidata.png "Unidata NetCDF"



## Key components in NetCDF

* **Variables** this is the bulk data, stored in *arrays* or *matrices*
* **Dimensions** these define the *shape* and *size* of the **variable**
* **Attributes** these store *metadata* that give *meaning* to the **variables** and their **dimensions**


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

* start with the shell `ncdump -h filename.nc`


### R example:

```R
library(ncdf4)
target_file <- "/path/to/file"
connection_to_nc <- nc_open(target_file)
  extracted_data <- ncvar_get(connection_to_nc, "variable_name")
  extracted_first_dimension <- ncvar_get(connection_to_nc, "first_dimenison_name") 
  extracted_second_dimension <- ncvar_get(connection_to_nc, "second_dimenison_name") 
  extracted_third_dimension <- ncvar_get(connection_to_nc, "third_dimenison_name") 
nc_close(connection_to_nc)
mean_of_each_layer <- apply(extracted_data,3,mean,na.rm=TRUE)
image(x=extracted_first_dimension, y=extracted_second_dimension, z=extracted_data[,,1])
```

### Python example

```python
from netCDF4 import Dataset

# Read dataset
data = Dataset(data_file)

print("The file contains the following variables:')
print(data.variables.keys())

data_variable = data.variables['name'][:, :, :]
history_metadata = data.history

```

### Matlab examples


```matlab
ncload myfile.nc
who
```


### Shell examples?


```bash
ncdump -h myfile.nc
```


## Specific tools

* ncdump -h
* nco, cdo, ...
* Python and the libs, Dr. Climate on the Python stack: https://drclimate.wordpress.com/2016/10/04/the-weatherclimate-python-stack/
* R and ncdf4, raster
* GDAL
* Matlab



### Don't read this out, open Panoply and describe it directly: 

Get a file. 

```R
u <- "ftp://eclipse.ncdc.noaa.gov/pub/OI-daily-v2/NetCDF/2017/AVHRR/avhrr-only-v2.20170116.nc.gz"
download.file(u, basename(u), mode = "wb")
system(sprintf("gunzip --keep %s", basename(u)))
```

A specific example could be a map of sea surface temperature, for the entire globe at 1-degree resolution. 

* the variable is the 360x180x1 temperature values in a matrix/array
* the dimensions are "longitude" (with length 360) and "latitude" (with length 180) and a single time step (we know when we measured the values)
* the attributes store the extra details we need to find the values for each step in the dimensions, the units of the temperature measurement, the units of the dimension values, and **global** metadata about who measured it and how. 
```


