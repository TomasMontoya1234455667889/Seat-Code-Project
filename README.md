## Project Description: Vehicle Price Prediction Model

### Tackling the Problem
The primary decision in developing our vehicle price prediction model was selecting the most relevant variables. My approach included:

1. **Assessing Variable Viability**: Evaluating each variable's potential to enhance model accuracy and its practicality for user input.
2. **Analyzing Correlations**: For numerical variables like horsepower and mileage, I measured their correlation with vehicle prices. For categorical variables, such as manufacturer, I analyzed average price differences across categories.
3. **Final Variable Selection**: Based on relevancy and ease of user input, I chose the following variables:
   - **Manufacturer**: Different brands significantly impact price (e.g., Dacia vs. Cupra).
   - **Model**: Essential for capturing specific vehicle sub-types.
   - **Transmission**: Another critical categorical variable.
   - **Horsepower (HP)**: Directly correlates with price.
   - **Year**: Reflects the vehicle's age.
   - **Mileage**: Indicates the vehicle's usage.

### The Model
We decided to adopt a hierarchical approach for our prediction model. We use a Linear Mixed Model (LMM) which we use to group the vehicles by Manufacturer, we then used the variables Model & Transmission as our two categorical variables. The other variables used are Horsepower, Year, and Mileage. Through this, we can segregate Manufacturer and Model, furthermore, as we include HP, we can capture the price difference within the model subtypes.

$$
\text{Price} = \beta_0 + \beta_1 \text{Horsepower} + \beta_2 \text{Year} + \beta_3 \text{Mileage} + \beta_4 (\text{Manufacturer}) + \beta_5 (\text{Model}) + \beta_6 (\text{Transmission}) + \beta_7 (\text{Year} \cdot \text{Mileage})
$$

An excellent characteristic of the LMM is its simplicity. As a statistical model, this is extremely advantageous. For one, we can reduce the computing time; furthermore, it’s extremely easy to add, remove, and alter the variables used within the formula. Moreover, we can add interaction terms; in our case, $\beta_7$ explores the interaction between Year and Mileage. 

An important detail to point out is that we added a function in our model to include all unique car models into the train data. This way, we can ensure that the model can be inputted with any of the models in the dataset. For further information on LMM and how they work, reference (Statsmodels, 2023).

### Results
Through this model, we achieved an R² value of 0.89 on an 80-20 split. In addition, we calculated another measure of accuracy (Equation 1, 2). This measure captures the variation between Predicted Price and the Real Price. Using this alternative method, we obtained a mean accuracy of 0.90. 

Figure 2 reveals the variation of accuracy depending on car manufacturer, which shows a lot of consistency amongst all car manufacturers. In other words, the model does a great job at accurately predicting all vehicles regardless of which brand they’re from. 

As of now, we have a working prototype of a website that runs locally, as seen in Figures 3 and 4. In the current version, we manually input the Year of the car, Manufacturer, Mileage, and other relevant details. After all the data has been entered and selected, we either click on the button or press the ‘enter’ button. The website sends the information to a Python script, which runs the model and then returns a prediction value back onto the website.

We want to continue working on this and provide even better insights for users and an overall better user experience. For one, we want to make a better interface, such as shown in Figure 5. Another improvement is to make adjustments to the model, so in instances where the prediction model fails to properly predict the price for certain types of models, we can adjust certain parameters to properly capture the variables and their impact on the price.

---

## Languages and Utilities Used

### Programming Languages
- **Python**: The primary language for developing the model and backend functionality. Python's extensive libraries and frameworks, such as Statsmodels and Pandas, were instrumental in data analysis and model building.
- **HTML/CSS**: For developing the frontend of the prototype website, ensuring a user-friendly and visually appealing interface.
- **JavaScript**: To enhance the interactivity of the website, handling user inputs and communicating with the backend.

### Libraries and Frameworks
- **Statsmodels**: Used for building the Linear Mixed Model (LMM) and performing statistical analysis.
- **Pandas**: Essential for data manipulation and preprocessing.
- **NumPy**: Used for numerical operations and managing arrays.
- **SciPy**: Utilized for additional statistical functions and optimizations.
- **Flask**: A lightweight web framework for Python, used to create the web application backend that processes user inputs and runs the prediction model.
- **Jinja2**: For templating in Flask, enabling dynamic generation of HTML pages.

### Tools and Utilities
- **Jupyter Notebook**: For exploratory data analysis, visualization, and initial model development.
- **Git**: Version control system used to manage the project's source code.
- **GitHub**: Hosting the project repository, facilitating collaboration and version tracking.
- **VS Code**: The primary integrated development environment (IDE) used for coding and debugging.
- **Postman**: Used for testing API endpoints and ensuring seamless communication between frontend and backend.
- **Docker**: Containerization platform to ensure consistent development and deployment environments.

### Data Sources
- **Public Car Datasets**: For obtaining comprehensive data on vehicle specifications and prices.
- **Web Scraping Tools**: Used to collect additional data from various automotive websites.

### Deployment and Hosting
- **Heroku**: Cloud platform used for deploying the web application.
- **AWS**: Amazon Web Services for scalable cloud storage and computing resources, if needed.

### Collaboration and Documentation
- **Slack**: Communication tool for team collaboration.
- **Notion**: For project management, task tracking, and documentation.
- **Google Drive**: For sharing files and collaborative work.

<h2>Appendix</h2>

<p align="center">
Figure 1: <br/>
<img src="https://i.imgur.com/ud6sZjD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Off	Amount = |Price - Predicted	Price| (Equation 1)
Accuracy = 1 − (Off	Amount/Price) (Equation 2


Figure 2:  <br/>
<img src="https://i.imgur.com/99TXSRN.png" height="30%" width="15%" alt="Disk Sanitization Steps"/>
<br />
<br />

Figure 3: <br/>
<img src="https://i.imgur.com/DQabyR8.png" height="30%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />

Figure 4:  <br/>
<img src="https://i.imgur.com/RVsP4Af.png" height="15%" width="30%" alt="Disk Sanitization Steps"/>
<br />
<br />

Figure 5:  <br/>
<img src="https://i.imgur.com/JBRqDEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
References
Linear Mixed Effects Models - statsmodels 0.14.1. (n.d.). 
https://www.statsmodels.org/stable/mixed_linear.htm
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
