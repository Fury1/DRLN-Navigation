[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

# Project 1: Navigation

## Project Details

### **Introduction**

This is the first project of the Udacity Deep Reinforcement Learning Nanodegree program. For this project, it was required to train an agent using a DQN to navigate and collect only yellow bananas in a large, square world.

![Trained Agent][image1]

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

### **State Space**

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.

Example State space:

*States have length: 37*

Example:

        [1.         0.         0.         0.         0.84408134 0.
        0.         1.         0.         0.0748472  0.         1.
        0.         0.         0.25755    1.         0.         0.
        0.         0.74177343 0.         1.         0.         0.
        0.25854847 0.         0.         1.         0.         0.09355672
        0.         1.         0.         0.         0.31969345 0.
        0.        ]

### **Action Space**

*Actions have length: 4*

Four discrete actions are available, corresponding to:

- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

### **Solved Environment Requirements**

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.

---

## Getting Started

1.  Download or clone this repo to a directory using `git clone https://github.com/Fury1/DRLN-Navigation.git`

2. To set up your python environment and run the code in this repository. Navigate to the cloned directory if you haven't already. Create (and activate) a new environment with Python 3.6. An Anaconda install is recommended.

        conda create -n drlnd python=3.6
- Linux or Mac:

        source activate drlnd
- Windows:

        activate drlnd
- Install environment packages:

        conda env create -f environment.yml

3. Follow the instructions in [this repository](https://github.com/openai/gym) to perform a minimal install of OpenAI gym within this project directory or using `pip`.

    - Next, install the classic control environment group by following the instructions [here](https://github.com/openai/gym#classic-control).
    - Then, install the box2d environment group by following the instructions [here](https://github.com/openai/gym#box2d)

4. Create an IPython kernel for the drl environment.

        python -m ipykernel install --user --name drlnd --display-name "drlnd"

Before running code in a notebook, change the kernel to match the ***drlnd*** environment by using the drop-down Kernel menu.

![Jupyter Kernel](https://user-images.githubusercontent.com/10624937/42386929-76f671f0-8106-11e8-9376-f17da2ae852e.png)

---

## How to Run

Open the `Navigation.ipynb` file using Jupyter. Ensure the Jupyter kernel is set to the ***drlnd*** environment that has been previously created above. Once the correct kernel is verified, run all code cells.

The notebook will start running output down to `4. It's your turn!`, then the kernel should stop and reset.

At this point you should have seen the Unity window launch and some random actions taken in the environment. In addition, there should be some output in the cells that will help you get familiar with the environment.

If everything worked as described you should be ready to start training an intelligent agent to solve the task at hand. Click on cell `4. It's your turn!`, and run all output BELOW. This will start training the network with the predefined parameters that ultimately solved the environment. If you are  not interested in training, feel free to view the saved output of the notebook.

A DQN network and agent has been predefined and set up to solve the task.

For those feeling ambitious, experiment with hyperparameters and see if you can improve the agent.

*Hyper parameters to adjust:*

        BUFFER_SIZE = int(1e5)  # replay buffer size
        BATCH_SIZE = 256        # minibatch size
        GAMMA = 0.99            # discount factor
        TAU = 1e-3              # for soft update of target parameters (blends networks slowly)
        LR = 1e-4               # learning rate (aka alpha)
        UPDATE_EVERY = 3        # how often to update the network
        n_episodes=1500         # total number of episodes to train for
        max_t=2000              # max number of time steps per episode
        eps_start=1.0           # epsilon starting value
        eps_end=0.01            # epsilon decay minimum value
        eps_decay=0.75          # epsilon decay rate

If you are feeling more ambitious feel free to experiment with different network architectures then the PyTorch model defined.

*Network:*

        # Define the network layers
        self.fc1 = nn.Linear(state_size, fc1_units)
        self.fc2 = nn.Linear(fc1_units, fc2_units)
        self.fc3 = nn.Linear(fc2_units, action_size)

Enjoy!
