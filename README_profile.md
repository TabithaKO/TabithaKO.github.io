### Hi, I'm Tabby 👋


- 🔭 I'm a computer science PhD student at Brown University advised by Professor Nora Ayanian
- 👯 I'm looking to collaborate on vision & robotics projects
- 📫 How to reach me: tabitha[underscore]oanda[at]brown[dot]edu
- My computer vision [blog articles](https://blog.paperspace.com/author/tabby/)
- My [CV](https://github.com/TabithaKO/docs/blob/main/Tabitha_Oanda_CV_PhD%20(7).pdf)



## Computer Vision Projects
### [gans_blazing](https://github.com/TabithaKO/gans_blazing) 🔥 🔥
This is an extended project where I use face analysis models and GANs to highlight the possible uses of AI in the fashion and beauty industry. I create notebooks that are easy to use for landmark detection, pose estimation, face reenactment, style transfer, and image inpainting.


https://user-images.githubusercontent.com/50864401/184269056-e84ed259-c01f-4c60-ac9d-f90e1bd191f2.MP4


### [Custom Face AutoEncoder](https://github.com/TabithaKO/Autoencoders)
I trained 4 autoencoders for face images belonging to these groups: Black Women, Black Men, White Women, White Men. The goal of this project was to use autoencoders to compress the image data in order for me to analyze the distribution of the images using simpler models like KNN and logistic regression.

### [Hairstyle Detector App](https://github.com/TabithaKO/hair-detector)

This is a hairstyle detection model that was trained on images of Black women with a wide variety of hairstyles.
I created a CreateML model that I added to an iOS app that I created and installed on my phone.
The app allowed me to access photos from my gallery and correctly classify the hairstyle on the individual in the image.

### [Hand Pose Prediction](https://github.com/TabithaKO/CS585-HW2)
My team and I used traditional computer vision techniques such as template matching to identify 5 distinct hand poses and draw a bounding box around the hand.
In this project my partner and I utilized skin color detection and OpenCVs template matching algorithm to complete this task.


### [Kalman Filter Multiple Object Tracking](https://github.com/TabithaKO/MultipleObjectTracking)
I worked with two classmates to design an algorithm that we used to track and estimate the trajectories of multiple objects (flying bats) in a frame of a video.
By applying the algorithm on multiple frames we were able to track the trajectories across an entire video.

### [Custom Object Detector YOLO V3](https://github.com/TabithaKO/signs-YOLO)
I scraped a custom dataset from a search engine and trained the YOLO V3 network on my images. The goal was to create a custom traffic sign detection model for my robotic car project



## Robotics Projects
### [Robotic Arm](https://github.com/TabithaKO/Cerebella)
I assembled a robotic arm using servos and servo brackets available on Amazon.
I used an Arduino to control the servos and a Raspberry Pi to send signals to the Arduino based on a pose detection model.
The pose detection model I used was OpenPose. I translated the pose detection predictions from the model into actionable servo signals to control the robotic arm.



### [Soft Robotic Hand](https://github.com/TabithaKO/SoftRobot)
I designed a robotic hand using Shapr3D (CAD software) and a standard 3D printer.
I designed some soft robotic muscles using silicone and some Arduino contolled air pumps.
I combined the soft robotic muscles and the hand to create an actuated robotic hand.


### [Self Driving Toy Car](https://github.com/TabithaKO/CarProject)
In this project I assembled a robotic car kit and attached a Raspberry Pi camera at the head of the car.
I trained an object detection model based on common household items. I wrote a python program to control the car based on the object detected in its path.
This project inspired the most recent version of the [Data Science in Action summer camp](https://www.hsph.harvard.edu/biostatistics/machine-learning-for-self-driving-cars/).



## Research (Internships)
###  Summer 2022 : NERF Robustness, Microsoft Research
I design and perform experiments to evaluate the robustness of NERFs under different training and testing conditions.

###  Summer 2021 - May 2022 : UniFace, Bargal Lab, Boston University
I trained a style transfer GAN using the StarGAN_V2 architecture. I trained the model on a custom dataset that comprised of faces of Black celebrities.
The premise of this project was to train a cross domain style transfer model which can perform better on Black faces because this demographic was underrepresented in the original data. I eventually wound up training the model to perfrom style transfer across 3 race groups (White, Black, Asian) and 2 gender groups (Male, Female). The groups and genders were determined by the FairFace and UTKFace projects.
This project is still ongoing hence the repository and data are still private until publication. However, here's a [notebook](https://github.com/TabithaKO/docs/blob/main/paperspace_stargan%20(2).ipynb) highlighitng sharable aspects of the project, here's a [video demo](https://drive.google.com/file/d/1maN0SwKNM_VSipfrW2Irdrx3ojYmgSmO/view?usp=sharing) of the image generation process from our custom trained model, and here's a link to the [StarGAN_V2 paper](https://arxiv.org/abs/1912.01865)

https://user-images.githubusercontent.com/50864401/184266588-c692ab97-bc6f-428c-9946-d1c5e6e3543f.MP4[400x200]

### Summer 2020 : Pose Estimation, Economo Lab, Boston University
In this project I worked with Professor Economo to collect pose estimates of rodents in the lab using computer vision models DeepLabCut (DLC) and Animal Part Tracker (APT). We later used this pose measurements to prefict future position of the rodent using a timeseries model. More details about the project are [here](https://tabithako.github.io/UROP_Summer2020/).


### Fall 2020 : Disease Diagnosis, Cai Lab, Harvard University
In this project I trained machine learning models to classify patient records as indicators of certain diseases: Lung Cancer, Arthritis and Coronary Atery Disease. I cleaned and processed the training data by writing code to convert keywords in the sample files to CUIs based on the CUI dictionary provided by MIMIC library. The data came from deidentified patient records, Wikiperdia, MedScape and Uptodate websites.

### Fall 2019 : Food Classification, Betke Lab, Boston University
In this proejct I worked as an undergraduate intern at the Betke lab under Mona Jalal (PhD). During this time I replicated experiements that had been performed in a previous version of the project that had [been published](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=tTXTO0oAAAAJ&citation_for_view=tTXTO0oAAAAJ:eQOLeE2rZwMC). The experiements involved trainining classifiers on Kenyan food images that had been scrapped off of Instagram.

## Guest Talks
- Summer 2021,2022: Guest Lecture: Boston University Deep Learning Course (CS 523)
- Spring 2021: Computer Vision Workshop: Code For Africa
- Spring 2021: [Arduino Day](https://www.youtube.com/watch?v=k0HQ776d4Kk&t=6660s): Featured Community Member
- Summer 2020: Undergraduate Research Opportunities Program Symposium
- Summer 2020: Nairobi Women in Machine Learning and Data Science

## News
- Boston University Undergraduate Research Opportunities [Feature](https://www.bu.edu/urop/achievements/student-spotlight/featured-researcher-tabitha-oanda/)
- Shaping Women in STEM Africa [Feature](https://stemwomenafrica.medium.com/stem-woman-crush-tabitha-oanda-64b2aca46ed6)
- Spell ML [Feature Video](https://www.facebook.com/spelldeeplearning/videos/via-tabitha-oandathis-weekend-i-decided-to-do-some-aerial-practice-on-the-sling-/681506712452484/)
