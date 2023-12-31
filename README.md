# Image-Recognition-with-TensorFlow-and-Keras
Build a simple image recognition model using TensorFlow and Keras.
from tensorflow.keras.applications import MobileNetV2
from tensorflow.keras.preprocessing import image
from tensorflow.keras.applications.mobilenet_v2 import preprocess_input, decode_predictions
import numpy as np

model = MobileNetV2(weights='imagenet')

img_path = 'image.jpg'
img = image.load_img(img_path, target_size=(224, 224))
x = image.img_to_array(img)
x = np.expand_dims(x, axis=0)
x = preprocess_input(x)

preds = model.predict(x)
decoded_preds = decode_predictions(preds, top=3)[0]

print(f"Top Predictions: {decoded_preds}")
