# DQN

This repository contains an exploration of solutions to the udacity banana problem.

# Banana brain

### Basic description of the game

Agent must navigate to collect bananas in a large, square world.  

![Alt Text](DQN.gif)

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.  

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

# Setup

Step 1: Clone the Course Repository
Follow the instructions in the course [GitHub repository](http://[example.com](https://github.com/udacity/Value-based-methods#dependencies)) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project. 

(For Windows users) The ML-Agents toolkit supports Windows 10. While it might be possible to run the ML-Agents toolkit using other versions of Windows, it has not been tested on other versions. Furthermore, the ML-Agents toolkit has not been tested on a Windows VM such as Bootcamp or Parallels.

Step 2: Download the Unity Environment
For this project, you will not need to install Unity - this is because we have already built the environment for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:

Linux: [click here]([opens in a new tab](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip))
Mac OSX: click [here]([opens in a new tab](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip))
Windows (32-bit): [click here]([opens in a new tab](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip))
Windows (64-bit): [click here]([opens in a new tab](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip))
Then, place the file in the p1_navigation/ folder in the course GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out this [link]([opens in a new tab](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64)) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not [enabled a virtual screen]([opens in a new tab](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md))), then please use this [link]([opens in a new tab](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip)) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should [follow the instructions to enable a virtual screen]([opens in a new tab](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), and then download the environment for the Linux operating system above.)

# Copy files

Copy file:

* Navigation.ipynb
  *   This notebook contains the training loop.
  *   Relevant hyperparameters that can be found here are:
      1) Number of training episodes, n_episodes
      2) Maximum number of steps per simulation,
      3) Epsilon start value (for epsilon greedy), eps_start
      4) Mininmum epsiolon value (for epsilon greedy), eps_end
      5) Epsilon decay rate (for epsilon greedy), eps_decay
* Model.py
  *   Basic torch NN with 2 hidden linear layers with ReLu activation function and one linear output function without activation fuction
  *   input size is based on the state space of the banana environment.
  *   output size is based on the action space of the banana environment.
  * Relevant parameters:
    1) number of weights in first layer, fc1_units
    2) number of weights in second layer, fc2_units
* dqn_agentu.py
  *   Contains the reinforcement class Agent and the replay buffer class ReplayBuffer
  *   Relevant hyperparameters to be found here are:
     1) BUFFER_SIZE, size of the replay buffer
     2) BATCH_SIZE, the sample batch size used to update the NN
     3) GAMMA, the discount factor for how much to take next state Q value into account
     4) TAU, for soft updating the target network, [0..1], higher values update more from the local network parameters, relative to the existing target parameters
     5) LR, learning rate for the NN
     6) UPDATE_EVERY, frequency in units of episodes for updating the target network
 * checkpoint.pth
    * the trained model weights from the described network parameters in report.pdf
