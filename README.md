<a name="Title"></a>
# Walkthrough - Building an Image Classifier of State Licenses using Microsoft Cognitive Services Custom Vision

![Cognitive Services UI Demo](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-WalkthroughCognitiveServices.png)

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

2. Navigate to the Custom Vision portal **https://customvision.ai**.  Select the **Sign In** button to log in with any Microsoft account (older name: Microsoft Live account).  If prompted, Agree to any terms of service.

3. Select the **New Project** buttom (Screenshot shown below)
<p align="center">
  <img width="163" height="217" src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-NewProject.png">
</p>

4. A properties pane will appear on the right-hands side.  Give the project a **Name** (i.e. DemoStateLicenses).  Enter a **Description** (i.e. Image Classification of State Licenses).  In **Project Type** ensure that "Classification" is selected.  In the **Domain** selection fields, select "General (compact)"

5. Select **Create Project** to create the new project.

6. You now have a new project created.  In order to get started building a classifier, you need to add some images.  Select the **Add Images** button from the center of the UI screen.  (Screenshot shown below with the button highlighted in red)

![Custom Vision - Add Images](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-AddImages.png)

7. A menu will appear on the right-hand side.  Select the **Browse local files** to add some images.  A file selection menu will appear.  Navigate to the local folder where you downloaded the training & validation images.  In the **Training folder** select the **New York** folder and then finally select all of the image files in that Training/NewYork folder (shown in the screenshot below).  Important Note:  **DO NOT** select images from the validation folder.

![Custom Vision - Add Images](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-AddImages-SelectedTraining.png)

8. The selected drivers licenses images will upload to the Custom Vision service.  You now need to let the service know what these images are.  In supervised Machine Learning poblems, this is called "labeling or tagging" of the data.  Since, all of the images we added belong to **NewYork** types of drivers licenses; simply enter **NewYork** under the **My Tags** field.  This will label all of the 19 drivers licenses images as NewYork. (Screenshot below)
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-AddImages-Tagged.png">
</p>

9. Select the **Upload 19 Images** button.  This will upload the images to the Custom Vision service with the provided tags.  Depending on your internet connection and location relative to the default Custom Vision service, this may take a couple minutes.  After all the images are uploaded, click the **Done** button to confirm the successful creation of the images & tags.

10. You have successfully uploaded & tagged (labeled) one set of drivers licenses images for NewYork.  However, in order to build a classifier that can distinguish between different types of drivers licenses; you need to provide examples of different drivers licens images.  **Repeat steps #7 - #9** for the remaing image types: **Illinois, NewJersey, California, Texas** using the respective files and tag name for each folder.  Select the **Add Images** button to repeat the image adding process.

11. 
11.  After 
