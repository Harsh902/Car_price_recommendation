# Car Price Recommendation System

Original dataset taken from kaggle.com: [Dataset](https://www.kaggle.com/datasets/sukhmanibedi/cars4u)

Cleaned dataset suitable for GUI: [Dataset](https://github.com/Harsh902/Car_price_recommendation/blob/main/used_cars_data_cleaned.csv)

Dataset suitable for model training: [Dataset](https://github.com/Harsh902/Car_price_recommendation/blob/main/cardata_numerized.csv)
## Project Description
My project is designed to help users from India predict the approximate price of a used car according to their preferences.

## Prerequisites

| Name | Version |
| ------ | ------ |
| Python | 3.11.4|
| PyQt6  | 6.6.1   |
| Matplotlib | 3.8.2|
| numpy  | 1.26.3   |
| pandas | 2.1.4|
| scikit-learn | 1.3.2|
| used_cars_data_cleaned | [link](https://github.com/Harsh902/Car_price_recommendation/blob/main/used_cars_data_cleaned.csv)|
| cardata_numerized | [link](https://github.com/Harsh902/Car_price_recommendation/blob/main/cardata_numerized.csv)|

## Installation
Please download [*main.py*](https://github.com/Harsh902/Car_price_recommendation/blob/main/main.py), [*cardata_numerized.csv*](https://github.com/Harsh902/Car_price_recommendation/blob/main/cardata_numerized.csv) and [*used_cars_data_cleaned.csv*](https://github.com/Harsh902/Car_price_recommendation/blob/main/used_car_data_cleaned.csv) files into the same folder. \
The whole project can also be downloaded as a zip file.

Please install all of the required libraries to run the program successfully.

### Virtual Environments
If you use an IDE such as PyCharm, a virtual environment will be created automatically. \
Otherwise, you can create a virtual environment using the following commands: 

****For Windows**:**

    python -m venv /path/to/new/virtual/environment

****For Linux + macOS**:**

    (venv) $ python -m pip install <package-name>

Once you have created a virtual environment, you must activate it, before installing the packages.

****Windows**:**

    PS> venv\Scripts\activate
    (venv) PS>

****Linux + macOS**:**

    $ source venv/bin/activate
    (venv) $

You can then install the packages:

**Windows:**

    (venv) PS> python -m pip install <package-name>

**Linux + macOS:**

    (venv) $ python -m pip install <package-name>

You can find more information here: 
- [Official Documentation For Virtual Environments in Python](https://docs.python.org/3/library/venv.html) 
- [Virtual Environments Tutorial - RealPython](https://realpython.com/python-virtual-environments-a-primer/#how-can-you-customize-a-virtual-environment) (Personal login required)

## Basic Usage

1. Please run the main.py file.

2. After the application is running, the data file is read after clicking on the 'Start Analisys' button.

- The predicted price for default inputs is shown.
- The 'Start Analisys' button is disabled, and its text is set to 'Interactive Analisys Started'.

3. Custom values can be submitted using various widgets.
- The plot reacts interactively to the input and gives a prediction.

4. The modified price is displayed on the plot, and on the text section above the 'Interactive Analisys Started' button.

> Note: Price is displayed in Euros and in lakhs on the plot.\
1 lakh Indian rupees = ~1000 Euros.

5. Additionally, the user can view some trends on the data using the buttons on the right of the plot canvas.
The text above them explains the plot.

6. Save button stores the plot in ".png" format at user's specified location.
- In case of unsaved data, the "quit button" asks for confirmation before closing.

## Implementation of the Requests

### Graphical User Interface (GUI)

#### Data Import
I import the data in our code using the "pandas.read_csv" method in the *generate_model* method.

#### Data Reading And Analysis
The data is analyzed after clicking on the "Start Analysis" button.

#### Input Widgets And Statistical Metrics
I use 3 different types of input widgets for 8 statistical metrics:
- QComboBox:
    - transmission_type: maps the transmission type of the car to our *prediction function*
    - fuel_type : maps the kind of fuel used to the *prediction function*
    - brand_class: maps the brand of the car to the *prediction function*
- QSpinbox:
    - power: maps the power of the car to our *prediction function*
    - kmd : maps the number of kilometers the car was used for to the *prediction function*
    - engine : maps the strength of the ca engine to the *prediction function*
- QSlider:
    - age_slider: maps the age of the car to the *prediction function*
    - seat_no: maps the number of seats in the car to the *prediction function*

The *prediction function* is called "show_prediction"

### Visualization And Data Overview For User
To implement this part we used Matplotlib 3.8.2 library and integrate it in PyQt6.
There are 6 plots available for user:
- Main plot with Year Vs Price of car
- Fuel Type Vs Average Mileage,
- Number Of Seats Vs Average Price
- Owner Type Vs Average Price
- Transmission Distribution
- Seats Number Distribution

### Data Analysis With Pandas and Numpy
To implement this part I used pandas 2.1.4, numpy 1.26.3 and scikit-learn 1.3.2 libraries.

Biggest part of this section was done during the dataset cleaning and exploration:
- data was observed
- otliers were removed
- during data exploration the left-skewed pattern of price and kilometer distribution were founded; it is the reason why log price and log km was used for model training and prediction

The part of data analysis which is available for user was done usimg 
pandas.describe(), pandars.info() libraries and scikit-learn functions m mean_squared_error() and r2_score()

### Scikit-Learn 
This section was implemented using LinearRegression class form scikit-learn library.

I split the dataset from "used_cars_dataset_cleaned.csv" file into 4 parts: X, y for training the model and X, y for testing the model. 
- X_train - 70% of rows from all columns except "Price_log"
- X_test - remaining 30% of rows from all columns except "Price_log"
- y_train - corresponding 70% of rows from "Price_log" column. Using it as a labels for model
- y_test - corresponding 30% of rows from "Price_log" column. Using it to measere the accurcy of our model

Mean squared error is equal to 0.1, which could be called a good result.

## Work Done
This project involved me doing the following tasks:
- GUI
- Integration of Matplotlib in PyQt6
- Dataset cleaning, exploration and description.
- Scikit-Learn
- Data analisys and plotting of:
    - Age Of Car Vs Price,
    - Fuel Type Vs Mileage,
    - Number Of Seats Vs Price
    - Owner Type Vs Price
    - Transmission Distribution
    - Seats Number Distribution
