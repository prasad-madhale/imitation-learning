# Imitation Learning via Reinforcecment Learning (ILRL)

This project uses policy gradient methods such as PPO or TRPO along with Generative Adversarial Networks to achieve Imitation Learning on discrete gym environments.

*Methodology used here is explained in **Generative Adversarial Imitation Learning (GAIL)** [[paper]](https://arxiv.org/pdf/1606.03476.pdf)*

### Gist of it:

**Given an Expert Policy as input the GAIL algorithm uses Policy Gradient method like PPO (in this case) to achieve Imitation Learning and in most cases the learned policy gets better than the input Expert Policy.**


**For more information why we choose this methodology over other algorithms read the report:** [GAIL to solve Discrete environments](https://github.com/prasadchelsea33/imitation-learning/blob/master/Report/PPO(Prasad%20Madhale).pdf)

## Overview:
1. **Run PPO algorithm** - run the PPO algorithm on an environment
    1. *Create Actor-Critic* architecture which represents the two policy networks
    2. *Code the PPO algorithm*
    3. *Train an agent using the PPO algorithm*
2. **Sample trajectories** - Sample some trajectories which represents the Expert Policy which we later use to train our agent which uses Imitation learning
    1. *Restore the agent policy network weights*
    2. *Sample some state and action using the expert policy*
    3. *Save the sampled states and actions into csv files*
3. **Test Expert Policy** - Test the learned expert policy to see if it satisfies the criteria for solving the environment (render the runs if you want)  
4. **Train agent using GAIL for imitation learning** - given the expert trajectories as input we use Generative Adversarial Imitation Learning to train the agent
    1. *Create a Discriminator* that differentiates between the Expert Policy and Generated Policy (same as in a conventional Generative Adversarial Network)
    2. *Train the agent* to learn by imitating the given expert policy (uses GAIL algorithm)
5. **Run Baseline implementations of PPO and TRPO to compare performance with our implementations**
6. **Observe reward plots on Tensorboard** - the tensorboard contains the following plots :-
    1. Our PPO implementation Reward and Lengths
    2. Expert Policy Testing plot
    3. GAIL reward and lengths plot
    4. Baseline reward, length and loss plots
    
**Note** - We can also use other Policy gradient methods like TRPO to generate expert policy as well as the utility algorithm in GAIL for Imitation Learning

## Dependencies:
1. Tensorflow (faster if you have GPU support enabled)
2. OpenAI gym
3. numpy

## Instructions to run:
1. Run Jupyter notebook or Jupyter lab
2. Open [GAIL.ipynb](https://github.com/prasadchelsea33/imitation-learning/blob/master/GAIL.ipynb) file
3. Follow the instructions in the notebook to run the project
4. Follow the instructions in the notebook to generate and observe the plots on *Tensorboard*

## Results on CartPole-v0 environment:

### Our PPO implementation Rewards
![Our PPO implementation Rewards](/plots/my_ppo.png)

### GAIL learned agent Rewards
![GAIL rewards](/plots/gail_rewards.png)

### Baseline PPO rewards
![Baselines PPO rewards](/plots/baseline_ppo.png)

## References:
1. Generative Adversarial Imitation Learning [[paper]](https://arxiv.org/pdf/1606.03476.pdf)
2. [OpenAI baselines GAIL](https://github.com/openai/baselines/tree/master/baselines/gail)
3. [Tensorflow implementation of Generative Adversarial Imitation Learning(GAIL) with discrete action](https://github.com/uidilr/gail_ppo_tf)
4. [Simple GAIL implementation using Tensorflow](https://github.com/AndyHsiao26/GAIL-Tensorflow)
