# Self-Driving-Car
A Reinforcement Learning algorithm that drives a self driving car.

## Problem Description
This Reinforcement Learning algorithm drives from the top left of the screen to the bottom right and will go the other direction once it has reached the corner. It will keep driving from the top left to the bottom right, then from the bottom right to the top left and repeat. These points will be refered to as the car's objective.

You can draw "sand" on the screen and the algorithm will try to avoid that sand (it receives a negative reward).

## Inputs to the Deep Q Network
This algorithm utilizes Deep Q-Learning with 5 inputs. The first 3 inputs come from 3 sensors on the front, left, and right of the car which returns the number of sand blocks around them. The last 2 inputs return the orientation of the car, a value from -1 to 1 which represents a value between -180 to 180 degrees corresponding to objective.

## Rewards
The algorithm gets a small reward for heading towards the object and a small negative reward for heading away. These values are set to 0.1 and -0.1. These values were left small so that the car would have the freedom to drive in the opposite direction a bit in order to avoid sand without being heavily penalized. In contrast, the car receives a -5 reward if it drives over sand. Furthermore, the car receives a -1 reward if it goes to close to the sides of the map. Finally, a variable/scaled reward is received each time the algorithm reaches it's objective which is defined by previous_steps - current_steps. This additional reward will ensure that the algorithm gets penalized for taking a longer route than the previous run and that it will be rewarded if it takes a shorter route. This reward scales corresponding to high much longer/shorter the current route is compared to the previous route.

## Download
Feel free to download the code and run it on your machine. Simply run the map.py file. I have included a saved model and optimizer which you can load by simply clicking the load button after running map.py. You may want to adjust some parameters depending on how you want your car to move. I've trained this car to zig zag up and down the map about 4 times with obstacles along the way. I did this by drawing sand to block it's direct path like walls and adding random circles of sand in the pathway to make the environment more complex. In order to achieve this, I've set the reward for driving on sand pretty high and I set driving away from the objective relatively low. Furthermore, I've set a temperature of 10 which basically defines how confident you want your algorithm to be. Basically, the algorithm will determine it's next action probabilistically (yes it's using softmax). Setting a higher temperature will make the algorithm more confident in the action with the highest probability and the opposite is true. Basically higher temperature leads to less exploration and vice versa. The rewards are defined in the map.py file and the temperature in the aii.py file, all variables have been commented.
