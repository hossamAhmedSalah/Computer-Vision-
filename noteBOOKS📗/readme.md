## Cv001 
demostrating some usage of _opencv_ in dealing with images and videos input 
and doing some Color threshold to remove the background from an image and replace it 


[notebook cv001](/cv001.ipynb)
--------------------------------------------------------
How can different color spaces affect the process of detecting some colors easily ? 
--------------------------------------------------------
Color spaces 
- RGB (Red, Green, Blue) <0, 255> 
- HSV (Hue, Saturation, Value) <0=>180>
- HLS (Huc, Lightness, Saturation) 
in this notebok I used several images of ballons to compare them in various filters and masks 
to show which is better in detecting the color for this case 'pink'


[ballons🎈](balloons.ipynb)
---------------------------------------------------------
How can different between Night and Day in images using features extracted from the images ? 
--------------------------------------------------------
[day and night🌞🌚](dayAndNight.ipynb)
---------------------------------------------------------
Applying some filters and see how they help in edge detecting
--------------------------------------------------------
[filters🖼️](filters.ipynb)
contains some studies of how 
- to make custome kerenal 
- to use guassian filter
- low pass filters 
- high pass filters
- cane edge detection 
- hysteresis thresholding 
- a function to plot one row of images and another one to plot a grid of images 
**ploting one row**
```python
def plot2(images, rows, cols, labels = None, sizex = 20, sizey = 10):
    if len(images) < rows * cols:
        print("Number of images is less than the number of subplots.")
        return
    fig, axs = plt.subplots(rows, cols, figsize=(sizex, sizey))
    for i in range(rows):
        for j in range(cols):
            axs[j].imshow(images[j], cmap = 'gray')
            if labels:
                axs[j].set_title(labels[j])
            else :
                axs[j].set_title(f"image_{j}")
    plt.show()
```
**ploting a grid of images**
```python
def plot_images(images, rows, cols, labels = None, sizex = 20, sizey = 10):
    if len(images) < rows * cols and rows != 1:
        print("Number of images is less than the number of subplots. or rows = 1")
        return
    fig, axs = plt.subplots(rows, cols, figsize=(sizex, sizey))
    for row in range(rows):
        for col in range(cols):
            axs[row,col].imshow(images[row*cols+col])
            if labels:
                axs[row,col].set_title(labels[row*cols+col])
            else:
                axs[row,col].set_title(f"image_{row*cols+col}")
    plt.show()
```
note that 💡 ```labels```, ```sizex```, ```sizey``` are optional parameters
that mean you can use it as follow :
```python
plot2([image1, image2], 1, 2, ['sunny', 'not sunny'])
```
or 
'''
plot2([image1, image2], 1, 2, sizex = 40, sizey = 60)
'''
in the last case the images takes a default name as image_<image_index>
we can also ommit the ```sizex``` and ```sizey```




