For **AWS Forecast** and the use case of **cost escalation of products**, the choice of the time series model depends on the data characteristics (trend, seasonality, volume, etc.) and forecasting horizon. AWS Forecast provides both **AutoML** (automatic selection) and **manual model selection**. The commonly used models are:

---

### **1. ARIMA (AutoRegressive Integrated Moving Average)**

* **Type:** Statistical
* **Use case:** Works well for data with **trend** but little seasonality.
* **Pros:** Simple, interpretable, good for linear trends.
* **Cons:** Not suitable for complex seasonal patterns or multiple covariates.

---

### **2. ETS (Exponential Smoothing)**

* **Type:** Statistical
* **Use case:** Data with **trend and seasonality**.
* **Pros:** Handles seasonality and trends explicitly.
* **Cons:** Cannot model complex interactions.

---

### **3. Prophet (Additive Regression Model)**

* **Type:** Regression-based (developed by Facebook)
* **Use case:** Data with **strong seasonality and holidays/events**.
* **Pros:** Easy to include external events (e.g., promotions, price hikes).
* **Cons:** Less accurate for highly volatile or sparse data.

---

### **4. DeepAR+ (Recurrent Neural Network, RNN)**

* **Type:** Machine Learning (RNN)
* **Use case:** Large-scale **product-level forecasting** across multiple related time series.
* **Pros:** Handles **non-linear trends, seasonality, and multiple related series**. Can produce probabilistic forecasts.
* **Cons:** Requires more data and tuning.

---

### **5. Transformer-based / NPTS (Neural Prophet Time Series)**

* **Type:** Deep Learning
* **Use case:** Long-term forecasts, capturing complex patterns in **cost escalation** across multiple products.
* **Pros:** Better for highly non-linear data and multi-seasonality.
* **Cons:** More compute-intensive.

---

### ✅ **Typical AWS Forecast Recommendation**

* For **product cost escalation**, you often have:

  * **Historical prices** (trend)
  * **Promotions / events / supply shocks** (external factors)
  * **Multiple SKUs** (cross-product correlation)

* AWS Forecast typically suggests **DeepAR+** when:

  * You have **many products (time series)**
  * You want **probabilistic forecasts**
  * Cost escalation is **non-linear and influenced by multiple factors**

* If the dataset is small or mostly **linear**, **ETS or Prophet** may be sufficient.


Do you want me to do that?
