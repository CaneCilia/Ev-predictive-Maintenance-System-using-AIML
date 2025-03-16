To build a robust AI model for predicting EV system health, the dataset includes three key target variables: **battery_failure**, **motor_failure**, and **system_health_status**. Each of these variables plays a crucial role in identifying potential issues and ensuring the vehicle's optimal performance. Below is a detailed explanation of each target variable, including its purpose, structure, and example data.

### **Battery Failure Prediction**
The **battery_failure** variable is a **binary classification** target that indicates whether the battery is likely to fail or experience significant degradation. This prediction is essential for identifying potential battery replacement needs, ensuring vehicle safety, and preventing unexpected breakdowns. The feature is represented as a boolean value — `True` or `False`.

For instance, a battery with **95% health**, **300 charging cycles**, and no recorded temperature spikes is less likely to fail, resulting in a `False` value for `battery_failure`. Conversely, a battery with **45% health**, **600 charging cycles**, and a recent temperature spike would be more susceptible to failure, resulting in a `True` value. This binary classification helps fleet managers, service centers, and EV owners proactively address battery issues before they become critical.

| **battery_health** | **charging_cycles** | **temperature_spike** | **battery_failure** |
|:------------------|:--------------------|:-----------------------|:---------------------|
| 95%                 | 300                  | False                    | False                  |
| 45%                 | 600                  | True                     | True                   |

### **Motor Failure Prediction**
The **motor_failure** variable is also a **binary classification** target designed to predict the likelihood of motor malfunction or deterioration. This prediction is crucial in identifying motor wear, ensuring efficient performance, and enabling proactive maintenance.

For example, a motor operating at **60°C**, with an efficiency level of **90%**, and no recorded overcurrent alerts is less prone to failure (`False`). Conversely, a motor running at a high temperature of **85°C**, with reduced efficiency at **65%**, and an overcurrent alert triggered may indicate a deteriorating motor, resulting in a `True` value for `motor_failure`.

| **motor_temperature** | **motor_efficiency** | **overcurrent_alert** | **motor_failure** |
|:-----------------------|:---------------------|:------------------------|:-------------------|
| 60°C                    | 90%                   | False                    | False                |
| 85°C                    | 65%                   | True                     | True                 |

### **System Health Status Prediction**
The **system_health_status** variable is a **multi-class classification** target that provides a comprehensive assessment of the EV’s overall system health. This value is categorized into three possible states: `"Healthy"`, `"Warning"`, or `"Critical"`. Predicting this status allows for efficient risk assessment, enabling timely interventions to prevent failures.

For example, an EV with **92% battery health** and **88% motor efficiency** would likely be classified as `"Healthy"`, reflecting stable system conditions. On the other hand, reduced battery health at **60%** and motor efficiency at **55%** may trigger a `"Warning"` status, indicating potential concerns that require attention. An EV showing severe deterioration — with **40% battery health** and **30% motor efficiency** — would be classified as `"Critical"`, signaling an urgent need for maintenance.

| **battery_health** | **motor_efficiency** | **system_health_status** |
|:-------------------|:---------------------|:-------------------------|
| 92%                 | 88%                   | "Healthy"                  |
| 60%                 | 55%                   | "Warning"                  |
| 40%                 | 30%                   | "Critical"                 |

### **Model Recommendations for Prediction**
To effectively predict these outcomes, different machine learning models are recommended based on the nature of each target variable:

- For **binary classification** tasks such as `battery_failure` and `motor_failure`, models like **Random Forest**, **XGBoost**, and **Logistic Regression** offer high accuracy and interpretability.
- For **multi-class classification** tasks such as `system_health_status`, models like **XGBoost with Softmax**, **LightGBM**, and **Neural Networks** (e.g., Multi-Layer Perceptron) are well-suited to handle complex data patterns.

Choosing the right model depends on the dataset size, complexity, and available computational resources. Feature engineering, proper data normalization, and effective hyperparameter tuning will further enhance model performance and ensure accurate EV system health predictions.