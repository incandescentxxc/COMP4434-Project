# Introduction
Rating prediction is an important feature that PolyTube should have. Since the rating is a number out of 10, this problem can be viewed as a regression problem. In order to treat a regression problem, several methods can be done- simple multi-variate linear regression, decission tree method, support vector machine, and neural networks. Each of the method may require different treatment of feature enigeering. To start, this project would adopt a linear regression method, with other more advanced methods presented later. This report will start with the feature enigneering work in prepartion for linear regression. Then we construct the dataset into a train set and a test set. Then we will implement the model using existing sklearn library. An analysis of this model will be added afterwords. In the end, future work about using other methods will be discussed.

# Feature Enigneering
This part introduces some pre-processing techinics we use to pre-process the data. I will explain the pre-processing procedures for each of data columns.
- teleplay_id and name:
    They are used to identify a particular data row, which take no influence in our model. I simply drop the two columns.
- type:
    Though in the documentation of the project, a record has type either "short", "medium", or "long". My investigation of the original data shows that there are in total six kinds, which are "short", "medium", "long", "Music", "Special", and "ONA". Moreover, there are data which do not possess a type. 
    
    Obviously, they are categorical data. To handle this, I introduce the dummy encoding method. That is, I add six more columns named as the corresponding labels. If this record orginally has a type of any kind of the above, the corresponding dummy variable will be marked as 1, and the rest of them will be 0. In this way, we transform the type column into six parllel columns. For a record which is missing any type, all of the dummy variables will be 0.
- episodes:
    This is a numerical-type data, which possess direct realistic meaning. There are two options of the handling of this column. Either we treat it as a normal numberical data, or we transform it into a categorical data based on an interval method. The justification of transforming it into a categorical data includes two points.
    1. Episodes are not strictly continous. Say, there are some numbers which rarely appear because it does not make much sense of having such a number of episodes. 
    2. Different number of episodes can be mapped into a realistic setting in daily life. For example, a less-than-3 episodes of a series may be regarded as a short series. A more-than 24 episodes series may be seen as long series. The transformation can entitle this column with more realistic meaning, masking the unimportant details of the number.
    However, before the deadline of mid-term report, I still used the first method to handle this column. However, handling of the missing data is still needed. There are some records which show an unknown label in episodes. In this case, I simply drop them because there are only less than 2% (228) such rows. 
- rating:
    This corresponds to y in the final model. However, there are some rows having this attribute missing. I drop them because this column is critical for testing.
- members:
    This is a continuous numerical data. I drop the row if this value is missing. 
- genre:
    This an important categorical data. A record may possess one or more genres. To handle this, I also adopt the dummy encoding approach. A list of columns are added, which are corresponding to the genres. If some row has genre to be empty, then all of the corresponding dummy variables are set to be 0.


# Train set & Test set

# Models

# Prelimary results

# Future work