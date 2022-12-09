I am having issues with the coco dataset. It is coming with segmentation with RLE format (when iscrowed = 1) 
and the python code knows how to handle it only when it comes in the polygon format (when iscrowed=0). I successfully 
trained a coco dataset containing the cangaroon label where iscrowed was equal to 0. I could not find a workaround 
for the dataset trained using CVAT and DEXTR cutter since it is coming as a COCO json RLE format. 

I modify the MaskRCNN code as I could and added it to the repository. 
