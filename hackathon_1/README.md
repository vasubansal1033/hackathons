submissionNotebook.iypnb and submissionNotebook1.ipynb contains the basic CNN models. submission3.ipynb contains the best model. <br> 

This folder contains my code for JanataHack: Computer Vision Hackathon, organized by Analytics Vidhya during COVID-19 pandemic. Link for the same is here https://datahack.analyticsvidhya.com/contest/janatahack-computer-vision-hackathon/#ProblemStatement <br>

# Importance of problem
Fatalities due to traffic delays of emergency vehicles such as ambulance & fire brigade is a huge problem. In daily life, we often see that emergency vehicles face difficulty in passing through traffic. So differentiating a vehicle into an emergency and non emergency category can be an important component in traffic monitoring as well as self drive car systems as reaching on time to their destination is critical for these services.
We are provided with the train and the test dataset. Emergency vehicles usually includes police cars, ambulance and fire brigades.<br>

The evaluation metric for this competition is Accuracy.

# My approach
The train dataset providede consisted of 2352 images, which included both train images and the test images on which we had to predict. The train and test images were mentioned in .csv files provided. I performed 90/10 train-validation dataset split on the train images. <br>
The images were of size (224, 224) and were colored.

So I started with a basic CNN model which consisted of Convolution layers followed by Max pool layers(in pairs of 3). Then a fully connected layer of 512 units. Since it's a binary classification the output layer consisted of 1 unit layer with sigmoid activation. I used RMSProp as the optimizer and binary cross entropy as my loss function. I used relu activation for the most part. Trained the model for 20 epochs. This model heavily overfitted the train data as the accuracy I got was 99.66% on the train set and 80.12% on the validation set. I tried experimenting with the number of filters, their sizes from (2,2), (3,3) a bit but the model overfitted a lot. <br>

Then I tried using data augmentation using standard transformations like rotation, width and height shift, shear distortion, zoom and flipping. I trained again this time with 80 epochs and I got an accuracy of 87.5% on train set and 88.55% on the validation set which was a heavy improvement. One thing to notice was that there was a large peak in the middle of the validation loss function, which could mean that the loss function used is not resulting in a proper convex function.<br>
I trained this model for 10 more epochs and got 89.59% on train dataset and 90.96% on the validation set. The performance was still increasing at a steady rate, but I decided to stop here as I thought I should go for getting good results on a lesser number of epochs.<br>
I submitted the predictions with this model and got a rank 338 out of about 450 participants. The private score was 0.837. <br>
 
 Next I decided to use Transfer learning. I chose pre-trained InceptionV3 for this task. All layers were frozen and at the end I added two convolution Dense layers each having 128 units with relu activation, keeping everything else same from the previous training. I trained this model for 20 epochs and got an accuracy of 0.9443 on train set and validation accuracy of 97.5%. This model resulted in a rank of 203 and private score of 0.93779.<br>
I trained this model for 40 more epochs and got got an accuracy of 95.9% on train set and validation accuracy of 98.12% on validation set. This model gave a score of 0.966 and I got a rank of 89 among 450 participants. <br>
I did not continue further with training this model as the loss functions were fluctuating at the end and the overall trend was not decreasing by a good amount.


