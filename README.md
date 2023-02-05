# 3D-Ball-Unity

This project consists of a description of opening an example Unity environment, training it using Proximal policy optimization and embedding the trained model into the Unity environment

# 3D-Ball-Environment

![simulation](https://user-images.githubusercontent.com/116836999/216847145-71515ad7-ebdf-41f4-a7d2-4e0a5eabec55.png)

The environent consists of 12 agents or cubes with faces on them and each agent has a small ball on its upper side. The goal is to make the agents behave in such a way that they balance the balls on their heads by tilting in the correct manner.


# Agent

Behavior Parameters — Every Agent must have a Behavior. The Behavior determines how an Agent makes decisions.
Max Step — Defines how many simulation steps can occur before the Agent's episode ends. In 3D Balance Ball, an Agent restarts after 5000 steps.
Behavior Parameters : Vector Observation Space
Before making a decision, an agent collects its observation about its state in the world. The vector observation is a vector of floating point numbers which contain relevant information for the agent to make decisions.

The Behavior Parameters of the 3D Balance Ball example uses a Space Size of 8. This means that the feature vector containing the Agent's observations contains eight elements: the x and z components of the agent cube's rotation and the x, y, and z components of the ball's relative position and velocity.

Behavior Parameters : Actions
An Agent is given instructions in the form of actions. ML-Agents Toolkit classifies actions into two types: continuous and discrete. The 3D Balance Ball example is programmed to use continuous actions, which are a vector of floating-point numbers that can vary continuously. More specifically, it uses a Space Size of 2 to control the amount of x and z rotations to apply to itself to keep the ball balanced on its head.
