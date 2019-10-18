# Neural-Lyapunov-Control
This repository contains the code for learning Lyapunov functions and control policies of nonlinear dynamical systems in the paper:
Neural Lyapunov Control

## Requirements
- [dReal4](https://github.com/dreal/dreal4)
- [PyTorch](https://pytorch.org/get-started/locally/)

## How It Works
The framework consists of a learner and a falsifier. The learner minimizes the Lyapunov risk to find parameters in both a control function and a neural Lyapunov function. The falsifier takes the learned control function and the neural Lyapunov function from the learner and checks whether there is a state vector violating the Lyapunov conditions.

## A typical procedure for generating a pair of Lyapunov function and controller is as follows:
- Define the neural network with random parameters for Lyapunov function and initialize controller’s parameters to the solution of linear quadratic regular
- Define a controlled dynamical system 
- Set checking conditions for falsifier 
- Start training and verifying 
- Procedure stops when no counterexample is found by falsifier

The training part updates the parameters by iteratively minimizing the Lyapunov risk, a cost function measures the degree of violation of the Lyapunov conditions and the verifying part periodically searchs counterexample state vectors and add them back to the training set for the next iteration. This procedure provides flexibility to adjust the cost function for learning additional properties of controllers and Lyapunov functions. In example we add tuning term to maximize the region of attractions. 

## Example
- [Inverted pendulum](https://github.com/YaChienChang/Neural-Lyapunov-Control/blob/master/Inverted%20_Pendulum.ipynb)
- [Path following (kinematic bicycle model)](https://github.com/YaChienChang/Neural-Lyapunov-Control/blob/master/Path_Following%20(kinematic%20bicycle%20model).ipynb)
