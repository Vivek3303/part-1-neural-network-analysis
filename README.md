# part-1-neural-network-analysis
---

## Final Reflection

* **What role do weights and biases play in the model?**
Weights determine the strength and importance of the connection between inputs and the subsequent neuron. During training (via backpropagation), these weights are continually updated to minimize the error. The bias acts as an intercept, allowing the activation function to be shifted left or right to better fit the data, ensuring the model can fire even when all input features are zero.

* **Why is an activation function required?**
Without activation functions, a neural network—regardless of how many hidden layers it has—would mathematically behave as a single linear regression model. Activation functions (like ReLU or Tanh) introduce non-linearity into the network, allowing it to learn complex, non-linear relationships and boundaries within the data.

* **What happens when the learning rate is too high or too low?**
The learning rate dictates the step size taken during gradient descent. If the learning rate is too high, the algorithm may overshoot the global minimum, bouncing around and failing to converge. If it is too low, the network takes excessively small steps, leading to very slow convergence and a high risk of getting stuck in local minima.

* **Did your model show signs of underfitting or overfitting? Explain.**
Customer churn datasets are inherently imbalanced (the vast majority of customers are retained). In early testing, the model achieved 98% accuracy by simply overfitting to the majority class, resulting in a Recall of 0.0 for actual churners. 

To correct this, I introduced balanced **Class Weights** and **Dropout layers**. The results perfectly illustrated the Accuracy/Recall trade-off:
* **Experiment 1 (2 Layers, 64 Neurons, Heavier Dropout):** Reverted to majority-class prediction (Recall 0.0, Accuracy 95.5%), indicating that the model underfit the minority class due to excessive dropout combined with early stopping. 
* **Experiment 2 (1 Layer, 32 Neurons, ReLU):** Achieved a much stronger Recall of ~42.8%, successfully identifying potential churners. The overall accuracy dropped to 74% as the model accepted more false positives to catch the minority class.

### Pro-Level Optimization (Experiment 3)
To push the model to industry standards, I implemented **L2 Regularization**, a dynamic **Learning Rate Scheduler** (`ReduceLROnPlateau`), and evaluated custom decision thresholds. 

By dropping the decision threshold from 50% to 35%, the model demonstrated the classic Precision-Recall trade-off. The model's ability to catch true churners (Recall) doubled, jumping from 29% to 57% (catching 4 out of 7 actual churners). To achieve this, the model accepted more False Positive alarms (21), gracefully dropping the overall Accuracy to 94%. In a real-world business context, a 94% accuracy model that successfully flags over half of the at-risk customers is significantly more valuable than a 98% accuracy model that misses them entirely.

A well-balanced model should achieve high accuracy on both training and testing datasets with minimal performance gap, indicating good generalization capability.

---
