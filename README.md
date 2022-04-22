# SHIFT-STAC-demo
Repo for public use for science discovery using data from the Surface Biology and Geology (SBG) SHIFT AVIRIS-NG campaign. Examples are provided in mainly Python, with some R examples.

[More info about AVIRIS-NG data products](https://avirisng.jpl.nasa.gov/dataportal/)

Files include:

-`requirements.txt`: the complete list of required packages for Python venv creation

-`demo.ipynb`: tutorial Jupyter notebook

## Instructions

The demo files are available on s3://dh-shift-curated/demo

You can also download this repo by opening Terminal and making sure you are in the desired working directory, then running:

`git clone https://github.com/marinadunn/SHIFT-STAC-demo`

## Setup environment:

You can create a Python virtual environment on SHIFT-SMCE by running:

`python3 -m venv shift-env`

To activate the environment, run:

`source shift-env/bin/activate`

You can confirm this is active by running `$ which python`, which should `.../shift-env/bin/python`

Now you can install packages. A file with a list of dependencies needed to run these tutorials has been provided for convenience called `requirements.txt`. To install these, run:

`python3 -m pip install -r requirements.txt`

If you need to install any additional packages, you can use 

`python3 -m pip install <package>`

#### Your environment should now be properly setup.

-----------------------------------------------------------------------------------------------------------

## STAC Specifics
The SpatioTemporal Asset Catalog (STAC) specifies a standard language for structuring and querying geospatial data and metadata. The STAC specification is designed around the extensibility & flexibility of JSON, and is comprised of Catalogs, Collections, Items, and the API.

**STAC Catalog**: JSON object that contains list of STAC Items, or other child STAC Catalogs. Can be further extended to include additional metadata. No restictions for organization; typically uses ‘sub-catalog’ groupings. [More about STAC Catalog Specification](https://github.com/radiantearth/stac-spec/tree/master/catalog-spec)

**STAC Collection**: JSON object containing additional info describing the spatial and temporal extents of data; extension of Catalog. Can be further extended to include additional metadata. [More about STAC Collection Specification](https://github.com/radiantearth/stac-spec/blob/master/collection-spec/collection-spec.md)

**STAC Item**: GeoJSON feature with descriptive attributes that define its time range and assets; a collection of inseparable data & metadata. Represented in a flexible JSON format. Can indlude additonal fields & JSON structures for further customizing data searches. [More about STAC Item Specification](https://github.com/radiantearth/stac-spec/blob/master/item-spec/item-spec.md)

STAC Catalog hierarchy:
```
SBG-SHIFT STAC Catalog 
│
└─── AVIRIS-NG (Collection)
│   │
│   └─── <flight line> (Item)
```
where the STAC item is a dataset for one flight line of date form `YYYYMMDD` (see below). For each of these items, the dataset is an asset of form `angYYYYMMDDtHHNNSS.zarr`, as well as assets for jpegs of RGB True Color, RGB enhanced, and R, G, and B bands plotted separately. Note that the RGB composite images are not yet georeferenced, while bands plotted separately are.

```  
YYYY:  The year of the airborne flight run.
MM:    The month of the airborne flight run (i.e. 05 represents May).
DD:    The day of the airborne flight run (22 is the 22nd day of the month).
HH:    UTC hour at the start of acquisition
NN:    UTC minute at the start of acquisition
SS:    UTC second at the start of acquisition
```  
