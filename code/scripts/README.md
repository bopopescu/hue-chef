### Folder Structure & naming: 

### Init Script:

- data_appender.sh
- Param: starting $ or starting folder name. 

#### ./data/raw_images/
- Folder name is $, where $ is a numeric value.
- Each folder will have 100 images. 
- Responsibility of Folder *i* is images [(i-1) * 100 + 1, i * 100].
- *For example:* Folder 3 will be responsible for images [201 to 300].

#### ./data/reduced_images/ 

- Structure: { exact same structure as raw_images }
- All the image files in /reduced_images/ folder will be of size [255 x 255].

#### ./data/palette_data

- $.json corresponds to the palette information for folder $.
- *Example*: 5.json will have palettes for images 401 to 500. 


### Files:

- **image_generator.py** => Resizes all the training images to [255 x 255].
```
python image_generator.py -i <foldername>
```
- **palette_generator.py** => Uses ColorMind API to generate palette for the the resized images and store them in a JSON file. 
```
python palette_generator.py -i <foldername>
```


### Steps: 

> - The input files are images present in the data directory that are read by ImageGenerator.py to produce a json file in the format Eg. <Image_name1>.jpg, <Image_name2>.jpg
>- {
  "Image_name1" : [ [R,G,B],.......(255X255)],
  "Image_name2" : [ [R,G,B],.......(255X255)]
  }

>- The input files are images present in the data directory that are read by PaletteGenerator.py to produce a 5 tuple palette for every image as json in the output. Eg. <Image_name1>.jpg, <Image_name2>.jpg

>- {
  "Image_name1" : [[R,G,B],....5],
  "Image_name2" : [[R,G,B],.....5]
  }
