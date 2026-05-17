# part-1-neural-network-analysis
---

## Final Reflection

### What role do weights and biases play in the model?

Weights determine the strength and importance of the connection between input features and neurons in the next layer. During training, these weights are continuously adjusted through backpropagation to minimize prediction error and improve model performance.

Biases act as additional parameters that shift the activation function, similar to the intercept term (`c`) in the equation `y = mx + c`. They allow the network to produce flexible outputs even when input values are zero, improving the model’s ability to learn complex patterns.

---

### Why is an activation function required?

Activation functions introduce non-linearity into the neural network. Without them, multiple layers of neurons would behave like a single linear model, limiting the network’s ability to learn complex relationships.

Functions such as ReLU, Sigmoid, and Tanh enable the model to capture non-linear decision boundaries and intricate data patterns, which are essential for solving real-world problems like image recognition, classification, and prediction tasks.

---

### What happens when the learning rate is too high or too low?

The learning rate controls how much the model updates its weights during gradient descent.

- **Learning rate too high:**  
  The model may take excessively large steps during optimization, causing it to overshoot the minimum loss point. This can lead to unstable training, oscillation, or complete divergence.

- **Learning rate too low:**  
  The model updates weights very slowly, resulting in long training times and delayed convergence. In some cases, the model may get stuck in local minima or fail to learn effectively.

Choosing an optimal learning rate is important for achieving stable and efficient training.

---

### Did your model show signs of underfitting or overfitting? Explain.

If the training accuracy is significantly higher than the validation or testing accuracy, the model demonstrates **overfitting**. In this case, the network memorizes training data patterns but struggles to generalize to unseen data.

If both training and validation accuracy remain low, the model is **underfitting**, indicating that it lacks sufficient complexity or training capacity to capture meaningful relationships in the dataset.

A well-balanced model should achieve high accuracy on both training and testing datasets with minimal performance gap, indicating good generalization capability.

---
