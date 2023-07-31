# Report on CSOC RL Model Training and Performance Evaluation Project

## Introduction

This comprehensive report presents the efforts made to develop and train a Reinforcement Learning (RL) model for the MinerlTreechop environment. The primary goal was to create a working RL model using a custom policy based on convolutional neural networks (CNNs). Additionally, I will discuss the challenges I encountered during the project and provide insights into potential improvements.

## Project Overview

The project was initiated based on a previous successful attempt with Vizdoom, aiming to create a similar working model for the MinerlTreechop environment. I started by exploring the Minerl library and its documentation. During this process, the first challenge arose, as the installation of the Minerl library required a specific version of Java, which I had to address to proceed further. Additionally, I came across a message in the Minerl Discord server suggesting the use of RL libraries or custom stable baselines libraries for better results.

## Challenges Encountered

1. **Minerl Library Installation:** The initial hurdle in the project was the installation of the Minerl library, which demanded a specific version of Java to be installed. Overcoming this challenge was essential to move forward with the project.

2. **Use of rlibs:** In an attempt to find an alternative solution, I tried using rlibs as suggested on the Minerl Discord server. However, the rlibs library proved to be quite complex, and progress beyond 30% was hindered.

3. **Switch to Custom Models:** To overcome the limitations faced with rlibs, I decided to switch to creating custom models. This decision was supported by my prior experience with open-source contributions in ML projects, although my experience was limited to three projects.

## Custom Model Development

The custom models were implemented as follows:

1. **CustomCnnFeatureExtractor:** The CustomCnnFeatureExtractor is a fundamental component of the RL model designed for the MinerlTreechop environment. Its main purpose is to serve as a feature extractor that takes raw observations from the environment and transforms them into a meaningful feature representation. This feature representation is crucial for the subsequent decision-making process in the RL model.

The feature extraction process is performed using a sequence of Convolutional Neural Network (CNN) layers. CNNs are well-suited for image processing tasks due to their ability to capture spatial relationships and detect relevant patterns in visual data. The CustomCnnFeatureExtractor class leverages the power of CNNs to learn high-level features from the raw observation space.

The architecture of the CustomCnnFeatureExtractor consists of several CNN layers with non-linear activation functions in between. Each CNN layer applies a set of learnable filters to the input observations, producing feature maps that represent different visual aspects of the environment. These feature maps are then passed through non-linear activation functions (such as ReLU) to introduce non-linearity and enhance the network's ability to capture complex patterns.

The output of the last CNN layer is flattened to create a one-dimensional feature vector, which serves as the extracted features. These features are then passed on to the subsequent component, the CustomCnnPolicy, for action selection.

2. **CustomCnnPolicy:** The CustomCnnPolicy builds upon the feature extraction capabilities of the CustomCnnFeatureExtractor. It takes the extracted features and feeds them through fully connected layers to produce action logits. These action logits represent the raw scores assigned to each possible action in the RL model's action space.

The CustomCnnPolicy class plays a crucial role in the RL agent's decision-making process. By mapping the extracted features to action logits, the policy effectively determines the agent's next action based on the current observations from the environment.

The architecture of the CustomCnnPolicy consists of fully connected (dense) layers, which take the one-dimensional feature vector obtained from the CustomCnnFeatureExtractor and process it further. These layers introduce additional non-linearity and learn to capture complex relationships between the extracted features and the optimal actions to take in the environment.

The final layer of the CustomCnnPolicy produces the action logits, which are then converted into probabilities through a softmax activation function. These probabilities represent the likelihood of selecting each action from the RL model's action space.
3. **MinerlTreechopActionSpace:** The MinerlTreechopActionSpace is a crucial aspect of the RL model specifically tailored to the unique action space of the Minerl Treechop environment. In RL, an action space defines all possible actions that an agent can take in the environment. However, environments may have discrete or continuous action spaces, each with specific constraints and requirements.

In the case of MinerlTreechop, the action space is complex, consisting of multiple discrete actions, each representing various in-game actions the agent can perform, such as moving, jumping, attacking, and camera movement. The MinerlTreechopActionSpace class acts as an interface that facilitates the conversion between the RL model's action representation (action logits) and the corresponding in-game actions required by the environment.

The MinerlTreechopActionSpace provides methods to transform action logits into a dictionary format suitable for the Minerl Treechop environment. This dictionary contains binary values representing whether each in-game action should be performed or not. It effectively maps the RL model's action space to the specific in-game actions needed to interact with the environment effectively.

4. **MinerlTreechopEnv:** The MinerlTreechopEnv is a custom environment class developed to encapsulate and adapt the MineRLTreechop-v0 environment for seamless integration with the RL model. It acts as a wrapper around the original environment, providing additional functionalities necessary for RL training and evaluation.

The primary role of the MinerlTreechopEnv is to adapt the action space to match the format required by the RL model. It also efficiently processes observations received from the environment before passing them to the feature extraction component.

Additionally, the MinerlTreechopEnv class handles resetting the environment, processing rewards, and monitoring the episode's termination conditions. It serves as a bridge between the RL model and the underlying MineRLTreechop-v0 environment, ensuring a smooth interaction and efficient training process.

By developing the MinerlTreechopEnv class, the RL model can interact with the Minerl Treechop environment effectively and efficiently learn optimal policies to achieve its objectives.

## Testing with Random Policy

To verify the correctness of the custom environment and models, a `RandomPolicy` was implemented. However, during testing, it was observed that the total reward obtained by the agent was consistently 0.0, suggesting possible issues with the policy's action sampling or reward calculation. Debugging and resolving these issues are essential to ensure proper functioning of the RL model.

## SAC Training and Error

Efforts were made to train the RL model using the Soft Actor-Critic (SAC) algorithm, a popular off-policy RL algorithm. However, an error related to the `use_sde` argument during the SAC model's initialization prevented successful training.

## Recommendations

To overcome the challenges and enhance the project's success, the following recommendations are proposed:

1. **Error Debugging in SAC Training:** Investigate and resolve the error related to the `use_sde` argument in the SAC model initialization. Ensure that the argument is correctly used and matches the policy's definition.

2. **Debugging Random Policy:** Examine the random policy implementation thoroughly to identify any issues with action sampling or reward calculation. Ensure that the policy explores the environment effectively and obtains non-zero rewards during testing.

3. **Documentation and Collaboration:** Maintain detailed documentation of steps, challenges, and debugging attempts. Proper documentation aids in troubleshooting and collaboration with the community to gain valuable insights and assistance.

## Conclusion

The project showcased commendable efforts in building a custom RL model for the MinerlTreechop environment. The implementation of custom policies and feature extractors demonstrated an understanding of RL concepts and model design. However, challenges related to installation, policy implementation, and training must be addressed to achieve optimal performance. By adhering to the recommended actions and continuous improvements, the project is poised to deliver a successful RL model capable of achieving satisfactory performance in the MinerlTreechop environment. Collaboration and documentation play a vital role in navigating through obstacles and maximizing the project's potential for success.

