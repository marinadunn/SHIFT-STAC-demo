# SHIFT-STAC-demo
Repo for public use for science discovery using data from the Surface Biology and Geology (SBG) SHIFT AVIRIS-NG campaign. Examples are provided in Python.

[More info about AVIRIS-NG data products](https://avirisng.jpl.nasa.gov/dataportal/)

Files include:

-`requirements.txt`: the complete list of required packages for Python venv creation

-`data_visualization_demo.ipynb`: demo Jupyter notebook of visualization and analysis for example dataset

## Instructions

If running this demo on the SHIFT-SMCE, files are already available in the AWS S3 bucket `dh-shift-curated` under `/demo/`, and the required packages have already been installed in the environment.

If you prefer to work on the demo locally, you can also download this repo by running:

`git clone https://github.com/marinadunn/SHIFT-STAC-demo`

You can then create a Python virtual environment by running:

`python3 -m venv shift-env`

To activate the environment, run:

`source shift-env/bin/activate`

You can confirm this is active by running `$ which python`, which should `.../shift-env/bin/python`

A file with a list of dependencies needed to run the demo has been provided called `requirements.txt`. To install these, run:

`python3 -m pip install -r requirements.txt`

If you need to install any additional packages, you can use 

`python3 -m pip install <package>`

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
where each STAC item is a flight line of format `angYYYYMMDDtHHNNSS`, and its asset is the Zarr dataset of format `angYYYYMMDDtHHNNSS.zarr`.

```  
YYYY:  The year of the airborne flight run.
MM:    The month of the airborne flight run (i.e. 05 represents May).
DD:    The day of the airborne flight run (22 is the 22nd day of the month).
HH:    UTC hour at the start of acquisition
NN:    UTC minute at the start of acquisition
SS:    UTC second at the start of acquisition
```  
