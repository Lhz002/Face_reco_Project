# Real-time face recognition project report

## Introduction

This project is a real-time face recognition system developed by python language and based on OpenCV and DNN network models. Our system has achieved the functions of registration of face feature vector, data preservation and deletion modification, face annotation, simple graphical interactive interface. The goal of matching the faces in the database with those obtained from the camera is completed. The specific program running logic is shown in the figure below.


![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/ff8e00ee-13b7-4821-a700-b8a9035bd22c)

 

 

## Load model

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/ac99e1f4-0266-41d8-a1b5-801a29cb561d)


The program model loading in accordance with the operation method of the given file operation. The database file was a *.csv* file and the threshold score was set to 0.3.

## Register part

## Data registration

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/5e648afd-c589-41eb-9627-d39673c1bb02)


Start by creating a *.csv* file reader. Create a *user_buffer* and *feature_buffer* to store feature vectors and corresponding names in *.csv* files. Next, create the registration function. Face recognition and feature vector extraction were carried out through function *detector* and *recognize*r of model, respectively. Then the feature vector is converted into 1*128 format for easy reading. And then convert it to a list format. When the *user_buffer* is empty or the name does not exist in the *user_buffer*, the name information and feature vector are added to the corresponding buffer. If it already exists, the information in the database is updated to remove the old information. Finally, display the “Finished Registration”.

## Data deletion

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/9b0944ee-61fe-4823-b7ff-3572e8ea4d9e)

Define the delete function. When this function is called, if the *user_name* entered is not in the *user_buffer*, the message “Warning: NO SUCH USER” will be printed. If the user exists, the *Index* function is used to search for the user's information in buffer and delete the corresponding information about the user.

## Data update



At the end of each system, data in *user_buffer* and *fearture_buffer* will be written into the.csv file for data update.

 ![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/570d3bf1-001c-47d8-bb08-9d85a8cba46e)


## Recognition part

## Face matching

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/615f3a32-2a43-4ec4-a986-761070f00b83)


When defining the recognition function, *max_score* and *match_user* are first initialized. Then the detector function in the model is called to identify the faces in the video. If the face cannot be captured, a value of None is returned. After that, the features of the first face captured are extracted. When there are already registered features in *fearture_buffer*, the feature vectors in the buffer are converted to float32 and then the match function in the *recognizer* function of model is called to score the differences between the two vectors. If the score is greater than the set threshold score and is the largest among all the scores that meet the conditions. It prints the matching *user_name* and calls the *draw_face_rectangles* function to mark the face. If no match is found, "UnMaich!!!" is displayed.

## Face Marking
![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/5411f3ef-a448-41cd-94ea-5bb1be6d1122)



Obtain the coordinates of the recognized face and determine the size of the rectangle according to the diagonal points. Sets the color and line thickness of the rectangle. After setting the font and position of the display. Call a function in OpenCV to display.

## Graphical interactive interface
![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/e7de29ae-87d4-406a-bb23-5f5a9ca6fdba)



The *numpy* library and the *cv2* library are called to draw two blank images of the same size as the identified video frame. Draw two buttons with rectangles on each blank picture and fill them. The buttons are "Regist" and "Delete" respectively. Finally, the *addWeighted* function in *cv2* is called with the original graph overlay.

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/5dcf787c-1f7b-4e86-a9a0-cbb343b1d76b)


Finally define the mouse position detection function. Returns the location of the mouse.

## Execution part

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/61034a2c-7763-42c8-abb3-6f62630ad7b9)


First initializes the point of the mouse callback, initializing the decision for both buttons. The face instance is then created, and the input string is initialized. In the loop, determine the mouse position and update the status of the button when the mouse is clicked at the button position. When the ESC key is pressed on the keyboard, exit the program and update the database.

![image](https://github.com/Lhz002/Face_reco_Project/assets/139037029/596719b5-2b90-4162-9739-2ae545b27e7e)


When the button is clicked, the character entered on the keyboard is recognized. According to the function performed by the corresponding button, the face information recognized in the video frame can be registered or deleted. When the button function is not executed, the faces identified in the display video frame are marked.

## Reference

1. https://github.com/fengyuentau/WSB2022-assignment.

 
