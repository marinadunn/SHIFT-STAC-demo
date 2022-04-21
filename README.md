# SHIFT-STAC-demo
Repo for public use for science discovery using data from the Surface Biology and Geology (SBG) SHIFT AVIRIS-NG campaign. Examples are provided in mainly Python, with some R examples.

[More info about AVIRIS-NG data products](https://avirisng.jpl.nasa.gov/dataportal/)

Files include:

-`requirements.txt`: the complete list of required packages for Python venv creation

-`environment.yml`: setup file for conda env creation containing the complete list of required packages

-`demo.ipynb`: tutorial Jupyter notebook

-`catalog.json`: copy JSON of the SBG-SHIFT STAC Catalog

## Download Repo

To download the repo, open Terminal and make sure you are in the desired working directory, then run:

`git clone https://github.com/marinadunn/SHIFT-STAC-demo`

## Setup environment:

#### Conda: 
To setup using conda, you can create a virtual conda environment from a file with a list of dependencies needed to run these tutorials. One has already been provided for convenience called `environment.yml` with the environment name 'shift-env’ and specified both conda + pip requirements. You can change this to your liking if desired. 

To create a conda environment from this file locally, in your Terminal run:

`$ conda env create --file environment.yml`

To activate the environment, run:

`$ conda activate shift-env`

If you need to update the environment (i.e. if a new version of a dependency is released), simply update the contents of your `environment.yml` file, then run:

`$ conda env update --prefix ./env --file environment.yml  --prune`

To use this environment as a kernel inside Jupyter, you can also manually add it by running:

`$ python -m ipykernel install --user --name <env_name> --display-name "Python (<env_name>)"`

For more info on using with Jupyter, [see here](https://medium.com/@sachinjose31/install-tensorflow-gpu-and-use-it-using-kernel-in-jupyter-6d82c8c5e468).
More info about managing conda environments can be found at https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

#### Python virtual environment: 
If conda is not available or you prefer to use 'pip', you can create a virtual environment using Python. Make sure Python 3 is first installed.

To create an environment, in the Terminal run:

`$ python3 -m venv shift-env`

To activate the environment, run:

`$ source shift-env/bin/activate`

You can confirm this is active by running `$ which python`, which should `.../shift-env/bin/python`

Now you can install packages. A file with a list of dependencies needed to run these tutorials has been provided for convenience called `requirements.txt`. To install these, run:

`$ python3 -m pip install -r requirements.txt`

If you need to install any additional packages, you can use 

`$ python3 -m pip install <package>`

#### Your environment should now be properly setup. 

######-------------------------------------------------------------------------------

## Instructions:

After completing environment setup, launch the Jupyter notebook in a Terminal by running:

`jupyter notebook`

######-------------------------------------------------------------------------------

## STAC Specifics
The SpatioTemporal Asset Catalog (STAC) specifies a standard language for structuring and querying geospatial data and metadata. The STAC specification is designed around the extensibility & flexibility of JSON, and is comprised of Catalogs, Collections, Items, and the API.

STAC Catalog: JSON object that contains list of STAC Items, or other child STAC Catalogs. Can be further extended to include additional metadata. No restictions for organization; typically uses ‘sub-catalog’ groupings. [More about STAC Catalog Specification](https://github.com/radiantearth/stac-spec/tree/master/catalog-spec)

STAC Collection: JSON object containing additional info describing the spatial and temporal extents of data; extension of Catalog. Can be further extended to include additional metadata. [More about STAC Collection Specification](https://github.com/radiantearth/stac-spec/blob/master/collection-spec/collection-spec.md)

STAC Item: a GeoJSON feature with descriptive attributes that define its time range and assets; a collection of inseparable data & metadata. Represented in a flexible JSON format. Can indlude additonal fields & JSON structures for further customizing data searches. [More about STAC Item Specification](https://github.com/radiantearth/stac-spec/blob/master/item-spec/item-spec.md)

The SBG-SHIFT STAC Catalog is grouped into the following hierarchy:
```
SBG-SHIFT STAC Catalog 
│
└─── AVIRIS-NG (Collection)
│   │
│   └─── <flight line> (Item)
```
where <flight line> is a STAC item of date form `YYYYMMDD` (see below). For each of these items, there are assets/datasets of form `angYYYYMMDDtHHNNSS.zarr`, a GeoJSON file of the flight outline, and an RGB composite image. 
```  
YYYY:  The year of the airborne flight run.
MM:    The month of the airborne flight run (i.e. 05 represents May).
DD:    The day of the airborne flight run (22 is the 22nd day of the month).
HH:    UTC hour at the start of acquisition
NN:    UTC minute at the start of acquisition
SS:    UTC second at the start of acquisition
```  
