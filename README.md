# Deep Convolutional Q-Learning for Pac-Man

## Overview
This project implements a Deep Convolutional Q-Learning (DQN) algorithm to solve the classic game Pac-Man. The agent uses convolutional neural networks to process raw pixel input from the game and learn optimal policies through reinforcement learning.

## Environment Description

### Action Space
The action space consists of discrete actions representing the possible moves of Pac-Man:
- `0`: Move up
- `1`: Move right
- `2`: Move down
- `3`: Move left

### Observation Space
The state is represented by a frame of the game, which is an image of the game screen.

### Rewards
The rewards are structured as follows:
- Positive reward for eating pellets, power pellets, ghosts, and fruits.
- Negative reward for being eaten by ghosts.
- Additional rewards for completing a level.

### Episode Termination
An episode terminates when:
- Pac-Man is caught by a ghost.
- All pellets are eaten.
- A maximum number of steps is reached.

## Implementation

### Neural Network
A convolutional neural network (CNN) is implemented using TensorFlow with the following architecture:
- Input layer: The size of the input layer corresponds to the dimensions of the game frame (height, width, channels).
- Three convolutional layers:
  - Conv layer 1: 32 filters, 8x8 kernel, stride 4, ReLU activation.
  - Conv layer 2: 64 filters, 4x4 kernel, stride 2, ReLU activation.
  - Conv layer 3: 64 filters, 3x3 kernel, stride 1, ReLU activation.
- Flattening layer: Flattens the 3D output to 1D.
- Fully connected layer: 512 units, ReLU activation.
- Output layer: Size equal to the action space (4).

### Experience Replay
Experience replay is implemented to store and sample past experiences to break the correlation between consecutive experiences and stabilize training.

### DQN Agent
The DQN agent is responsible for:
- Selecting actions using an epsilon-greedy policy.
- Storing experiences in replay memory.
- Sampling experiences and learning from them.
- Performing updates on the target network to ensure stable training.

### Hyperparameters
The following hyperparameters are used:
- `learning_rate = 0.001`
- `minibatch_size = 32`
- `discount_factor = 0.95`
- `replay_buffer_size = 2000`
- `update_target_model_frequency = every episode`
- `number_episodes = 1000`
- `maximum_number_timesteps_per_episode = 5000`
- `epsilon_starting_value = 1.0`
- `epsilon_ending_value = 0.01`
- `epsilon_decay_value = 0.995`

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/deep-convolutional-q-learning-pacman.git
   cd deep-convolutional-q-learning-pacman
