# deep-learning-challenge

**Alphabet Soup Charity Model Report**

## Overview
This report outlines the development and optimization of a deep learning model aimed at predicting the success of organizations funded by Alphabet Soup. The binary classification neural network was constructed, trained, and optimized to enhance predictive accuracy.

The dataset comprised categorical and numerical variables linked to funding applications. Preprocessing steps were conducted to clean and transform the data before model training to ensure optimal feature representation and improve model performance.

---

## 1. Data Preprocessing

### **Target Variable:**
- **IS_SUCCESSFUL** (Binary: 1 for successful, 0 for unsuccessful)
- This variable indicates whether an organization’s funding request was successful, serving as the model's prediction target.

### **Feature Variables:**
- All relevant columns remaining after removing unique identifiers and non-predictive attributes.
- Features include application type, organization classification, funding amount requested, and other characteristics influencing success probability.

### **Removed Variables:**
- **EIN and NAME** (as they do not contribute to prediction).
- These columns contain unique identifiers specific to each organization, making them irrelevant for predicting success outcomes.

### **Handling Categorical Data:**
- **APPLICATION_TYPE** and **CLASSIFICATION** had numerous unique categories.
- Since some categories appeared infrequently, they were consolidated into an "Other" category to reduce dimensionality and improve generalization.
- One-hot encoding (`pd.get_dummies()`) was applied to convert categorical variables into numerical representations, enabling their use in the neural network.

### **Splitting Data:**
- Data was split into training (75%) and testing (25%) sets using `train_test_split()` to ensure the model learns from one subset and is evaluated on another.

### **Feature Scaling:**
- `StandardScaler` was applied to normalize numerical features for consistency in distribution, ensuring fair weight assignment across different scales of data.

---

## 2. Initial Model Configuration (AlphabetSoupCharity.ipynb)

### **Model Architecture:**
- **Input Layer:** Matches the number of dataset features.
- **Hidden Layer 1:** 9 neurons, ReLU activation function to introduce non-linearity and capture complex patterns.
- **Hidden Layer 2:** 18 neurons, ReLU activation to enhance feature learning.
- **Output Layer:** 1 neuron, Sigmoid activation for binary classification, outputting probabilities for success.

### **Compilation:**
- **Loss Function:** Binary Crossentropy, suitable for binary classification tasks.
- **Optimizer:** Adam, chosen for its adaptive learning rate and efficiency in convergence.
- **Metric:** Accuracy, used to evaluate model performance.

### **Training:**
- Trained for 100 epochs to allow the model to learn sufficient patterns from the data.

### **Performance Results:**
- **Loss:** 0.5543
- **Accuracy:** 72.99%

---

## 3. Optimization Efforts (AlphabetSoupCharity_Optimization.ipynb)

### **Model Adjustments:**
- Introduced an additional hidden layer to deepen the network and improve feature learning.
- Adjusted the neuron count per layer to enhance learning capacity while maintaining efficiency.

### **Training Modifications:**
- Reduced training epochs to 20 to mitigate overfitting, ensuring the model generalizes well to new data.
- Applied a 15% validation split during training to monitor the model's performance on unseen data.

### **Activation Functions:**
- Retained ReLU for hidden layers due to its efficiency in handling vanishing gradient issues.
- Sigmoid activation remained for the output layer to ensure binary classification outputs remain within a probability range of 0 to 1.

### **Results After Optimization:**
- **Loss:** 0.5536
- **Accuracy:** 72.54%
- Despite optimization efforts, the model's accuracy decreased slightly instead of improving.

---

## 4. Final Summary

### **Final Accuracy Achieved:**
- **Initial Model:** 72.99%
- **Optimized Model:** 72.54%


### **Conclusion:**
- The final model classified successful funding applications with approximately **72.54% accuracy**, demonstrating moderate predictive ability.


