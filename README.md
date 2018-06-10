<a name="Title"></a>
# Walkthrough - Building an Image Classifier of State Licenses using Microsoft Cognitive Services Custom Vision

![Cognitive Services UI Demo](https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-WalkthroughCognitiveServices.png)

<a name="Overview"></a>
## Overview ##
**Microsoft Cognitive Services Custom Vision** allows non-professional data scientists build custom cognitive classifiers using adaptive learning.  All that is required is good knowledge of your domain data, since all the work is done in the browser!

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

### Task 1: Creating a Custom Vision Project & Adding Training Image Data ###

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

11. After you have uploaded all of your images and tagged (labeled) them, you should notice on the left-hand side a summary of the image assets that are contained in the Custom Vision service.  Before proceeding to the next task of building the classifier, ensure that all of the 5 different license types are present.  Your project summary pane should look similar to the screenshot below.
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-AddImages-AllTagged.png">
</p>



### Task 2: Building an Image Classifier, Evaluating Performance & Making New Predictions ###

1. You are ready to build a image classifier.  To build the first model, simply click the green **Train** button highlighted in the screenshot below. In the Custom Vision service it is that easy!
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-Train.png">
</p>

2. The Cusom Vision service has begun training an image classifier.  You will be shown a screen that highlights the progress.  After a few minutes, a web screen will display the **performance characteristics** of the built classifier in both summary (overall model performance) and for each different type of license.  These metrics can help you quickly baseline the quality of your classifier.  The screenshot below shows the performance metrics UI:
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-PostTrain.png">
</p>

3. The **Precision** metric states the likelyhood of the predicition being correct.  The **Recall** metric states likelyhood of correctly tagging an actual drivers license tag.  For example, if our classifier is able to correctly predict an actual New York tag with a high degree of certainty (probability) then that would improve the **Recall** number.  If this is your first time building a classifier, you may think these numbers are low.  There are several ways we can improve this:
- You have only uploaded a small amount of images.  Custom Vision (at a minimum) requires 15 images of each type.  For example, you only have 9 images for Texas.
- Notice the **Probability Threshold** on the top left.  This is a default decision boundary of selecting an actual prediction for the Precision/Recall metric calculations.  This is set to 50%.  In order to count positively towards the Precision & Recall metrics, the classifier needs to be at least 50% "certain" that an image is going to be labeled as such.  However, note we have 5 different state license types.  You could have a scenario where one image is predicted to be 44% likely to be one type and the other four types to be just 14% each.  Even though it is below 50%, the gap between 44% versus 14% is great enough that the likelyhood of the prediction is high.

> For more information on Precision & Recall, navigate to: https://en.wikipedia.org/wiki/Precision_and_recall

4. Now that you have baseline performance metrics, you can test the actual performance of the classifier by testing new images it has never seen before (images it was **NOT** trained with).  Click the **Predictions** tab on the top navigation menu.  Next select **Quick Test**.  Finally select the **Browse local files** button and select an image from the **Validation** folder.  Note: you can select any image, but it is important to select images from the Validation folder to ensure that the classifier has not seen this image before.  Screenshot below highlights the correct folder location.
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-Performance.png">
</p>

5. After the image is uploaded, it will be scored against the image classifier.  The classifier will return a list of predictions ordered by the highest probability scores first.  The higher the gap between the first and other items on the list, the better predictive power of the model.  Try a few different images from the **Validation** folder to see how the model is performing.  You should see results simlar to the screenshot below.
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-PerformanceNewYork.png">
</p>

6. Take a look at the screenshot above.  Notice the image above is clearly a New York State drivers license and the model never having seen this image before was able to allocate a 73% probability to the **NewYork** tag (label).  Pretty cool, right?  As a human it is easy for us to note that it is a New York State license, because the image clearly states this several times.   However, the model (image classifier) doesn't know it did a good job.  It is time to tell your model that it performed well and give it a pat on the back.  Secondarily, since our model has seen this new image; why not add it to the image assets and make our model smarter (improve predictive poewer) by retraining it with the updated image set.

7. Close any idividual side menus and select the **Predictions** tab in the main menu.  In that view, (assuming you completed Step 5 above) you should now see all of the images that your model "has scored" or "has made predictions on".  If you hover over each image, you will be displayed with a quick summary of the top tag predictions.  Note on the bottom right of each image there is a small **check box** button.  This allows you to select multiple images in bulk and tag them all at once.  This is super handy when your model (image classifier) is in production and you want to tag tens/hundreds of images at once to a single tag.  You can also select any individual image and this will bring you to a screen (shown below to enter the proper tag)
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-AddNewTags.png">
</p>

8. If you have completed the step above (Step 7), you now have new tagged (labeled) images.  This means the model (image classifier) can be made smarter by retraining with more images than you started with.  Simply by going through the process of adding new tags/labels, the training pool of images is automatically expanded.  **Click the (green) Train** button on the top menu and this will re-train the model with a new version (the Custom Vision service calls it Iteration).  After the model is built, notice that the performance characterstics of Precision/Recall are changed.  **Compare the iterations** by clicking the different iteration numbers; note that Recall/Precision change (hopefully they are going up).

> **Note:** Machine Learning & Data Science are iterative processes.  They demand constantly evolving with new examples of data to improve their predictive power.  As you can see, the **Custom Vision Service** facilitates this process directly in the UI by easily allowing you to tag new images and with a push of a Train button craft a new model.

9. Up to this point, you have seen how easily it is to test new images using the web UI.  However, what if you wanted to put this model into production and be able to deliver images for predictions automatically?  The Custom Vision service allows you to do this in two key different ways:
- an API using RESTful conventions is automatically created for you after training your first (and subsequent) models.  This API can be automated to make new predictions using any programming language that can "talk to" REST URIs.
- using the **Compact** model type, you can export the models into a self-contained serialized model file or a Docker container.  This allows you to deploy cognitive models "in process" close to your software logic or take a Docker container and host wherever Docker can run.  What this means is that you can take a classifier and consume it on **ANY** public cloud, hybrid or even on-premises envionment!  How cool is that?

10. For the **Prediction URL**, select the **Prediction URL** button that can be found under the **Performance** tab.  You can see required schema in order to craft a proper request to make a prediction.  (Screenshot shown below)
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-PredictionURL.png">
</p>

11. In order to **Export your model**, select the **Export** button that can be found under the Performance tab.  Selecting this button will bring up a right-hand menu for the type of export that can be done.  You can export model types that target: iOS devices, Andtroid devices, Windows/macOS/Linux servers and even Docker containers.  The Screenshot below displays the various export options.
<p align="center">
  <img src="https://github.com/bartczernicki/ImageClassificationStateLicenses/blob/master/WalkthroughImages/CustomVision-ExportCompactModel.png">
</p>

> **Note:** If the Export button is greyed out (or does not appear) you need to change to a Compact domain type.  This can be done using the Setting menu.  Use the gears menu item on the top tab to access this.

> **Note:** The ONNX format is an acronym for the **Open Neural Network Exchange** format.  It allows you to convert between various AI persisted formats.  This format is starting to become ubiquitous and faciliatates a standard method of persisting a neural network architecture.

<a name="Summary & Next Steps"></a>
## Summary & Next Steps ##

In this walkthrough lab you have learned howto build an image classifier easily using the Custom Vision Service and by adding  your own data.  There was zero code required and Microsoft provided a serverless (abstracted compute) architecture service in a web UI to be productive immediately.
