# Urban-Sound-Classification

#I ntro (About dataset)

This dataset contains 8732 labeled sound excerpts (<=4s) of urban sounds from 10 classes: air_conditioner, car_horn, children_playing, dog_bark, drilling, enginge_idling, gun_shot, jackhammer, siren, and street_music. The classes are drawn from the urban sound taxonomy. For a detailed description of the dataset and how it was compiled please refer to our paper. All excerpts are taken from field recordings uploaded to www.freesound.org. The files are pre-sorted into ten folds (folders named fold1-fold10) to help in the reproduction of and comparison with the automatic classification results reported in the article above.

In addition to the sound excerpts, a CSV file containing metadata about each excerpt is also provided.
# Methodology

There are 3 basic methods to extract features from audio file :
a) Using the mffcs data of the audio files (we can then use RNN based models like LSTMs, GRUs to train on these features)<br>
b) Using a spectogram image of the audio and then converting the same to data points (As is done for images). This is easily done using mel_spectogram function of Librosa (This involves CNNs)<br>
c) Combining both features to build a better model. (Requires a lot of time to read and extract data).<br>

I have chosen to use the second method. The labels have been converted to categorical data for classification. CNN has been used as the primary layer to classify data<br>

## Librosa
Librosa was used for data preprocessing and feature extraction.
Features available using Librosa :<br/>
### MEL Features
#### MFCC <br/>
In sound processing, the mel-frequency cepstrum (MFC) is a representation of the short-term power spectrum of a sound, based on a linear cosine transform of a log power spectrum on a nonlinear mel scale of frequency.<br/>
Mel-frequency cepstral coefficients (MFCCs) are coefficients that collectively make up an MFC. They are derived from a type of cepstral representation of the audio clip (a nonlinear "spectrum-of-a-spectrum").<br/>
#### MFCC of a dog bark<br/>
![image](https://user-images.githubusercontent.com/31596604/51472544-ce520c80-1d9f-11e9-883c-e08c4463a5b4.png)<br/>
#### Melspectrogram <br/>
A mel-scaled spectrogram.<br/>
#### Melspectrogram of a dog bark<br/>
![image](https://user-images.githubusercontent.com/31596604/51472743-5f28e800-1da0-11e9-9402-5ba41dfefae5.png)<br/>
### Chroma Features
In music, the term chroma feature or chromagram closely relates to the twelve different pitch classes. Chroma-based features, which are also referred to as "pitch class profiles", are a powerful tool for analyzing music whose pitches can be meaningfully categorized (often into twelve categories) and whose tuning approximates to the equal-tempered scale. One main property of chroma features is that they capture harmonic and melodic characteristics of music, while being robust to changes in timbre and instrumentation.<br/>
#### Chroma_stft<br/>
A chromagram from a waveform or power spectrogram.<br/>
#### Chromagram of a dog bark<br/>
![image](https://user-images.githubusercontent.com/31596604/51472838-a616dd80-1da0-11e9-87f3-54a6a9e03170.png)<br/>
#### Chroma_cqt<br/>
Constant-Q chromagram.<br/>
#### Constant-Q chromagram of a dog bark<br/>
![image](https://user-images.githubusercontent.com/31596604/51472906-e0807a80-1da0-11e9-8988-f060eed38957.png)<br/>
#### Chroma_cens<br/>
The chroma variant “Chroma Energy Normalized” (CENS).<br/>
#### Chroma cens of a dog bark<br/>
![image](https://user-images.githubusercontent.com/31596604/51472963-09087480-1da1-11e9-863f-084b84ecd584.png)<br/>

# TODO

## Neural Network Implementation 
A simple Neural Network with dropouts was used.<br/>
The following results are obtained by training on folders 1-9 and testing on folder 10. <br />
Train accuracy: 93.14% <br />
Test accuracy: 66.06%<br />

## Convolutional Neural Network Implementation 
A convolutional Neural Network with dropouts was used.<br/>
The following results are obtained by training on folders 1-9 and testing on folder 10. <br />
Train accuracy: 95.90% <br />
Test accuracy: 73.11%<br />

References -> 
https://github.com/AmritK10/Urban-Sound-Classification/blob/master/Urban_data_preprocess.ipynb<br>
https://github.com/AmritK10/Urban-Sound-Classification<br>
https://github.com/AmritK10/Urban-Sound-Classification/blob/master/Urban_cnn_model.ipynb<br>
