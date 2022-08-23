# Flatiron_phase5cap


# Gun-Image-Classification

<p align="center">
  <img src = "https://www.rd.com/wp-content/uploads/2021/04/GettyImages-861879906-MLedit-1.jpg" width="500" height="320">
</p> 

## Business Understanding

Unfortunately, we often see news reports of acts of violence involving guns in the United States. While it is difficult to identify potentially dangerous individuals from committing such crimes, there is the thought that these mass shootings we see on the news could have been prevented. 

For instance, there has been evidence after the fact, that these dangerous individuals have exhibited violent behavior through online social media platforms <a href="https://www.theguardian.com/us-news/2022/may/28/texas-gunman-threats-behavior">(The Guardian)</a>. 

There have even been <a href="https://www.cityandstateny.com/policy/2022/05/hochul-proposes-new-gun-laws-social-media-crackdowns-after-mass-shooting/367113/">recent legislative efforts</a> in New York State following the mass shooting in Buffalo on May 2022 establishing Domestic Terrorism Units tasked with tracking down people looking to commit acts of violence. 

With these preventative efforts in mind, we will explore whether image recognition technology has the ability to distinguish between images of guns and not guns. 

**Stakeholders**: New York State Domestic Terrorism Unit

Is there a way to detect potentially dangerous individuals by image recognition of guns? 

- Where is gun violence in America most prevalent? 
- Has there been an increase in gun violence? Are there trends we are seeing over time? 

*For further exploration into these questions, please see the exploratory data analysis (EDA) notebook.*

**Data Sources:** 
- <a href ="https://wonder.cdc.gov/ucd-icd10.html">Center for Disease, Control, and Prevention</a>

**Image Data:** 
- <a href="https://dasci.es/transferencia/open-data/24705/">Andalusian Research Institute in Data Science and Computational Intelligence (DaSCI)</a>
- <a href="https://www.kaggle.com/datasets/ahmadahmadzada/images2000"> Kaggle </a>

The dataset consisted of 65% of various gun types including handguns and rifles. The remaining 35% consisted of other hand-held objects such as knives, phones, bats, and money. In other words, the data was classified as follows: 0 for "not gun" and 1 for "gun".

<img width="1140" alt="sample images label" src="https://user-images.githubusercontent.com/86889081/183101690-b87b1a66-24a2-455a-97c7-ca472bbde79b.png">


*Note: Supplementary to this project, please see the 'Image Classification - Multiclass' notebook for a multi-class image classification of various images other than just guns and not guns.*

**The Task:** 
    
Perform an analysis on gun violence in the United States and create a machine learning model that can classify images of guns and not guns. The intention is to proactively detect potentially dangerous individuals on social media and for authorities to respond appropriately.
    
For reference, this project implements Keras library. Keras is one of the leading high-level neural networks APIs and does a great job in the classification of images.

## Data Processing:
    
To prepare the images for modeling, the images in each data set were reshaped, normalized, and selected for modeling into the training, validation, and test sets. All 3 steps are accounted for using the `ImageDataGenerator` package from Keras. 
    
3,000 images were used in the training set, the next 1,000 images were used in the validation set, and the remaining 1,000 images were used in the test set.
    
## Modeling:
    
The primary metric for assessing model performance was accuracy (classification of guns and not guns). However, we also considered the recall score (ratio of # of true positives of guns to the total image class of gun images) since the context of false negative images far outweigh the significance of accuracy for the purposes of this business problem. 
    
The modeling process consisted of an iterative approach of attempting to build upon the previous best model. Training set images were fit into each respective model with validation performed to gauge performance on the testing data. A baseline model consisting of a simple dense neural network was instantiated as a benchmark. 
    
Building off the baseline model, a number of different architectural modeling decisions were implemented and described more fully in this notebook. In general, we implemented different optimizers, introduced new layers, dropped layers, added max pooling layers, and dropout layers. 

## Evaluation

**Model Performance:**

We found that through the modeling process, even our best performing machine learning model performs exceptionally well when it comes to classification of gun and not gun images. 

Specifically, we determined that our best model, the CNN- V6 had a 88% accuracy and a 96% recall. As discussed, there is a trade-off when it comes to improving upon accuracy and recall. As one metric increases, the other effectively decreases and a balance must be found between the two. 

<p align="center"> <img width="365" alt="accuracy and loss" src="https://user-images.githubusercontent.com/86889081/183102178-6798735a-e10a-48a5-a344-566b4caec3bf.png"></p> 

Ultimately, the model that strikes the best balance was the CNN-V6 model. 

<p align="center"> <img width="336" alt="confmatrix" src="https://user-images.githubusercontent.com/86889081/183102209-e2a25056-f9b9-4c2f-867b-4ecd2cc364c7.png"></p> 



**Model Value & Limitations:**

While we were able to effectively prove that machine learning CNN models can perform exceptionally well at distinguishing between images of guns and not guns, there are still difficulties in implementing this technology at a larger scale. 

For example, there are data privacy and ethical concerns related to the usage of images on social media platforms such as Instagram or Facebook. Further it is important to note that even if an image is classified as a gun, there needs to be evidence to suggest that the social media post is inherently violent in nature. There is potential to explore whether a social media post is violent with other machine learning techniques such as using natural language processing (NLP). 

**Recommendations & Next Steps:**

- Secure partnerships with social media platforms such as Instagram and Facebook to garner implementation at a larger scale. Discuss the ethical situations surrounding data usage and privacy. 


- Secure more data related to social media posts. Posts with guns alone are not necessarily violent in nature. Explore NLP for texts associated with images of guns flagging potentially dangerous individuals. 


- Expand to the public sector (ie. security systems and cameras). Potential for privacy issues in public. However, recognition of guns in public can trigger faster response times to active shooter situations. 


## Repository Structure

```
├── images_presentation
├── pdfs
├── .gitignore
├── EDA.ipynb
├── Image Classification - Binary.ipynb
└── Image Classification - Multiclass.ipynb
└── README.md
```




