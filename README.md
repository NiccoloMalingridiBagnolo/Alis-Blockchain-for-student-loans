# ALIS - Blockchain for student loans
# INTRODUCTION

In this Repo you will find three main components which constitute the prototype for an Ethereum based peer to peer student loan system. There are two Solidity contracts which will be deployed to the blockchain and one Jupyter notebook where we conduct a machine learning analysis to enable us to price each loan to each student, in the Jupyter notebook one can also find a proof of concept of the envisioned application. Specifically the Jupyter notebook is divided into three segments. The first being the ML analysis and model chioice. The second being a loan pricing analysis and the computation of interet rates and risk ratings for each student. Lastly, the third segment is the application prototype. As a final note, the history of the development of the project can be found in the variuos branches of this repository, where each branch rappresents a different segment of the project, while the final product is located in the master branch.

# SOLIDITY CONTRACTS

## InvestorToken
The first Solidy contract is the InvestorToken. This contract only works in tandem with the second contract, the StudentLoan: a function is provided within the InvestorToken contract which allows one to specify the address of the StudentLoan contract and subsequently interact with it. This is a tradable contract and many instances are envisioned to be in circulation

## StudentLoans
The second Solidy contract is the StudentLoan. This contact will only have one circulating instance, and is responsabile for managing all loan applications, loans, students, and InvestorTokens.

# ALIS JUPYTER NOTEBOOK

## Machine Learning Analysis
In the first section of the Jupyter notebook one can see the machine learning analysis aimed at correctly predicting the defualt rates for each student. We approach this problem by predicting average deafault probability of sutdents in a given college with respect to a set of both student and college characteristics. We try out five different models: a Logistic regression, a Gradient Boosting regression, a K-Nearest Neighbours Regression, a Support Vector Machine and a Random Forest Regression. Finally we settle on Random Forest Regression as it provides us with the most accurate result. Mean absolute error is reported for all five different methods, while model optimization and prediction standard errors are done for the chosen Random Forest Model.

## Pricing
We use the pricing formula from Options, Futures, and Other Derivatives by John C. Hull "Estimating default probabilities from bond yield spreads" Chapter 24.4 and define a function to convert the estimated default rate, which is predicted by the Random Forest Regression to a corresponding interest rate. Default rates are then segmented into ten quantiles, corresponding to ten credist risk ratings.

## Application
The application is designed to be interactive and will reproach you if you try to enter incorrect values such as when asked to input the amount you wish to invest and you spell out 'ten' it will ask for an integer value. To use the prototype the two Solidity contracts need to be deployed to a Blockchain (for example on Ganache via Remix.ide) and the contract addresses stored in the relavent variables in the Notebook. Note more than one InvestorToken can be deployed. Then, using your personal address as Student, Investor, or Buyer, or even better by specifying multiple addresses to play each part one can interactively see how the application supposedly works. The notebook is organized and pre-run in such a way that one can already see an example of this demonstration.

# DATASET
Moreover, a word on the dataset we used to conduct the machine learning analysis.
We decided to use a subset of the College Scorecard dataset provided by the US Department of Education which includes 6,806 institutions and 1,986 variables related to each institution. Below we report the list of chosen variables (out of the 1,986 available ones) with a brief explanation on the meaning of each one:

CDR3: Three-year cohort default rate. We chose this as our response variable.

C150_4 and C150_L4: Proportion of full-time, first-time, degree/certificate-seeking undergraduates who completed a degree or certificate in a four-year and less-than-four-year institution within 150 percent of normal time.

COMPL_RPY_3YR_RT and NONCOM_RPY_3YR_RT: 3-year repayment rate for students who completed and didn’t complete their course of studies.

GRAD_DEBT_MDN: The median debt amount for completers overall.

PCTFLOAN: Percent of all undergraduate students receiving a federal student loan.

MD_EARN_WNE_P8: Median earnings 8 years after entry.

MEDIAN_HH_INC: Median household income.

COUNT_WNE_INC1_P10, COUNT_WNE_INC2_P10 and COUNT_WNE_INC3_P10: Number of students working and not enrolled 10 years after entry in the lowest income tercile USD 0 - 30,000, in the middle income tercile USD 30,001 - 75,000 and in the highest income tercile USD 75,001+.

ICLEVEL: Level of institution (4-year, 2-year or Less-than-2-year).

UGDS: Enrollment of undergraduate certificate/degree-seeking students.

CONTROL: Control of institution (Public, Private nonprofit or Private for-profit).

COSTT4_A and COSTT4_P: Average cost of attendance for academic and program year institutions.

HIGHDEG: Highest degree awarded (Non-degree-granting, Certificate degree, Associate degree, Bachelor's degree, Graduate degree).

# Finally
Specific analysis details are provided as comments and markdowns in the notebook, as well as details concerning the workings of the most important functions.
