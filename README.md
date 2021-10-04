# Project "Save As" CSV
A Rather Intelligent User Interface that allows user's to save Qualifying Loans as a CSV File.
The gap we are trying to close is to make a lovely and easy to read CSV File that could be created for all new qualifying loans so that it would display an easy to read Spreadsheet and allow for easy record keeping on client loan information. The User can utilize the software to increase productivity by focusing on new clients instead of filtering through client data with is difficult to read.
---


## Technologies
Using Python, we have modular functionality for clean and consice code.
We also utilize libraries to call on company and bank data to make quick corrections as needed.
Operating on Mac OS 10.14 we utilize the latest Operating system to construct the software.
Depending on Jupyter Lab to run and correct our code, Our Developer environment of Anacoda we utilize the most reliable tools!
---


## Installation Guide
MUST PREINSTALL LIBRARIES
pip install fire
pip imstall questionary


#### Important import CODE 
import csv
import sys
import fire
import questionary
from pathlib import Path

from qualifier.utils.fileio import load_csv

from qualifier.utils.calculators import (
    calculate_monthly_debt_ratio,
    calculate_loan_to_value_ratio,
)

from qualifier.filters.max_loan_size import filter_max_loan_size
from qualifier.filters.credit_score import filter_credit_score
from qualifier.filters.debt_to_income import filter_debt_to_income
from qualifier.filters.loan_to_value import filter_loan_to_value
# How Will the User input the DATA?
def get_applicant_info():
    """Prompt dialog to get the applicant's financial information.

    Returns:
        Returns the applicant's financial information.
    """
    # Inquire to user about inoput information regarding client.
    credit_score = questionary.text("What's your credit score?").ask()
    debt = questionary.text("What's your current amount of monthly debt?").ask()
    income = questionary.text("What's your total monthly income?").ask()
    loan_amount = questionary.text("What's your desired loan amount?").ask()
    home_value = questionary.text("What's your home value?").ask()
    # Defining the data type to integer or float.
    credit_score = int(credit_score)
    debt = float(debt)
    income = float(income)
    loan_amount = float(loan_amount)
    home_value = float(home_value)

    return credit_score, debt, income, loan_amount, home_value

# Qualified Loans that are valid and will be approved, Examples From Test Run.
bank_data,credit_score,debt,income,loan,home value
Bank of Big - Starter Plus,300000,0.85,0.39,700,4.35
West Central Credit Union - Starter Plus,300000,0.8,0.44,650,3.9
FHA Fredie Mac - Starter Plus,300000,0.85,0.45,550,4.35
FHA Fannie Mae - Starter Plus,200000,0.9,0.37,630,4.2
General MBS Partners - Starter Plus,300000,0.85,0.36,670,4.05
Bank of Fintech - Starter Plus,100000,0.85,0.47,610,4.5
iBank - Starter Plus,300000,0.9,0.4,620,3.9
Goldman MBS - Starter Plus,100000,0.8,0.43,600,4.35
Prosper MBS - Starter Plus,100000,0.9,0.38,640,3.75
Developers Credit Union - Starter Plus,200000,0.85,0.46,640,4.2
Bank of Stodge & Stiff - Starter Plus,100000,0.8,0.35,680,4.35


---

## SAMPLE OF RAN PROGRAM
(dev) Hus-MacBook-Pro:loan_qualifier_app 
? Enter a file path to a rate-sheet (.csv): data/daily_rate_sheet.csv
? What's your credit score? 700
? What's your current amount of monthly debt? 3000
? What's your total monthly income? 10000
? What's your desired loan amount? 50000
? What's your home value? 150000
The monthly debt to income ratio is 0.30
The loan to value ratio is 0.33.
Found 11 qualifying loans
---

## Contributors
Primary contributor: AbuHorayra Hossain 
Email: Huthedesigner@gmail.com

---

## License
APACHE License 2.0
