# Detects differences between a Single Image and a List of Images (multiprocessing)

## pip install multiwhacamole

### Tested against Python 3.11 / Windows 10

## INPUT 

### 0.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/0.png?raw=true)

### 1.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/1.png?raw=true)


### 2.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/2.png?raw=true)

## OUTPUT - comparison with 0.png 

### 0.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/diff/0.png?raw=true)

### 1.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/diff/1.png?raw=true)

### 2.png

![](https://github.com/hansalemaos/screenshots/blob/main/imagedifference/diff/2.png?raw=true)


```python

import cv2
from multiwhacamole import finddifferences
picturelist = [
	r"C:\Users\hansc\Downloads\dfsdfsdf\0.png",
	r"C:\Users\hansc\Downloads\dfsdfsdf\1.png",
	r"C:\Users\hansc\Downloads\dfsdfsdf\2.png",

]
singlepicture = r"C:\Users\hansc\Downloads\dfsdfsdf\0.png"
df = finddifferences(singlepicture, picturelist,
					 percentage=10,
					 interpolation=cv2.INTER_NEAREST,
					 cpus=5,
					 chunks=1,
					 draw_output=True,
					 usecache=True,
					 print_stdout=False,
					 print_stderr=True,
					 draw_color=(255, 255, 0),
					 thickness=2,
					 thresh=3,
					 maxval=255,
					 save_folder='c:\\testrecognition'
					 )

print(df)

#   aa_start_x aa_start_y aa_end_x aa_end_y aa_center_x aa_center_y aa_width aa_height aa_area                    aa_screenshot  aa_img_index
# 0       <NA>       <NA>     <NA>     <NA>        <NA>        <NA>     <NA>      <NA>    <NA>  [[[253 249 247]\n  [253 249 247             0
# 1         60        780      200      900         130         840      140       120   16800  [[[253 249 247]\n  [253 249 247             1
# 2        620        740      750      870         685         805      130       130   16900  [[[253 249 247]\n  [253 249 247             1
# 3         70        640      200      770         135         705      130       130   16900  [[[253 249 247]\n  [253 249 247             1
# 4       1060        370     1600      710        1330         540      540       340  183600  [[[253 249 247]\n  [253 249 247             1
# 5         10          0      250       90         130          45      240        90   21600  [[[253 249 247]\n  [253 249 247             1
# 6        580        640      620      750         600         695       40       110    4400  [[[  0 255 255]\n  [  0 255 255             2
# 7          0        300     1600      900         800         600     1600       600  960000  [[[  0 255 255]\n  [  0 255 255             2
# 8        900          0     1040       80         970          40      140        80   11200  [[[  0 255 255]\n  [  0 255 255             2
# 9          0          0      810       90         405          45      810        90   72900  [[[  0 255 255]\n  [  0 255 255             2


# If the DataFrame takes too long to print due to the screenshots, use: https://github.com/hansalemaos/PrettyColorPrinter
```