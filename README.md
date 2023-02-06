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

# Dependencies

1. Unity Editor to visualize the environment
2. Python 3.7.2 or higher
3. com.unity.ml-agents Unity package
4. com.unity.ml-agents.extensions Unity package
5. mlagents Python package


# Training a new model with Reinforcement Learning

A model was trained using proximal policy optimization with the following hyperparameters


 ## hyperparameters:
          batch_size:   64 
          buffer_size:  12000
          learning_rate:        0.0003
          epsilon:      0.2
          lambd:        0.99
          num_epoch:    3
          shared_critic:        False
          learning_rate_schedule:       linear
          beta_schedule:        linear
          epsilon_schedule:     linear
### network_settings:
          normalize:    True
          hidden_units: 128
          num_layers:   2
          vis_encode_type:      simple
          memory:       None
          goal_conditioning_type:       hyper
          deterministic:        False
### reward_signals:
          extrinsic:
            gamma:      0.99
            strength:   1.0
            network_settings:
              normalize:        False
              hidden_units:     128
              num_layers:       2
              vis_encode_type:  simple
              memory:   None
              goal_conditioning_type:   hyper
              deterministic:    False
        init_path:      None
        keep_checkpoints:       5
        checkpoint_interval:    500000
        max_steps:      500000
        time_horizon:   1000
        summary_freq:   12000
        threaded:       False
        self_play:      None
        behavioral_cloning:     None
        
        
        
 # Results 
 ![cumulative reward](https://user-images.githubusercontent.com/116836999/216882971-ab3da719-5b0c-41b2-8129-8737ea66987d.png)
 ![episode length](https://user-images.githubusercontent.com/116836999/216882999-f5e373c5-88ab-4f40-8abf-b022757752f2.png)


After about 250k steps the reward converges and reaches its maximum value of 100

# Embedding model into Unity environment
Now that we have trained out model we can test it out in the actual Unity environment<br>

The model is in the form of an .onnx file. It is placed in the proper directory and the environment is tested out

The below video shows the 3DBall environment tested out on out PPO trained model and we can see that the cubes are able to balance the balls.

https://user-images.githubusercontent.com/116836999/216885631-dfd1d65f-c7d6-4515-b6a6-c614e3ae7844.mp4




