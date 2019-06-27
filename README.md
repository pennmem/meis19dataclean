# meis19dataclean
Data and code used in Steven Meisler's paper in iEEG preprocessing

# Subject Data Structures
Subject data structures may be found in (XXXXX). To load a subject's data and assign it to a variable, use $VAR_NAME$ = np.load('$PATH_TO_SUBJECT_DATA$')['data'][()]

You can use the following keys to index into the structures. Each element represents data from a different session. A lot of these data were gathered using the CMLReader (documentation can be found here: https://github.com/pennmem/cmlreaders):
'D'/'G'/'S': Indices of Depth, Grid, and Strip electrodes, respectively.

'contacts': Data frame with electrode information, such as label name, region, and coordinates.

'num_contacts': Number of contacts per session.

'pairs': Similar to 'contacts', but displaying information about bipolar pairs.

'num_pairs': Number of pairs per session.


'events': Information about the word epochs that were presented to the subject.

'recalls': Arrays denoting which epochs were subsequently recalled (1 = recalled, 0 = not recalled)

'rec': Indices of recalled epochs within 'recalls' arrays

'not_rec': Indices of not-recalled epochs within 'recals' arrays

'lists': Array that denotes the number of epoch lists a session had. A full session would have 25 lists.

'num_lists': Number of lists per session.

'word_lists': Array that is the same size as 'recalls' for that session that denotes the word-to-list correspondance.

'num_words_sess': Number of words per session.


'exps': What experiment ('FR1' or 'catFR1') each indice refers to.

'sessions': Number of session within an experiment (0 being the first session). For example, if 'sessions' output is [0, 0, 1], then the subject may have one subject of 'FR1' and two of 'catFR1'. The output of 'exps' would be ['FR1', 'catFR1', 'catFR1']


'powers_car_uni': Log-transformed power output from morlet wavelet convolution for common-average rereferenced data for the univariate analyses. Shape is $num_words$ X ($num_channels$ X8) since there are eight frequency bins. The *Nth* 8 row elements represent the 8 powers for the *Nth* channel.

You can also use 'pairs' instead of 'car' to denote bipolar data, and 'multi' instead of 'uni' to denote the frequencies used for multivaraite analyses.

'stds_car'/'kurs_car'/'stds_pairs'/'kurs_pairs': standard deviation or kurtosis data for the common-average or bipolar data. Shape is $num_epochs$ X $num_channels$. Each (i, j) element represents the standard deviation or kurtosis of the ith epoch in the jth channel.
