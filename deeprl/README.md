# DeepRL
Modularized implementation of popular deep RL algorithms by PyTorch. Easy switch between classical control tasks (e.g., CartPole) and Atari games with raw pixel inputs.

Implemented algorithms:
* (Double/Dueling) Deep Q-Learning (DQN)
* Categorical DQN (C51, Distributional DQN with KL Distance)
* Quantile Regression DQN
* (Continuous/Discrete) Synchronous Advantage Actor Critic (A2C)
* Synchronous N-Step Q-Learning
* Deep Deterministic Policy Gradient (DDPG, pixel & low-dim-state)
* (Continuous/Discrete) Synchronous Proximal Policy Optimization (PPO, pixel & low-dim-state)
* The Option-Critic Architecture (OC)
* Action Conditional Video Prediction

Asynchronous algorithms (e.g., A3C) are removed in the current version but can be found in [v0.1](https://github.com/ShangtongZhang/DeepRL/releases/tag/v0.1).

# Dependency
* MacOS 10.12 or Ubuntu 16.04
* PyTorch v0.4.0
* Python 3.6, 3.5
* Core dependencies: `pip install -e .`
* Optional: [Roboschool](https://github.com/openai/roboschool), [PyBullet](https://pypi.org/project/pybullet/)

# Remarks
* There is a super fast DQN implementation with an async actor for data generation and an async replay buffer to transfer data to GPU. Enable this implementation by setting `config.async_actor = True` and using `AsyncReplay`. However, with atari games this fast implementation may not work in macOS. Use Ubuntu or Docker instead.
* Python 2 is not officially supported after [v0.3](https://github.com/ShangtongZhang/DeepRL/releases/tag/v0.3). However, I do expect most of the code will still work well in Python 2.
* Although there is a `setup.py`, which means you can install the repo as a library, this repo is **never** designed to be a high-level library like Keras. Use it as your codebase instead.

# Usage

```examples.py``` contains examples for all the implemented algorithms

```Dockerfile``` contains an example environment (w/ pybullet, w/ roboschool, w/o GPU)

Please use this bibtex if you want to cite this repo
```
@misc{deeprl,
  author = {Shangtong, Zhang},
  title = {Modularized Implementation of Deep RL Algorithms in PyTorch},
  year = {2018},
  publisher = {GitHub},
  journal = {GitHub Repository},
  howpublished = {\url{https://github.com/ShangtongZhang/DeepRL}},
}
```

# Curves

## BreakoutNoFrameskip-v4

![Loading...](https://raw.githubusercontent.com/ShangtongZhang/DeepRL/master/images/breakout.png)

* This is my synchronous option-critic implementation, not the original one.
* The curves are not directly comparable, as many hyper-parameters are different.

## RoboschoolHopper-v1

![Loading...](https://raw.githubusercontent.com/ShangtongZhang/DeepRL/master/images/hopper.png)

* The DDPG curve is the evaluation performance, rather than online.

## PongNoFrameskip-v4

![Loading...](https://raw.githubusercontent.com/ShangtongZhang/DeepRL/master/images/ACVP.png)

* *Left*: One-step prediction *Right*: Ground truth
* Prediction images are sampled after 110K iterations, and I only implemented one-step training for action-conditional-video-prediction.

# References
* [Human Level Control through Deep Reinforcement Learning](https://www.nature.com/nature/journal/v518/n7540/full/nature14236.html)
* [Asynchronous Methods for Deep Reinforcement Learning](https://arxiv.org/abs/1602.01783)
* [Deep Reinforcement Learning with Double Q-learning](https://arxiv.org/abs/1509.06461)
* [Dueling Network Architectures for Deep Reinforcement Learning](https://arxiv.org/abs/1511.06581)
* [Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602)
* [HOGWILD!: A Lock-Free Approach to Parallelizing Stochastic Gradient Descent](https://arxiv.org/abs/1106.5730)
* [Deterministic Policy Gradient Algorithms](http://proceedings.mlr.press/v32/silver14.pdf)
* [Continuous control with deep reinforcement learning](https://arxiv.org/abs/1509.02971)
* [High-Dimensional Continuous Control Using Generalized Advantage Estimation](https://arxiv.org/abs/1506.02438)
* [Hybrid Reward Architecture for Reinforcement Learning](https://arxiv.org/abs/1706.04208)
* [Trust Region Policy Optimization](https://arxiv.org/abs/1502.05477)
* [Proximal Policy Optimization Algorithms](https://arxiv.org/abs/1707.06347)
* [Emergence of Locomotion Behaviours in Rich Environments](https://arxiv.org/abs/1707.02286)
* [Action-Conditional Video Prediction using Deep Networks in Atari Games](https://arxiv.org/abs/1507.08750)
* [A Distributional Perspective on Reinforcement Learning](https://arxiv.org/abs/1707.06887)
* [Distributional Reinforcement Learning with Quantile Regression](https://arxiv.org/abs/1710.10044)
* [The Option-Critic Architecture](https://arxiv.org/abs/1609.05140)
* Some hyper-parameters are from [DeepMind Control Suite](https://arxiv.org/abs/1801.00690), [OpenAI Baselines](https://github.com/openai/baselines) and [Ilya Kostrikov](https://github.com/ikostrikov/pytorch-a2c-ppo-acktr)