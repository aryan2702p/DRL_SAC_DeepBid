# Soft Actor-Critic (SAC) for Renewable Energy Management

This project implements a Soft Actor-Critic (SAC) reinforcement learning algorithm to optimize battery storage in a renewable energy system. The goal is to maximize the profit by managing the energy storage and dispatch based on the renewable energy generation and market prices.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Algorithm Details](#algorithm-details)
- [Environment Details](#environment-details)
- [Training](#training)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction
The project aims to develop a reinforcement learning agent using the Soft Actor-Critic (SAC) algorithm to manage energy storage in a renewable energy system. The agent learns to make decisions on energy storage and dispatch to maximize profit based on the renewable energy generation and market prices.

## Installation
To run this project, you need to have Python installed. You can install the required dependencies using the following command:
```bash
pip install -r requirements.txt
```

## Usage
1. **Prepare Data**: Ensure that the data files are placed in the `data/` directory.
2. **Run Notebook**: Open the `SAC.ipynb` Jupyter Notebook and run the cells to train the SAC agent.

## Algorithm Details

### Soft Actor-Critic (SAC)
SAC is an off-policy actor-critic algorithm that aims to maximize the expected reward while also maximizing entropy. This encourages exploration and robustness to changes in the environment.

#### Actor Network
The actor network outputs the mean (`mu`) and log standard deviation (`log_std`) of the action distribution. Actions are sampled from a Gaussian distribution and then squashed using a `tanh` function to ensure they are within the valid range.

#### Critic Network
The critic networks (Q-functions) take both the state and action as input and output the Q-value.

#### SAC Agent
The SAC agent implements the update logic, including the soft update of target networks and the entropy term in the actor loss.

## Environment Details
The environment simulates the renewable energy system, including energy generation, market prices, and battery storage.

### State
The state includes:
- `gen`: Renewable energy generation
- `imb`: Market imbalance price
- `E`: Energy stored in the battery
- `additional_feature`: Any additional feature (optional)

### Action
The action includes:
- `bid`: Bid amount
- `rat`: Rate

### Environment Methods
- `reset()`: Resets the environment to the initial state.
- `step(action)`: Executes a step in the environment based on the given action and returns the next state, reward, done flag, and additional info.

## Training
The training loop involves:
1. Initializing the environment and agent.
2. Running episodes where the agent interacts with the environment.
3. Collecting experiences and storing them in a replay buffer.
4. Updating the agent using mini-batches sampled from the replay buffer.
5. Printing metrics to monitor the training progress.

### Training Parameters
- `num_episodes`: Number of episodes to train the agent.
- `batch_size`: Size of the mini-batch used for training.
- `max_buffer_size`: Maximum size of the replay buffer.
- `max_iteration`: Maximum number of iterations per episode.
- `print_interval`: Interval for printing training metrics.

## Results
The results include metrics such as Mean Absolute Error (MAE), Mean Bias Error (MBE), and revenue for training, validation, and testing. These metrics are printed every `print_interval` episodes to monitor the training progress.

## Contributing
Contributions are welcome! Please feel free to submit a pull request.

