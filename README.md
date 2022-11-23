# 2021 NASA Harvest Rwanda Baseline Model
<img src='https://radiant-assets.s3-us-west-2.amazonaws.com/PrimaryRadiantMLHubLogo.png' alt='Radiant MLHub Logo' width='300'/>
This notebook walks you through the steps to create a baseline field delineation model for detecting boundaries from sentinel-2 time-series satellite imagery using a spatio-temporal U-Net model on the 2021 NASA Harvest dataset for the Zindi competition.

## About
The dataset for this competition includes a time series of satellite imagery from Planet’s NICFI basemaps (license agreement) and labels for field boundaries that were annotated on the same imagery source. The labels were digitized over Planet Basemaps for the months of March, April (on season) and August (off season) of 2021 by a team of annotators from TaQadam. An additional 3 months of imagery (October, November and December) are added to the time series data and are then matched with corresponding field boundary labels.

The time-series is provided for six months (March, April, August, October, November and December), but you do not need to use the observations from all months. You are allowed to select specific months, or apply any pre-processing and feature extraction to the time-series data before input to your model. Note that you would need to provide your full feature-extraction and training scripts if you win in the competition.

The data you will have access to (Satellite imagery and labels) are tiled into 256x256 chips adding up to 70 tiles. Within those 70 tiles 1532 individual field boundaries have been identified. The dataset has been split into training and test chips (57 in the train and 13 in the test). You will train your machine learning model on the fields included in the training chips and will apply your model to predict field boundaries for chips in the test set. You will submit your predictions for field boundary masks for the list of chips in the test dataset.

Labels were created only for fields large enough to be distinguished on the planet basemaps and for fields completely contained in the chip; this means that not all the pixels are labeled in each chip .

Each chip has:

* Planet imagery for 4 bands `[B01, B02, B03, B04]` mapped to a common 3.7m spatial resolution grid for 6 timestamps `[2021_03, 2021_04, 2021_08, 2021_10, 2021_11, 2021_12]`
* A raster layer indicating the extent of field boundaries for the fields in the train set.
Data for this competition is hosted on Radiant MLHub - open-access repository for geospatial data. You can access the data by creating a free account on Radiant MLHub.

You can download the data using Radiant MLHub Python Client (see the example notebook) or simply by going to the Radiant MLHub website.

The data is structured in three collections based on the metadata specification of SpatioTemporal Asset Catalog (STAC):

* Source train collection: contains all the source imagery for the train set.
* Source test collection: contains all the source imagery for the test set
* Train label collection: Defines the training set, and contains the field boundary masks of fields in the train collection

### Variables definitions:

The label chips contain the mapping of pixels to crop type labels. The following pixel values correspond to the following crop types:

* 1 - Crop field boundary
* 0 - Not field boundary

## Submission files



