# Praca z obrazami - OpenCV + Python
## Import zależności
```
import imutils
import cv2
from google.colab.patches import cv2_imshow
```
## Ładowanie obrazu
```
image = cv2.imread("vikings.jpg")
(h, w, d) = image.shape
```

## Wyświetlenie długości, wysokości i głębokości obrazu
```
print("width={}, height={}, depth={}".format(w, h, d))
```
## Wyświetlenie obrazu
```
cv2_imshow(image)
```
