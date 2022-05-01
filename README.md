
## FOREST-CANOPY-DENSITY-DETECTION-SYSTEM
Forest canopy density is one of the most useful parameters to consider in the planning
and implementation of rehabilitation program.Many bands are required for computation
of Forest Canopy Density. Each band correspond to an image.Current technology has
certain limitations is capturing Forest Canopy Density.Firstly these images from satellite
are downloaded to ground stations . This itself takes lots of time and there is a lot of
data as well because satellite image transfers undergoes data loss . Secondly this
process is done under human influence therefore results obtained are subjected to Bias
Our project is to find a solution to this problem.Our project is a python script that can be
run on satellites . Images captured by satellite will be processed by our python file then
the required canopy density map will be produced. Instead of sending many images to
ground station only one resultant map will be sent.

Module-wise implementation details that include, 



MODULE 1: 

![MOD1](https://user-images.githubusercontent.com/52020282/166147158-a8806c5d-3312-4927-98d0-dcac13b0e84f.PNG)


Here we use geemap library and ee library to extract required image collection and feature
collection
Image collection is set of raster images.
Feature collection is set of vector information.
We input the area of interest . In our case we have taken districts as area of interest.
Then we filter the Image collection to get the best possible image for the given area of interest.
IMAHE
In second module we filter the required bands and
apply normalization to each band. We do this by using
the normalization formula .
[IMAGE] \
MODULE 2: 

![MOD2](https://user-images.githubusercontent.com/52020282/166147167-baeb25b1-03c8-4ad5-b710-e3b74a2f7d2f.PNG)


MODULE 3: 

![mod3](https://user-images.githubusercontent.com/52020282/166147171-8aa32654-9164-451a-bfb1-41ae92abc2db.PNG)


In third module we do band computation on normalized primary bands to generate required secondary bands which will required in further
computation. The formulas were mentioned in the
research paper. Then we visualize the these bands.

![1](https://user-images.githubusercontent.com/52020282/166147385-2681c541-694b-4800-8ea3-a5a442003e8e.PNG)



MODULE-4

In fourth module we do the prerequisite of Principal
Component Analysis.Our images are in earth engine
object format . We need to convert these earth engine
object int tiff images with compression format 'ZSTD'.
In 'ZSTD' format maximum amount of information is
retained.We use GDAL library for this conversion.

![MOD4](https://user-images.githubusercontent.com/52020282/166147184-c42b732f-ab6b-42b1-9abe-63bbe01eed8f.PNG)




We then save the calculated bands into colab directories. We need these images for
performing PCA . We use gdal library to convert the images to .tiff format with PACKBITS
compression. PACKBITS compression retains the most amount of data . 

MODULE - 5 \
In fifth module we do PCA on our image.We run PCA only on AVI band and BI band.We use whitebox library for PCA computation.First we configure White box
module then we run PCA module of Whitebox.
After we have processed the image we use the white
box library to produce the Forest Canopy Density map.

In final module we will perform PCA on the calculated bands . We will use Whitebox library
for this module. After PCA we will get Vegetation Density band and Scaled Shadow index
band. These two will be used to develop our Forest Canopy density map.
Essentially we will automating this entire process , that is given raw image and a region of
interest we can produce a Forest Canopy Density Map. 

Summarize the key points. 
- We first filter the required region of interest image
- Then we develop some functions which will required for
image computation
- After that we normalize our selected primary bands and
calculate secondary bands.
- Now we convert these secondary band images into images
with particular type of compression
- Lastly we need to perform PCA on secondary images and do
final computation to produce Forest Canopy Density Map.
