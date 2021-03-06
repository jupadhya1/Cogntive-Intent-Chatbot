# Goal-Oriented Chatbot trained with Deep Reinforcement Learning


## Details

This shows how to train a simple DQN agent with deep reinforcement learning as a goal-oriented chatbot using a simple user simulator. The code is a simplified version of TC-Bot by MiuLab with the main difference being that this code does not include NLG or NLU components but just trains the dialogue manager. NL components are not necessary to understand how a GO chatbot is trained with DRL and therefore are not implemented.

Here is a diagram from the paper for TC-Bot, and is similar to the flow of dialogue used in this project other than the LU and NLG components:


In addition to removing NL, there are changes to the success conditions, the DQN agent optimizer and a few other minor changes. Therefore, accuracy should not be compared directly between TC-Bot and this repo. 




## Dependencies
- Python >= 3.5
- Keras >= 2.24 (Earlier versions probably work)
- numpy

## How to Run
You can train an agent from scratch with ```python train.py```. 

In constants.json you can change hyperparameters including "save_weights_file_path" and "load_weights_file_path" (both relative paths) to save and load weights respectively. For example, to use the pretrained weights in the weights folder, set the value of  "load_weights_file_path" to "weights/model.h5". Weights for both target (tar) and behavior (beh) keras models are saved every time the current success rate is at a new high. 

You can also test an agent with ```python test.py```. But make sure to load weights by setting "load_weights_file_path" in constants.json to a relative path with both behavior and target weights. 

All the constants are pretty self explanatory other than "vanilla" under agent which means DQN (true) or Double DQN (false). Defualt is vanilla DQN. 


## Test (or Train) with an Actual User
You can test the agent by inputing your own actions as the user (instead of using a user sim) by setting "usersim" under run in constants.json to false. You input an action and a success indicator every step of an episode/conversation in console. The format for the action input is: intent/inform slots/request slots.

In addition the console will ask for an indicator on whether the agent succeeded yet (other than after the initial action input of an episode). Allowed inputs are -1 for loss, 0 for no outcome yet, 1 for success. 

## My Data
Used hyperparameters from constants.json.

Table of episodes (every 2000 out of 40000) by max success rate of a period/train frequency (every 100 episodes) up to that episode:


