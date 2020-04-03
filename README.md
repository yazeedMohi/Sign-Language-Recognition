# Sign-Language-Recognition
A simple and robust machine learning solution for the recognition of the different sign languages.

# General Description

**Set Histogram:** The first step is to select an appropriate histogram that all the images are to be filtered with, this gurantees that the resulting images are appropriately visible and distinguishable. The user runs the code below and places their hand inside the rectangle, then they press "C" on their keyboard until they find a good histogram, finally the user must press "S" to save the histogram for later usage.

**Create Gestures:** This portion essentially has two jobs: creating or reading from an SQL database file which contains all the registered gestures saved as tuples of (id, name/ text). The user is then asked to enter the id and the text of the new gesture, the camera is then started where an automatic gesture detection algorithm enables the program to take certain frames and save them as .jpg images in the user device storage for later training the model.

**Dipslay Gestures:** Displays all the gestures created so far as a grid image.

**Rotate Images:** Creates flipped instances of the saved gesture images, to augment the training set in the purpose of obtaining a larger training and validation sets for later.

**Load Images:** Reads the folder containing all the gesture images "/gestures" and compresses them into a pickle file for easier access when training the model, the file structure is "/gestures/-gesture_id-/-image_number_.jpg/", this structure helps by allowing the program to automatically figure out the lable associated with each image. The labels are then saved into their own pickle file. Data is seperated into training and validation sets according to some seperation factor.

**Recognition:** This portion is responsible for the actual testing of the model, it takes images from the camera, crops the, and then inputs them to the keras model, an evaluation is obtained for each frame, an evaluation is only considered viable if it has a probability higher than some threshold (70% in this code), once the same text has been predicted in a number of concurrent frames it is shown to the user in the input field for if they were to send it to someone else.
