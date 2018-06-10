<a name="Title"></a>
# Walkthrough - Building an Image Classifier of State Licenses using Microsoft Cognitive Services Custom Vision

![Cognitive Services UI Demo](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/CognitiveServicesImage.png)

<a name="Overview"></a>
## Overview ##
Microsoft Cognitive Services **Custom Vision** allows non-professional data scientists build custom cognitive classifiers using adaptive learning.  All that is required is good knowledge of your domain data!

This walkthrough demonstrates howto build an image classifier (classification model) using Microsoft Cognitive Services.  This walkthrough includes step by step instructions using the Custom Vision portal; requiring zero code.

<a name="Objectives"></a>
## Objectives ##

- Create a Custom Vision Project for Image Classification
- Add custom training data: custom images of 5 different state licenses: California, Illinois, New Jersey, New York & Texas
- Build an image classifier using adaptive learning
- Evaluate the Performance of the image classifier
- Provide steps on howto consume the built image classifier
- Next Steps

<a name="Prerequisites"></a>
## Prerequisites ##

- An internet connection & a browser
- Download the training & validation image set from this repository
- An Azure subscription is **NOT REQUIRED**, we will use the FREE trial SKU

<a name="Intended Audience"></a>
## Intended Audience ##

This lab is intended for aspiring AI professionals that would like to learn more about the Microsoft Cognitive Services Custom Vision service functionality.

### Task 1: Creating a Custom Vision Project & Adding Training Data ###

1. Download the **Drivers Licenses training & validation Images** that are located in there DriversLicenesImages in this repository: https://github.com/bartczernicki/ImageClassificationStateLicenses/tree/master/DriversLicensesImages

1. Navigate to the Custom Vision portal **https://customvision.ai**.  Select the **Sign In** button to log in with any Microsoft account (older name: Microsoft Live account).  If prompted, Agree to any terms of service.

1. Select the **New Project** buttom (image shown below)
![Custom Vision - New Project](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-NewProject.png)
