# Big-Data-Course

# Car recognizing

Als autohandelaar zijnde als student-ondernemer ben ik op het idee gekomen om een autoherkenningsprogramma te schrijven. Ik ben begonnen met een dataset te maken. Ik had al zelf veel bruikbare data aan de hand van al verkochte auto's, ik kwam uiteraard nog vele foto's te kort dus ben ik begonnen met foto's van Flickr.com en Unsplash.com. Na vele downloads verder en wat gecodeerd te hebben besloot ik dat deze dataset die ik zelf gemaakt had onvoldoende was om hiermee verder te gaan. Na wat google verder kwam ik op deze dataset terecht : https://ai.stanford.edu/~jkrause/cars/car_dataset.htm.
![Screenshot](TotalImages.png)

Na wat verder gezocht te hebben was er al iemand die deze onderverdeeld had : 
https://www.kaggle.com/jutrera/stanford-car-dataset-by-classes-folder. 
Nu gebruik ik deze en dit zijn de resultaten :

![Screenshot](Error1.png)





Het programma begint met alle libraries te importeren die ik nodig heb.

![Screenshot](Importeren.png)

Daarna controleer ik of hij de juiste directory wel vind.

![Screenshot](Fotodirectory.png)

Daarna worden de klassen ingelezen, dus per voertuig de klasnamen en het merk.

![Screenshot](classnamen.png)

Daarna importeren we de Keras libraries verder

![Screenshot](importeren2.png)

Daarna zetten we de parameters voor het model klaar, alsook word getest of ik in de juiste directory zit door de images die geteld worden samen met de klassen.

![Screenshot](Parameters.png)

Na dat de parameters zijn gedeclareerd maken we de methode om het model te maken.

![Screenshot](buildModel.png)

Hiermee begint het model met trainen.

![Screenshot](trainModel.png)



Dit is een ruwe dataset met pure foto's, na deze gebruikt te hebben kwam ik uiteraard op de fout dat deze nog moest onderverdeeld worden in de klassen en categorieën.
![Screenshot](BigData.png)








Heb deze maar even laten runnen omdat deze te groot en teveel lagen gebruikte. Dit betekent uiteraard wel meer nauwkeurigheid, dit is ook een andere en een iets meer geavanceerdere techniek tegenover diegene die ik nu op het einde gebruik. Dit verschil zit puur in de code van het model te creëren. De techniek heet transfer learning, deze techniek is beter dan de techniek die ik nu gebruik als het om ongeveer dezelfde taken zouden zijn dus niet echt specifiek maar eerder generiek, door de mindere lagen hebben we wel meer kans op overfitting dit betekent dat er te weinig lagen gekent zijn om het juiste resultaat te kunnen geven.

![Screenshot](LangeVersie.png)
