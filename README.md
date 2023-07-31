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

1. **CustomCnnFeatureExtractor:** This custom class served as a feature extractor by applying a sequence of CNN layers on the observation space, resulting in a feature representation.

2. **CustomCnnPolicy:** Building on the `CustomCnnFeatureExtractor`, this class took the extracted features and passed them through fully connected layers to produce action logits.

3. **MinerlTreechopActionSpace:** A crucial aspect of the project was defining a custom action space specific to the Minerl Treechop environment. The `MinerlTreechopActionSpace` class facilitated the conversion between the RL model's actions and the corresponding in-game actions.

4. **MinerlTreechopEnv:** A custom environment class, `MinerlTreechopEnv`, was developed to wrap the `MineRLTreechop-v0` environment. This class adapted the action space and efficiently processed observations.

## Testing with Random Policy

To verify the correctness of the custom environment and models, a `RandomPolicy` was implemented. However, during testing, it was observed that the total reward obtained by the agent was consistently 0.0, suggesting possible issues with the policy's action sampling or reward calculation. Debugging and resolving these issues are essential to ensure proper functioning of the RL model.

## SAC Training and Error

Efforts were made to train the RL model using the Soft Actor-Critic (SAC) algorithm, a popular off-policy RL algorithm. However, an error related to the `use_sde` argument during the SAC model's initialization prevented successful training.

## Recommendations

To overcome the challenges and enhance the project's success, the following recommendations are proposed:

1. **Error Debugging in SAC Training:** Investigate and resolve the error related to the `use_sde` argument in the SAC model initialization. Ensure that the argument is correctly used and matches the policy's definition.

2. **Debugging Random Policy:** Examine the random policy implementation thoroughly to identify any issues with action sampling or reward calculation. Ensure that the policy explores the environment effectively and obtains non-zero rewards during testing.

3. **Experimentation and Hyperparameter Tuning:** Conduct further experimentation with different RL algorithms, hyperparameters, and exploration-exploitation strategies to optimize model performance. Hyperparameter tuning can significantly impact the model's learning and overall success.

4. **Documentation and Collaboration:** Maintain detailed documentation of steps, challenges, and debugging attempts. Proper documentation aids in troubleshooting and collaboration with the community to gain valuable insights and assistance.

5. **Visualization and Logging:** Incorporate visualization and logging during training to monitor model performance, detect potential issues, and track improvements. Visualization can provide crucial insights into the learning process.

6. **Evaluation on Validation Set:** After successful training, evaluate the trained model on a separate validation or test set to accurately assess its performance. Evaluating the model's generalization is crucial to ensure its effectiveness in real-world scenarios.

## Conclusion

The project showcased commendable efforts in building a custom RL model for the MinerlTreechop environment. The implementation of custom policies and feature extractors demonstrated an understanding of RL concepts and model design. However, challenges related to installation, policy implementation, and training must be addressed to achieve optimal performance. By adhering to the recommended actions and continuous improvements, the project is poised to deliver a successful RL model capable of achieving satisfactory performance in the MinerlTreechop environment. Collaboration and documentation play a vital role in navigating through obstacles and maximizing the project's potential for success.

