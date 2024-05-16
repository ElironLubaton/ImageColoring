# ImageColoring
Coloring black and white images using deep learning and PyTorch.

The code is found in Colab in the link provided:
https://colab.research.google.com/drive/133oRIf8J-Qe3QejWyXuhKz4DxPkb9dJn?usp=sharing

You can train the model yourself from scratch, or download the pretrained weights and use it to colorize your black and white images.



## Final model's output

![image](https://github.com/ElironLubaton/ImageColoring/assets/125808481/6e33047e-619a-4456-846e-b1856904ff41)

Top row: Greyscale version of the images from test set.
Middle row: Colorized outputs by our model.
Bottom row: Real images from the test set.

___
![image](https://github.com/ElironLubaton/ImageColoring/assets/125808481/76841ba6-b9bf-4e5a-a9b2-aab33e412291)
Top row: Greyscale version of the images from test set.
Middle row: Colorized outputs by our model.
Bottom row: Real images from the test set.

___


## Dataset
We have used the Flowers102 dataset:   https://www.robots.ox.ac.uk/~vgg/data/flowers/102/  
The dataset consists of 8,819 colored pictures of flowers and provides us with a diverse range of flower types in different colors, shapes, picture angels and backgrounds.


## Pre Processing
The pre processing was done in several steps:
#### 1 - Resizing the images to 128X128.
We've managed to train the model properly also with a resize of 256X256, but the training process was much longer.

#### 2 - Converting the images from RGB color space to L*a*b color space.
This is the most important step which improved our results significantly. While working in RGB color space, it is needed to convert the three channels into one channel (grey channel) and then predict three channels again, hoping the image would be colored correctly. Thus, assuming we have 256 choices for each channel of the RGB, we have 256³ different combinations.

While using L*a*b color space, each letter represents:
L - Represents lightness from black to white on a scale of 0 to 100.
a* - On a scale of -110 to 110, negative corresponds with green, positive corresponds with red.
b* - On a scale of -110 to 110, negative corresponds with blue, positive corresponds with yellow.

When using L*a*b color space, we can give the L channel to the model (which is the greyscale image) and we want it to predict the other two channels, a* and b*. Thus, we have 220 choices for two channels, meaning we have $220^2$ 





