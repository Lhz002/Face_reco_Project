# Real-time face recognition project report

## Introduction

This project is a real-time face recognition system developed by python language and based on OpenCV and DNN network models. Our system has achieved the functions of registration of face feature vector, data preservation and deletion modification, face annotation, simple graphical interactive interface. The goal of matching the faces in the database with those obtained from the camera is completed. The specific program running logic is shown in the figure below.

![图示  描述已自动生成](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image002.png)

 

 

## Load model

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png)

The program model loading in accordance with the operation method of the given file operation. The database file was a *.csv* file and the threshold score was set to 0.3.

## Register part

## Data registration

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png)

Start by creating a *.csv* file reader. Create a *user_buffer* and *feature_buffer* to store feature vectors and corresponding names in *.csv* files. Next, create the registration function. Face recognition and feature vector extraction were carried out through function *detector* and *recognize*r of model, respectively. Then the feature vector is converted into 1*128 format for easy reading. And then convert it to a list format. When the *user_buffer* is empty or the name does not exist in the *user_buffer*, the name information and feature vector are added to the corresponding buffer. If it already exists, the information in the database is updated to remove the old information. Finally, display the “Finished Registration”.

## Data deletion

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)

Define the delete function. When this function is called, if the *user_name* entered is not in the *user_buffer*, the message “Warning: NO SUCH USER” will be printed. If the user exists, the *Index* function is used to search for the user's information in buffer and delete the corresponding information about the user.

## Data update

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png)

At the end of each system, data in *user_buffer* and *fearture_buffer* will be written into the.csv file for data update.

 

## Recognition part

## Face matching

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png)

When defining the recognition function, *max_score* and *match_user* are first initialized. Then the detector function in the model is called to identify the faces in the video. If the face cannot be captured, a value of None is returned. After that, the features of the first face captured are extracted. When there are already registered features in *fearture_buffer*, the feature vectors in the buffer are converted to float32 and then the match function in the *recognizer* function of model is called to score the differences between the two vectors. If the score is greater than the set threshold score and is the largest among all the scores that meet the conditions. It prints the matching *user_name* and calls the *draw_face_rectangles* function to mark the face. If no match is found, "UnMaich!!!" is displayed.

## Face Marking

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)

Obtain the coordinates of the recognized face and determine the size of the rectangle according to the diagonal points. Sets the color and line thickness of the rectangle. After setting the font and position of the display. Call a function in OpenCV to display.

## Graphical interactive interface

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image016.png)

The *numpy* library and the *cv2* library are called to draw two blank images of the same size as the identified video frame. Draw two buttons with rectangles on each blank picture and fill them. The buttons are "Regist" and "Delete" respectively. Finally, the *addWeighted* function in *cv2* is called with the original graph overlay.

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image018.png)

Finally define the mouse position detection function. Returns the location of the mouse.

## Execution part

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image020.png)

First initializes the point of the mouse callback, initializing the decision for both buttons. The face instance is then created, and the input string is initialized. In the loop, determine the mouse position and update the status of the button when the mouse is clicked at the button position. When the ESC key is pressed on the keyboard, exit the program and update the database.

![img](file:///C:/Users/14620/AppData/Local/Temp/msohtmlclip1/01/clip_image022.png)

When the button is clicked, the character entered on the keyboard is recognized. According to the function performed by the corresponding button, the face information recognized in the video frame can be registered or deleted. When the button function is not executed, the faces identified in the display video frame are marked.

## Reference

1. https://github.com/fengyuentau/WSB2022-assignment.

 