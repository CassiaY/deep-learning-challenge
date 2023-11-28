# Deep Learning Challenge: Alphabet Soup Charity Funding Predictions  
<font size="3">**Module 21 Challenge**  
**Contributors:** Cassia Yoon  
**Github link:** https://github.com/CassiaY/deep-learning-challenge</font>  

## Project Overview  
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.  
> Assignment prompt is found in [project pdf](/Module_21_Challenge.pdf).  

## Results:  
### Data Processing:  
Sample data:  
![sample of data](/Readme_imgs/original-data-sample.png)  

- What variable(s) are the target(s) for your model?  
The 'IS_SUCCESSFUL' column which states whether the funding resulted in a successful venture or not.
- What variable(s) are the features for your model?  
Application data including:  
    - application type
    - affiliated sector of industry
    - government organization classification
    - use case for funding
    - organization type
    - active status
    - income amount classification
    - special considerations for application
    - funding amount requested.
- What variable(s) should be removed from the input data because they are neither targets nor features?
The EIN and NAME columns which are used just for identification purposes.  

### Compiling, Training, and Evaluating the Model:  
- How many neurons, layers, and activation functions did you select for your neural network model, and why?  
I initially created a model with relu and sigmoid activation and 2 hidden layers (first layer containing 80 nodes and the second one containing 30 nodes). When building the initial model it is recommended to use 2-3 times a many neurons as there are input features. The number of input features was 43, so choosing 80 and 30 neurons was appropriate.  

- Were you able to achieve the target model performance?  
No, the accuracy score was **`72.9%`**.  
![original accuracy score](/Readme_imgs/original-accuracy.png)  

- What steps did you take in your attempts to increase model performance?  
    1. **First Optimization Attempt:** I first edited the preprocessing step by encoding the special considerations column.  
    ![optimization 1 edit](/Readme_imgs/optimization-1-edit.png)  
    The accuracy improved with this edit to **`73.0%`**  
    ![first optimization score](/Readme_imgs/optimization-1-accuracy.png)  

    2. **Second Optimization Attempt:** I then adjusted the model itself by adding a third hidden laye (considers more interactions between variables), increasing the number of neurons(speeds up the model and potentially reduces loss) in the hidden layers, and increasing the epochs (increases change that model will achieve optimal weight coefficients).  
    ![second optimization edit](/Readme_imgs/optimization-2-edit.png)  
    Surprisingly, this decreased the accuracy to a rating to **`72.7%`**, the lowest seen so far. This is likely due to an overfitting problem  
    ![second optimization score](/Readme_imgs/optimization-2-accuracy.png)  

    3. **Third Optimization Attempt:** I then used KerasTuner to try to optimize my model.  
    ![third optimization edit](/Readme_imgs/optimization-3-edit.png)  
    Unfortunately, it was not able to find a model with an accuracy score above 75%.   
    ![third optimization score](/Readme_imgs/optimization-3-accuracy.png)  

## Summary  
Overall, none of the deep learning models tested were able to predict funding success at above a 75% accuracy despite automating optimization. This may be due to an overfitting issue or limited data. I would recommend increasing the training data and also changing the variables so that there is less categorical and more numerical data. For example, instead of recording the income range of an applicant, it would be more benefitial to get an actual number, even if it is a rough estimate. They could collect additional information such as number of employees. I would also recommend trying the SVM (support vector learning) algorithm as it can handle categorical data well according to this [article from techtarget](https://www.techtarget.com/whatis/definition/support-vector-machine-SVM#:~:text=A%20support%20vector%20machine%20(SVM)%20is%20a%20type%20of%20supervised,data%20set%20into%20two%20groups.).  

# Resources  
Dataset: IRS. Tax Exempt Organization Search Bulk Data Downloads. [https://www.irs.gov/](/https://www.irs.gov/charities-nonprofits/tax-exempt-organization-search-bulk-data-downloads).
- How to export keras model:  https://keras.io/guides/serialization_and_saving/

# Acknowledgements
I wish to thank our teaching staff:
- Hunter Hollis
- Sam Espe
- Randy Sendek