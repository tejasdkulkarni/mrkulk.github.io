---
title: Open Questions in Machine Intelligence
updated: 2016-04-14 04:04
use_math: true
---

> This is a running post aggregating some key open questions in Machine Intelligence. If you want to suggest an update, email me -- tejasdkulkarni@gmail.com   

## The nature and origin of goals and intrinsic motivation
Let us start with the notion of value functions $V(s)$, where $s$ denotes the state of the world. $V(s)$ caches the utility of $s$ towards achieving any desidred goal $g$. In typical reinforcement learning settings, the agent observes rewards and states from the environment and takes actions to estimate the value function:

$$V(S) = \mathbb E(\sum_{t=0}^\infty \gamma_t r_{t+1} | s, \pi)$$

Here $\gamma$ denotes a discount factor which ensures a convergent series when the episode length $t$ is arbitrary. $\pi$ denotes the goal-directed policy that maps states to actions. 

Value functions are more important than rewards. Rewards are observed only in certain states. Value functions provide an estimate of expected future rewards from an aribtrary state in the environment, given the agent sufficiently explores the environment. This feature is crucial for generalization. But what happens when the agent cannot sufficiently explore high-dimensional state spaces or if the reward is too sparse? In such typical situations, the agent could benefit from being intrinsically motivated to come up with 'useful' goals to solve. 

The most basic form of intrinsic motivation could be stated as -- "learning feels good". But can we do better? I have listed some landmark papers on this topic:

1. _Intrinsically Motivated Reinforcement Learning: An Evolutionary Perspective_ by Singh et al.
* [Paper Link](http://web.eecs.umich.edu/~baveja/Papers/IMRLIEEETAMDFinal.pdf)
* This paper introduces the idea of optimal reward functions. Optimal reward functions are internal to the agent and are evolved over multiple generations of the agent. The environment induces a fitness function, which does natural selection of this reward function. The agent learns a policy under this reward function and the process continues. The deep insight about this paper is the nature and origin of intrinsically motivated behavior like curiosity or self-play. Some reward functions might encourage the agent to behave in ways that does not affect the fitness value immediately but could potentially have a big effect in the future. So this paper basically provides an emergent account of curiosity. Humans engage in curiosity driven behavior at an early stage. They indulge in behaviors such as block stacking which dosen't have immediate utility but are crucial to build up motor skills for the future. 

2. _Formal theory of creativity, fun, and intrinsic motivation_ by Schmidhuber et al.
* [Paper Link](http://people.idsia.ch/~juergen/ieeecreative.pdf)
* Schmidhuber introduced a task-agnostic notion of intrinsic motivation based purely on learning. Along with the typical RL machinery, assume the agent also learns a predictive world model. Given a history of states, the model should be able to predict the future. Now the intrinsic reward for current iteration $t$ can be defined as the delta between the model's predictive quality on the entire history $s_{1, t+1}$ versus the quality on $s_{1,t}$. The reinforecment learning machinery can then use this intrinsic reward along with the reward provided by the environment to find an optimal policy. 


<div class="divider"></div>

## Control over the Reward Channel
How do we ensure that an AI agent does not take control of it’s own reward channel?
<div class="divider"></div>

## Logical Uncertainty
<div class="divider"></div>

## Value Function Alignment
How do we practically align an AI’s value function with ours over long periods of time?
<div class="divider"></div>

## Human Goals
To build AI to solve human-like goals (perception, motor-control, etc.), how should we think about intermediate representations for efficient goal-directed behavior?
<div class="divider"></div>

## What are the physical bounds on intelligence?
<div class="divider"></div>

## Grounding
Deconstructing or grounding ‘thought’ and ‘knowledge’ to experiences
<div class="divider"></div>




