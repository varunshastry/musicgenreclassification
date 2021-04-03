# musicgenreclassification

What?
Identify the genre of the given audio sample (wav format)

How?
k-nearest-neighbour algorithm ( https://cs.carleton.edu/cs_comps/0910/netflixprize/final_results/knn/index.html ), popularly known as kNN, is typically used for classification and regression in machine learning. It computes the 'distance' between each entity and every other entity in the dataset, and creates groups of entities wherein the 'distance' between the entities is least and each group contains 'k' entities.
The 'distance' is an umbrella term which comprises of the differences between multiple attributes/features of the entities. In this specific case, the Mel Frequency Cepstral Coefficients would be the features of the audio samples used for computing the 'distance'.

Since this is supervised learning, the GTZAN dataset ( http://marsyas.info/downloads/datasets.html ) would be used to train the models. The dataset contains:
1,000 audio tracks
Each track is 30 secs long
10 genres - Blues, Classical, Country, Disco, Hiphop, Jazz, Metal, Pop, Reggae, Rock
Each genre contains 100 songs
As part of training the models, the following steps would be performed on each audio sample in the dataset:

Split the audio track into smaller frames of length 20 ms to 40 ms
Identify different frequencies in each frame
Separate the linguistic frequencies from noise
Eliminate noise by applying Discrete Cosine Transform (DCT) of these frequencies in each frame
As an output of training the models, the extracted features would be dumped into a DAT file, and this file would be used to test the models.

Takeaways
Basics of supervised machine learning - kNN
Basics of speech processing features in Python
Basics of Mel Frequency Cepstral Coefficients (MFCC)

Tools/Libraries
Python (and pip) 3.8
Python libraries
mfcc
numpy
scipy
Setup
Download and install python (and pip) 3.8 - https://www.python.org/downloads/
Set the env variable "PYTHONPATH"

For example → export PYTHONPATH=/usr/local/lib/python3.8/site-packages

Install pip →python -m pip install --upgrade pip setuptools wheel  (// run it from command prompt)
Install the libraries using → pip3.8 install -U numpy scipy python_speech_features

Code
Code to generate and train the models: classify_music_genre_script.py
Code to test the models: test_classify_music_genre_script.py

How to run?
Download the GTZAN data set from here into a directory (say ~/music-genre-classification/genres)
Unzip the downloaded dataset into the directory - genres
Download the source code (classify_music_genre_script.py and test_classify_music_genre_script.py) into a directory (say ~/music-genre-classification)
In the classify_music_genre_script.py file, in line no 53, change the directory to ~/music-genre-classification/genres
In the test_classify_music_genre_script.py file, in line no 63, change the directory to ~/music-genre-classification/genres
Train the models:
cd ~/music-genre-classification
python3.8 classify_music_genre_script.py
Successful execution of above command would result in the generation of my.dat file in the ~/music-genre-classification directory
Test the models by passing an audio sample file name as parameter to the script:
python3.8 test_classify_music_genre_script.py ~/MusicGenreClassification/genres/reggae/reggae.00054.wav
