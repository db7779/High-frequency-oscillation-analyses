# High frequency oscillations in iEEG during word presentation and recall
This repository covers three analysis approaches to make sense of high frequency brain oscillations (HFOs) and their temporal/spatial patterns in relation to semantic categories of words. 
The data is obtained from iEEG recordings of epileptic patients, pre-operatively. Each patient is presented with a number of words (encoding phase), and after some distraction task, she/he needs to recall as many of the words that were previously presented (recall phase). The words belong to one of predefined 17 semantic categories.

The main data consists of csv files, one for each word, in two directories (~/encode and ~/recall), that have a column indicating the brain area (in MNI level) and ~300 columns indicating time bins, with event of word presentation or recalling being in the middle timebin. Values are binary: 0 indicating an absence of HFO in the MNI x timebin, and 1 indicating a presence of HFO.

# Dimensionality reduction of HFO rates
The first approach is an exploratory analysis of average HFO rates using three dimensionality reduction techniques, PCA, ICA & tSNE. Graphical inspection for 2D and 3D reducted data is done for each subject (number of MNI areas and anatomical location vary between subjects), for before and after word presentation (encode) or recalling (recall).

# Weighted graph measures
For the second approach, we have obtained cross correlation matrices for MNI areas of the temporal lobe and we calculate several graph measures for each word's correlation matrix (weighted graph), in order to later group by semantic categories and investigate intra-lobe differences. Output dataframe is a condition_word x graph measures.

# LSTM & 1D CNN
We apply LSTM and 1D CNN algorithms to the HFO time series data, for the prediction task of recalled vs not-recalled (word-level). The input data is the words' csv files MNI x timebins containing the HFO time series (multivariate time series, MNIs being the variates), in the encoding phase (so good performance of the models would indicate that we can predict which words are going to be remembered, by the HFO activity during word encoding). The timebins used can be for the first half (before word presentation) or for the second half.
