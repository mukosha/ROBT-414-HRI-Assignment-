# ROBT-414-HRI-Assignment-
ROBT 414 Programming Assignments.

# I have used the Jupyter Notebook (Python 3) for this assignment.
#The purpose of this assignment is to recognize the most common emotions by using the OpenPose body recognition. 
#For this task I have decided to pick the following three emotions to be recognizable by the program:
#1.- Happy; 2.- Surprised; 3.- Sad.


# Pose Detection. Use of the OpenPose. 

## Note: The program is going to register and time the body postures; Implement the counter for the time a user was in each state and the total number of moments of the emotions + garbage option.

The assignment was donw by using the openpose repository.


## Usage
The openpose model uses 25 points. For my assignment I have used much less points. Most of the emotional poses use only the upper body.


### Requirements
 * Anaconda: Jupyter Notebook (Python 3)

### Keypoints

All keypoints are indexed by part id.  The parts and their ids are:

![image](https://user-images.githubusercontent.com/47817099/134653106-ae9f4023-5a07-4b54-919c-8ba9e4b9b8f0.png)



## External Libraries
pd is the standard short name for referencing pandas:
This library will be used for data analysis: in this assignment it is used to analyze the .csv file

![image](https://user-images.githubusercontent.com/47817099/134653281-2117ad1d-c401-4ef4-a2c6-4eab03d064aa.png)

## Code:

The algorithm that runs through all the points throughout all the frames of the video:
```python
   for index, point in emotion_data.iterrows():
        
        #Sad state requirements:
        #14,23 are < than 11,20 -> i.e. palms of the hands are higher than elbows (closing face)
        sad = point[23] < point[20] and point[14] < point[11]
        
        #Happy state requirements:
        happy = point[11] < point[5] and point[14] < point[5] and point[20] < point[5] and point[23] < point[5] and point[14] < point[47] and point[23] < point[50]
        
        #Surprised state requirements:
        surprised = point[14] < point[11] and point[23] < point[20] and point[2] < point[11] and point[2] < point[23] and point[13] < point[10] and point[19] < point[22]
        
        
        
        if happy: 
            happy_state_counter += 1
            happy_state_timer += 1
            
        
        elif surprised:
            surprised_state_counter += 1
            surprised_state_timer += 1
        
        elif sad:  
            sad_state_counter += 1
            sad_state_timer += 1
            
        else:
            garbage_option_counter += 1
            garbage_option_timer += 1              
```

## Thank you for attention.
