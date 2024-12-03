

## Fake Review Detection System

**Author**: Andrew Wright

### Executive Summary

Imagine an AI-powered detective that can spot fake online reviews in seconds. This project develops a machine learning model to protect consumers and businesses from misleading information, ensuring a safer and more trustworthy online shopping environment.

### Rationale

Why should anyone care about this question?  
Fake reviews have significant consequences:  
- **For Consumers**: They lead to poor purchasing decisions, wasting time and money.  
- **For Businesses**: They damage brand credibility and reduce revenue.  
- **For Platforms**: They create a lack of trust amongst users, impacting the marketplace's reputation.  

By automating fake review detection, we empower online platforms to maintain integrity and protect their users.

### Research Question

How can machine learning technology effectively distinguish fake reviews from genuine ones?

### Data Sources

We use a labeled dataset of online reviews where each review is marked as either fake or genuine. This provides the foundation for training and testing the model.  This dataset contains 40,000 reviews and is evenly split between real and fake.

Data Source: [Fake Reviews Dataset](https://www.kaggle.com/datasets/mexwell/fake-reviews-dataset/data)

### Methodology

1. **Collecting the Evidence**  
   Gather labeled data to provide the foundation for analysis.

2. **Cleaning the Data**  
   Preparing reviews by converting to lowercase, removing punctuation, eliminating stopwords (such as "and," "or," "but"), and applying stemming/lemmatization (reduces words to their base or root form "running" -> "run") to focus on the essence of the text.

3. **Encoding the Clues**  
   Human-readable text is transformed into numerical representations using **TF-IDF (Term Frequency-Inverse Document Frequency)**.
   - **Term Frequency (TF)**: How often a word appears in a document.
   - **Inverse Document Frequency (IDF)**: Reduces the importance of common words that appear in many documents.

4. **Training the Model**  
   Multiple algorithms (our "detectives") are trained, including:  
   - **Support Vector Machines (SVM)**: Finds a clear boundary between fake and genuine reviews.  
   - **Logistic Regression**: Estimates the probability of a review being fake.  
   - **Random Forest**: Combines decision trees for robust classification.  

5. **Fine-Tuning**  
   Optimizing hyperparameters like `C`, `kernel`, and `gamma` using **GridSearchCV**.
   - **GridSearchCV** systematically tests multiple combinations of hyperparameters to find the best-performing configuration for a model. It performs cross-validation on each combination, ensuring the chosen settings maximize the model's performance.

6. **Evaluating the Models**  
   Models are tested using metrics like accuracy and confusion matrices to visualize their performance.

### Results

Our system achieved impressive accuracy:  
- **SVM (Support Vector Machine)**: 87.40%
<br> ![SVM Confusion Matrix](images/svm_confusion_matrix.png)
- **Logistic Regression**: 87.18%
<br> ![Logistic Regression Confusion Matrix](images/logistic_reg_confusion_matrix.png)
- **Random Forest**: 84.40%
<br> ![Random Forest Confusion Matrix](images/random_for_confusion_matrix.png)

Ultimately, **SVM** was chosen as the final model based on the accuracy with which it was able to classify the reviews.

#### What is SVM?

**Support Vector Machine (SVM)** is a type of machine learning algorithm that helps a computer make decisions by finding the best way to separate things into categories. Imagine drawing a line (or a curve) on a graph to divide different groups of points—SVM finds the line that separates them with the biggest "gap" or margin, making it easier to classify new points correctly.

While basic SVMs work well with linearly separable data, real-world problems often require more complex decision boundaries. This is where kernel tricks come into play. Kernels allow SVM to transform the original input space into a higher-dimensional feature space, enabling the algorithm to create non-linear decision boundaries. Think of it like stretching and warping a piece of paper so that previously mixed-up points can be cleanly separated—this mathematical transformation lets SVM handle more intricate classification challenges, making it powerful for complex datasets like detecting nuanced differences between fake and genuine reviews.

It's like sorting items into boxes where SVM decides the neatest way to draw the boundary between the boxes, even when those boxes aren't simply arranged!

### Next Steps

We plan to enhance the system by:  
- Expanding the dataset to include reviews from more websites.  
- Cross-market testing to evaluate performance across various marketplaces.  
- Building a live system to flag suspicious reviews in real time.

### Outline of Project

- [Data Exploration Notebook](notebooks/ExploringData.ipynb): Discover the initial data preparation and exploratory analysis.  
- [Final Project Notebook](notebooks/CapstoneFinal.ipynb): See how the models were built, trained, and evaluated.

### Contact and Further Information

Feel free to reach out for questions, suggestions, or further information.

Andrew Wright - [LinkedIn](https://www.linkedin.com/in/wrightandy/)
