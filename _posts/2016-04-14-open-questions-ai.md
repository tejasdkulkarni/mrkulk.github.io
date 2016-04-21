---
title: Open questions in machine intelligence
updated: 2016-04-14 04:04
layout: post
comments: true
use_math: true
---

> This is a running post aggregating some key open questions in Machine Intelligence. If you want to suggest an update, comment below.  

## Building predictive models of the world at different temporal resolutions
Existing agents do not understand the environment we inhabit. In order to efficiently plan with minimal environmental interactions, it is necessary for the agent to learn knowledge at different spatio-temporal abstractions. For example, even if you haven't been in a car crash, you can predict sequence of high-level events following the crash or you could even imagine rough visual imagery of the scene. Current AI systems are nowhere close to achieving such a feat. 

<div class="divider"></div>

## The nature and origin of goals and intrinsic motivation
Let us start with the notion of value functions $V(s)$, where $s$ denotes the state of the world. $V(s)$ caches the utility of $s$ towards achieving any desidred goal $g$. In typical reinforcement learning settings, the agent observes rewards and states from the environment and takes actions to estimate the value function:

$$V(s)=max\_{\pi} \mathbb E ( \sum_{t'=t}^\infty \gamma^{t'-t} r\_{t'} \mid s\_t=s, \pi ) $$

Here $\gamma$ denotes a discount factor which ensures a convergent series when the episode length $t$ is arbitrary. $\pi$ denotes the goal-directed policy that maps states to actions. 

Value functions are more important than rewards. Rewards are observed only in certain states. Value functions provide an estimate of expected future rewards from an aribtrary state in the environment, given the agent sufficiently explores the environment. This feature is crucial for generalization. But what happens when the agent cannot sufficiently explore high-dimensional state spaces or if the reward is too sparse? In such typical situations, the agent could benefit from being intrinsically motivated to come up with 'useful' goals to solve. The most basic form of intrinsic motivation could be stated as -- "learning feels good". Can we say something more tangible? I have listed some landmark papers on this topic:

* **[Intrinsically Motivated Reinforcement Learning: An Evolutionary Perspective](http://web.eecs.umich.edu/~baveja/Papers/IMRLIEEETAMDFinal.pdf)**: Singh et al. introduced the idea of optimal reward functions. Optimal reward functions are internal to the agent and are evolved over multiple generations of the agent. The environment induces a fitness function, which does natural selection of this reward function. The agent learns a policy under this reward function and the process continues. The deep insight about this paper is the nature and origin of intrinsically motivated behavior like curiosity or self-play. Some reward functions might encourage the agent to behave in ways that does not affect the fitness value immediately but could potentially have a big effect in the future. So this paper basically provides an emergent account of curiosity. Humans engage in curiosity driven behavior at an early stage. They indulge in behaviors such as block stacking which dosen't have immediate utility but are crucial to build up motor skills for the future. 

* **[Formal theory of creativity, fun, and intrinsic motivation](http://people.idsia.ch/~juergen/ieeecreative.pdf)**: Schmidhuber introduced a task-agnostic notion of intrinsic motivation based purely on learning. Along with the typical RL machinery, assume that the agent also learns a predictive world model. Given a history of states, the model should be able to predict the future. Now the intrinsic reward for current iteration $t$ can be defined as the delta between the model's predictive quality on the entire history $s\_{1, t+1}$ versus the quality on $s\_{1,t}$. The reinforecment learning machinery can then use this intrinsic reward along with the reward provided by the environment to find an optimal policy. 

<div class="divider"></div>

## Efficiently solving Human Goals
To build AI to solve human-like goals such as navigation, scene understanding, motor-control, etc., how should we think about intermediate representations for efficient goal-directed behavior? Evolution has spent billions of years tuning biological agents to adapt in stochastic environments. A compact way to transfer information between agents is to encode useful goals into the genome, so that the agent can learn a policy to accomplish such goals during its lifetime. The niche of the universe we found ourselves in dictates the regularities in our environment. Due to this regularity, it is concievable for evolution to preserve basic goals such as discovering visual concepts, which may turn out to be useful to learn many higher order behaviors. [This is evident in baby Gazelle which learns to walk and do basic navigation within 10 minutes from birth](https://www.youtube.com/watch?v=iprhW773VyI).

This suggests an evolutionary account of why the brain creates sub-modules for different computations such as face processing. Early recognition of faces is critical for social intelligence and could also be leveraged to bootstrap learning about the visual world itself. What are the other mid-level representations that evolution could have preserved, that we as humans leverage in order to solve all the goals in our environmental niche? I believe understanding and building such representations will enable us to create data-efficient agents for solving many human goals.  

<div class="divider"></div>

## Control over the Reward Channel in Reinforcement Learning and Value Alignment
How do we ensure that an AI agent does not take control of it’s own reward channel? In a typical reinforcement learning setup, the agent tries to maximize expected future rewards to find optimal policies. In order to ensure that the agent continues to maximize it's reward channel, it can alter the it's environment in arbitrary ways. While doing so, the agent can disregard any human goals along it's path. How do we stop this? Nobody really knows but people have tried to come up with several arguments.

The most reasonable one I have come across is from [Daniel Dewey](https://intelligence.org/files/LearningValue.pdf). He argues that instead of expected future reward maximization, the agent should instead optimize expected utility over a pool of possible utilities. These utility functions could be designed so that the agent's values are consistent with human values. Since future trajectories over time are scored under a defined set of utility functions, even if the agent modifies it's _future_ utility functions, this improvement may not yield improvements according to the originally defined utility functions. And therefore this self-modification of future utilities will not be chosen by the agent. 

> Tejas Kulkarni, Cambridge, MA
