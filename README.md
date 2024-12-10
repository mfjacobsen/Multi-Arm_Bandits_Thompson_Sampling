# Multi-Arm_Bandits_Thompson_Sampling
An exploration of solutions to multi-armed bandits using Thompson Sampling. 

This repository contains two files, 
- MAB_Thompson_Sampling.ipynb
- MAB_Thompson_Sampling_Exploration.ipynb

MAB_Thompson_Sampling.ipynb compares the effectiveness of a normal distribution and a t distribution for multi-arm bandits:

-  The run_single_simulation function should be used to simulate a single iteration of a multi-arm bandits problem.
-  The run_simulations function runs a monte carlo simulation and outputs mean and variance of the cumulative regret.
-  Code to run and visualize the outputs of the functions is included in the second half of the file.
-  The run_single_simulation_animation function outputs data for animating the Thompson sampling process.
-  Code to animate the normal and t distributions is included at the end of the file.

MAB_Thompson_Sampling_Exploration.ipynb is similar to the first file, but allows for comparison of thompson sampling with an extended exploration phase:

-  The run_single_simulation function should be used to simulate a single iteration of a multi-arm bandits problem.
-  The run_simulations function runs a monte carlo simulation and outputs mean and variance of the cumulative regret.
-  Code to run and visualze the outputs of the functions is included in the second half of the file.

Parameters to adjust: 

-  k = the number of of bandit arms
-  R = the range of the reward
-  T = the number of rounds in the game
-  N = the number of monte carlo simulation
  
-  explore_lens = an array containing the fixed explorations per arm. Set each index as an initial exploration length to compare the effectiveness of different lengths. The second index [1] will thompson sample with a t distribution, all other indices will sample using a normal distribution. Example: explore_lens = [2, 2, 15, 30] compares four algorithms. Three use normal thompson sampling with 2, 15, or 30 initial explorations per arm, one uses a t distribution for thompson sampling with 2 explorations per arm. Only used in MAB_Thompson_Sampling_Exploration.ipynb.

Note and Methods

- The distributions of the rewards for each arm are randomized for each simulation
- When Thompson sampling at each round, each arm is assigned a random quantile, which is used in each algorithms respective posterior distribution.
- The reward sequence for each arm is randomized for each trial, but is the same for all algorithms within each trial. That is the i'th time each algorithm chooses arm k, it will recieve reward x.
- The above two design choices allow for direct algorithm comparison for single simulations.

Conclusions
- Thompson sampling benefits from initial exploration
- Using a T distribution is effective
- Directly exploring each arm more than twice can outperform the T distribution
  

