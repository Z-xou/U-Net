# U-Net

**Introduction**

Existing applications of U-Net apply the telescope data for training and testing the model; this trained model may not be suitable for other telescope data. Since telescopes have different resolutions - some datasets depict elongated, thin filaments, while others shorten, thick filamentary structures. Therefore, training a neural network on the universal dataset that can then be employed for various astronomical data is quite beneficial. 
This study exploits the efficiency of U-Net trained on geometrical shapes such as rectangles and ellipses to approximate filamentary structures and their orientation angles, which can expand the model's scope of application. 

**Methods**

Overall, you will need training dataset (rectangles, ellipses) and testing dataset (Herschel, Planck telescope data) for the model. This U-Net model requires image_input and mask_input to our training data. This is how they look:

<img width="535" alt="Снимок экрана 2022-12-28 в 00 38 44" src="https://user-images.githubusercontent.com/74349608/209708692-22b6cdc3-f0da-421a-a1df-c9455dcfb488.png">

These figures’ widths range from 1/15 of the map to ⅓ of the map, and the heights are from 1/10 of the width to ⅓ of the width. The rotation angles of the figures are 1-180; angles are counted from the vertical line directed to the left and increasing toward the lower vertical. The *image_input* are binary images. 

The maps for the *mask_input* are also 128x128-sized images, where each pixel represents the angles of the rotated figures or 0 if there is no rectangle, so there are 181 classes.

In the *training dataset* there are 10-90 such figures (rectangle, ellipse) with a step of 10. By alternating the sizes, shapes of the figures in the training dataset, the performance of our model also changes. 

Sometimes, the *test dataset* requires data preprocessing - as to scale the values in the image for the proper format, change the image sizes, turn fits files into png format an etc.

**Files**

There are several code sources, below is the brief introduction: 

* UNet.ipynb
  - If you want to know more about the code: https://github.com/bnsreenu/python_for_image_processing_APEER/blob/master/tutorial121b_loading_data_from_drive_in_batches_for_unet_training.ipynb

* Rell.ipynb (shortly from rectangle + ellipse)
  - This is where training dataset is generated
