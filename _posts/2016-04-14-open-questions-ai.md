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
	* fdfdd
	* dfdf
2. df

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




