Hi,

This is our final project for CS 598, DL4H, where we have reproduced a deep learning paper named - A Critical Evaluation of Local Explanations for Assessing Cervical Cancer Risk Factors

This is Himangshu, Jeremy and Mahesh in the team.

The original paper focuses on evaluating different explanation methods for assessing cervical cancer risk. It aims to provide insights into the quality and suitability of these explanations in a healthcare context.

Intro :
Cervical cancer is a life-threatening disease and one of the most prevalent types of cancer affecting women worldwide, Being able to adequately identify and assess factors that
elevate risk of cervical cancer is crucial.

The paper present a critical analysis of several existing local interpretability methods for explaining risk factors associated with cervical cancer.

It also, provide a method for analyzing and assessing the performances of various explanations

the ultimate goal of the paper is to help clinicians who use AI to better understand which types of explanations to use.

 

Specific approach : 
In the experiments done in this paper it tries to provide and empirical study analysing the performances of different methods for explaining cervical cancer risk factors. 

For each method, we contextualise how different formulations of these explanations might be appropriate for different patient contexts AND when an explainability technique may not be suitable for use. 

Finally, the it provides advice for practitioners as to how to use different types of explanations in practice for assessing and determining key factors for this type of cancer.

This paper also introduces an Algorithm for comparing the performances of various interpretability tools

It uses different matrices to to compare how explanations may differ in terms of their accuracy, compactness, consistency and robustness. Moreover, These metrics may be applicable in other contexts, beyond our cervical cancer risk assessment task.
 

Methodology: 

The paper proposes a systematic approach for interpreting the predictions of a black-box model using multiple interpretability methods

The approach consists
of three key phases: 
a) first we train a series of models for cervical cancer risk assessment and choose the best among these models; 
b) next, we interpret the models from thr previous step using a series of local explainability techniques; 
c) we compute a series of metrics to assess the plausibility and coherency of each of the explainability methods considered.

It is as described in the figure below - 




Results:
We have followed the code in the original paper and ran it locally to validate the results from the original paper with our local run. 

The original paper first compares the quality of each of the local explanation techniques and examine the top features produced by each of these techniques.

Next, we measure the decrease in accuracy of f∗ when we successively removed a fraction of the top features for each explanation. We have been able to get similar results as the original paper -

Overall, we see that LIME is the most robust to removal of features, while the model accuracy of all other explanations drops significantly after removing the top features

--- 
The top 30% important feature given by TreeSHAP have the most impact on model learning.

All explainers agree on HPV being the most important risk factor for cervical cancer

SHAP explainers have exactly the same top 10 most important features for Patient 1.

The most unstable explainers are those that depend on creating local neighborhoods.

Local surrogates and DiCE approximate 100% model’s output with 5 features.

Finally, it is seen that - No single explanation performs optimally across patients and metrics.


Future enhancement -







### Results

#### Table of results 
| Experiments | Original Paper Expectations (Hypothesis and Results) | Results | Discussions |
| :----: | :----: | :------: |:------: |
| Trained five different models - LR, RF, MLP, SVM and KNN with CV=10 |The paper mentioned RF as the model which performed as the best ML model for cervical cancer| RF, LR and MLP produced the best result with a score of 1 on F1, Accuracy, Precision, Recall and AUROC |  |
| Consistency between pairs of explainable AI models | Tree SHAP and Sampling SHAP is the most consistent pair, while Local Surrogate and DiCE is the least consistent pair. | We see that Local Surrogate and DiCE is the least consistent pair with a score of 1.4 and KSHAP and SSHAP having the least score of 0.025 | All SHAP models have similar scores and are quite consistent |  
| Faithfulness - removal of features doesn't affect model's accuracy | LIME is seen as the model with most faithful explanations while TreeSHAP has the lowest faithfulness score | We see LIME perform well upto 40% of feature while the accuracy of DICE model falls drastically till removal of 30% of features | The results were not identical primarily becuase the original solution was using a csv to which we didnt have access to validate and use the data present in it.|
| HPV is the most important risk factor for cervical cancer | All SHAP models primarily rely on 1 feature and that is HPV presence to predict cervical cancer | We too see a similar result where SHAP models heavily depend on 1 feature that is HPV but Surrogates and DICE use 4 to 10 different features to make their predictions | |
| Stability of explanations | LIME, KSHAP and local surrogates are found to be least stable with a lot of variability | LIME, KSHAP and local surrogates are found to be least stable with a lot of variability in our results as well ||
 


#### Ablation Study

1. Carried out different sampling techniques like Random over sampler, SMOTE, using original data and using ADASYN which is mentioned in the paper. We see that random forest, SVM and MLP generally perform well while KNN performs the worst on the given sampled data.
    
2. Used MLP instead of RF as mentioned in paper and we were able to justify similar outcomes when generating the compactness, stability, faithfulness metrics when using RF model


