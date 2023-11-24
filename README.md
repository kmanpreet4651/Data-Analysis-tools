# Data-Analysis-tools

**Introduction
Welcome!**
In this coding, you will learn how to use Python (pandas) for preprocessing your data when Imported from a SQL databease and you will be familiar with the connection methods and how you can run SQL Queries using Python.

**#Import Python Libraries**

import pandas as pd

import numpy as np

# Load the dataset
data1 = pd.read_csv('youtube_dataset.csv', encoding='latin-1')


# Sort the DataFrame by 'Subscribers' column in descending order
data= data1.sort_values(by='subscribers', ascending=False)

# Function to calculate the distribution of channeltype from the top 1000 records
def calculate_channel_distribution(data):
    channel_distribution = data['channeltype'].value_counts(normalize=True)
    return channel_distribution

def load_data_top_1000(data):
    top_1000_data = data.head(1000)
    top_1000_data.to_csv('top_1000_channels.csv', index=False)
    return top_1000_data

# Calculate channel distribution
channel_distribution_result = calculate_channel_distribution(data)
print(channel_distribution_result)

# Call the load_data_top_1000 function
top_1000_data = load_data_top_1000(data)

# Display the loaded DataFrame
top_1000_data.head()

# Display the loaded DataFrame
top_1000_data.head()

data2 = pd.read_csv('top_1000_channels.csv')
data2.head()

# We use the pakage manager pip to install all requred packages
pip install pymysql

# How to create an engine and connect to a database

# import required libraries
import pandas as pd
from sqlalchemy import create_engine
import pymysql

**Build the connection**
In this script, I used Python (pandas) for preprocessing your data when Imported from a SQL database and run SQL Queries using Python.
# create engine
engine = create_engine('mysql+pymysql://root:8699603125@localhost/assignment4')

# connection string
conn = engine.connect()

**Run Simple Queries and read them into a DataFrame**

# read a simple query into DataFrame
df = pd.read_sql("SELECT * FROM assignment4.youtube_dataset", conn)

# print DataFrame
print(df.head())

# Specify the table name in the database
table_name = 'top_1000_channels.csv'

# Write the DataFrame to the MySQL table
data2.to_sql(table_name, con=engine, if_exists='replace', index=False)

Deployment

In order to implement the project, include the given Python script into your data analysis workflow or set it up to execute on a regular basis.

Author
Manpreet Kaur

License
This project is licensed under the MIT License - see the LICENSE.md file for details.
