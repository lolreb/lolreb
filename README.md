import cv2
from PIL import Image

image_path='лице.jpg'
face_cascade=cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
image=cv2.imread(image_path)
face = face_cascade.detectMultiScale(image)
face = Image.open(image_path)
glasses = Image.open('kk.jpeg')
face = face.convert("RGBA")
glasses = glasses.convert("RGBA")
for (x,y,w,h) in face:
    glasses = glasses.resize((w, int(h/3)))
    face.paste(glasses, (x, int(y+h/4)),glasses)
    face.save("man_with_glasses.png")
    face_with_glasses = cv2.imread("man_with_glasses.png")
    cv2.imshow("Man_with_glasses", face_with_glasses)
    cv2.waitKey()
