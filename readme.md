# Project Car classifier

1. Started to find a dataset, first I tried to find a dataset by myself. Tried to find all the pics by myself. As a Used car dealer I thought I had enough pictures just by my own library
but that wasn't enough. After some searching and downloading pictures itself I found this dataset on the ethernet : ![Stanford dataset](fotos/Stanford.png)
https://ai.stanford.edu/~jkrause/cars/car_dataset.html

2. It were all random pictures so I kept searching on a dataset where someone already mapped the photo's. I found one on Kaggle.com : ![Kaggle](fotos/Kaggle.png)
https://www.kaggle.com/jutrera/stanford-car-dataset-by-classes-folder

3. I tried to make a car classifier in Jupyter notebook with Keras. Tried multiple times with other Epochs and different Batch sizes but the conclusion was that Keras wasn't good in my situation because you can only get it to work with your GPU if you are a  Nvidia Developer. Training the model took between the 24 hours and the 36 hours : ![Epochs](fotos/Epoch.png)

4. Here you can see the results of a small 25h hours of training. Not such good results with Keras.
![Kaggle](fotos/ResultEpoch.png)

Then I reversed it, Less epochs and bigger Batch sizes means better results. : 
![Kaggle](fotos/Result2.png)

5. Still not the results I hoped for and tried another model. Instead with Keras I went with PyTorch. PyTorch was able to work with my gpu which was heaven on earth compared to keras who always took multiple hours of my CPU running 100%. It's now with a pre trained model called Resnet34. It works with PyTorch. 
These are the results : 

These are the graphs and statistics of the results from the model : 
![Kaggle](fotos/ResultPy.png)

Prediction of this beautiful Volkswagen Beetle : 
![Kaggle](fotos/ResultBeetle.png)

Prediction of this sports car : 
![Kaggle](fotos/ResultFerrari.png)

6. The Beetle is 100% right. The Ferrari is not fully wrong. The Ferrari on the photo that I took by myself and used is the newer Model. A Ferrari 488.
Now I picked a tricky car. A car that is actually the same car as another one but just with a different badge. It's a car that I sold recently. An Abarth 595 who shares it's chassis with the normal Fiat 500. Only difference are the badges and another engine. As you can see I took the picture from the side to trick the model but he has it semi-right because he took the fiat.

![Kaggle](fotos/ResultAbarth.png)
