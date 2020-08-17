# Project Car classifier

1. Started to find a dataset, first I tried to find a dataset by myself. Tried to find all the pics by myself. As a Used car dealer I thought I had enough pictures just by my own library
but that wasn't enough. After some searching and downloading pictures itself I found this dataset on the ethernet : ![Stanford dataset](fotos/Stanford.png)
https://ai.stanford.edu/~jkrause/cars/car_dataset.html

2. It were all random pictures so I kept searching on a dataset where someone already mapped the photo's. I found one on Kaggle.com : ![Kaggle](fotos/Kaggle.png)
https://www.kaggle.com/jutrera/stanford-car-dataset-by-classes-folder

3. I tried to make a car classifier in Jupyter notebook with Keras. Tried multiple times with other Epochs and different Batch sizes but the conclusion was that Keras wasn't good in my situation because you can only get it to work with your GPU if you are a  Nvidia Developer. Training the model took between the 24 hours and the 36 hours : ![Epochs](fotos/Epoch.png)

4. Here you can see the results of a small 25h hours of training. Not such good results with Keras.

![Result](fotos/ResultEpoch.png)

Then I reversed it, Less epochs and bigger Batch sizes means better results. : 

![Result](fotos/Result2.png)

5. Still not the results I hoped for and tried another model. Instead with Keras I went with PyTorch. PyTorch was able to work with my gpu which was heaven on earth compared to keras who always took multiple hours of my CPU running 100%. It's now with a pre trained model called Resnet34. It works with PyTorch. Now with the help of my GPU the epochs only take a couple of minutes instead of almost an hour.
These are the results : 

These are the graphs and statistics of the results from the model : 
![Result](fotos/EpochPy.png)

![Result](fotos/ResultPy.png)

Prediction of this beautiful Volkswagen Beetle : 
![Car](fotos/ResultBeetle.png)

Prediction of this sports car : 
![Car](fotos/ResultFerrari.png)

6. The Beetle is 100% right. The Ferrari is not fully wrong. The Ferrari on the photo that I took by myself and used is the newer Model. A Ferrari 488.
Now I picked a tricky car. A car that is actually the same car as another one but just with a different badge. It's a car that I sold recently. An Abarth 595 who shares it's chassis with the normal Fiat 500. Only difference are the badges and another engine. As you can see I took the picture from the side to trick the model but he has it semi-right because he took the fiat.

![Car](fotos/ResultAbarth.png)


# Number plate detector

After the car classifier I wanted to try something else with cars. I found a pre trained model called YOLO (https://pjreddie.com/darknet/yolo/). With Yolo it would be possible to let the model check if there would be a number plate or not. At my home we installed a new camera system recently and because of security reasons I was thinking about using number plate recognition. But it wasn't possible with just a normal camera only with a ANPR camera but that comes with a heavy price tag (around €700). Now I wanted to try to make it myself and first I tried it on my own pictures to see what would happen. I got so far that I can detect them from a picture but I can't read them. These are the results : 

Picture from the front, easy to see

![Car](fotos/Opel.jpg)

Picture bit more difficult from the side

![Car](fotos/Opel2.jpg)

Picture from a custom number plate

![Car](fotos/Jaguar.jpg)


When there is no number plate he says nothing and also doesn't leave a marking on the photo

![Car](fotos/Bugatti.jpg)

# Object detector


1. Videos

As I said earlier we recently installed a new camera system. There is already motion detection in the camera's built in. I would maybe like to go a step further and install some other detection in. Like detection and counting of cars so I can see what is where going on. Counting cars on the parking lot or count who many people are in. But first before I start or maybe try to do that I'm gonna start with the detection of the camera's. My first example is footage of the camera who hangs outside to see a couple of my own cars who are parked up front. As you can see it's a small video of 10 seconds where you can see that he detects my own cars that are parked and the 2 cars that are driving by. In those small 10 seconds there were more than 311 frames. To let the model see the video takes a small 15 minutes. 
![Car](fotos/ResultVideo.png)

Before:
https://youtu.be/iLS4YvHryQA

After : 
https://www.youtube.com/watch?v=k4OpxJY5OCw&feature=youtu.be

2. Images 

With object detection I used Yolo again because I already had some experience with it. I also found a tutorial online who would help me with it. As you can see the pre trained model even detects animals, cars humans. It's perfect for the security reason I've picked it. Here are some results : 

![Car](fotos/foto.jpg)
![Car](fotos/Huis1.jpg)
![Car](fotos/lambo.jpg)


This is a picture the camera took when he tracked some motion. As you can see it tracks even more than i thought : 

![picture](fotos/halbuiten2-det.jpg)

# Combining the projects

I wanted to try if it would be possible to combine the projects with eachother and let the computer decide everything. I tried it first with my own footage from the camera's but they were to far away or the quality wasn't good enough. The problem with the object classifier is that it makes the quality worser from the picture : 

Original Photo : 

![picture](fotos/halbuiten2.jpg)

Detected Photo : 

![picture](fotos/halbuiten2-det.jpg)

Now trying the number plate :

Orig : 

![picture](fotos/halbuiten2_yolo_out_py.jpg)

Detected Photo : 

![picture](fotos/halbuiten2-det-cut.jpg)


As you can see on the pictures they look trimmed down in quality. When it are clear pictures like the one that I have used before it isn't a problem but when it's already from a distance with only a 5mp camera it's not usable. 

When I take HQ pictures from the ethernet doesn't mean it has a 100% rate. From the 3 pictures that I took only this one worked : 


![picture](fotos/car25-det_yolo_out_py.jpg)


After some testing of the number plate detector the biggest reason why he couldn't detecte the number plate is because it's from a difficult angle to recognize it and when I first use Car detector it's more difficult for the number plate detector to detect it. So know we now that our Number plate detector is our weakest point because the car detector does almost work everytime.

Here are some other examples where you can see that the number plate is good readable and easy to predict : 


![picture](fotos/Opel-det.jpg)

![picture](fotos/Jaguar-det.jpg)



Now I'm going to combine my 3 projects. First I'm gonna let the car classifier predict what kind of car it is : 

![picture](fotos/ResultBeetle.png)

He predicted it right, a Volkswagen Beetle from 2012. Now we are gonna predict if he has a number plate or not and where it is on the picture : 

![picture](fotos/beetle_yolo_out_py.jpg)

He predicted it right, he has a number plate. After the prediction of the number plate now we are gonna check object itself. Maybe there are even other objects in the picture like we have seen before on the other pictures that I used : 

![picture](fotos/beetle_yolo_out_py-det.jpg)

This is another example. First I ran the image through the car classifier as you can see he predicted it right : It's a Mercedes SL Series 

![picture](fotos/SL.png)

After I ran it through the classifier I wanted to try the car detector first because the image was from good quality so it would be possible to first through the image detector instead of the number plate : 

![picture](fotos/SL-det.jpg)

![picture](fotos/SL-det_yolo_out_py.jpg)

As you can see both were detected right. It was a good frontal picture of the car, the image loss the detection gave wasn't a problem at all.


# Statistics

For statistics I've picked multiple subjects and the first subject that I'm gonna show you are graphs from a dataset that I found online that has all the info over cars.
From MPG to MSRP etc : 
https://www.kaggle.com/CooperUnion/cardataset

In the first photo I'm going to show you the top 5 rows from the dataset so you can see how the data can be interpreted : 

![picture](stat/Top5.png)

The data has 12000 records that's big enough to have a nice average.

First I'm going to show you the years. As you can see on the graph most of the records that are in this dataset are from 2015 until 2017 because the dataset doesn't have the last recent models. The reason why it has a peak in the last years is because this dataset does have more records from 2010-2015 against 1990-1995.

![picture](stat/Year.png)
