# TravelTide-Project
An insightful travel analytics project focused on customer segmentation and loyalty programs, utilizing data-driven methods to explore user behavior, travel preferences, and spending patterns.

## Overview
In today's competitive travel industry, customer loyalty is critical for success. The Traveltide project focuses on developing a robust and tailored loyalty program for Traveltide customers by understanding their travel behaviors, preferences, and needs. By utilizing data-driven insights and machine learning techniques, we segmented customers into distinct groups and proposed personalized perks aimed at enhancing customer satisfaction and loyalty.

## Project Goals
- Segment the customer base into meaningful groups based on travel behavior, spending, and demographics.
- Offer strategic recommendations for implementing an effective, data-driven loyalty program at Traveltide.

## Workflow Overview
### 1. Connecting to the Database
The data was retrieved from a PostgreSQL database using SQLAlchemy to establish a connection and perform SQL queries:

import sqlalchemy as sa
import pandas as pd

# Create a connection to the PostgreSQL database
engine = sa.create_engine("postgresql://username:password@host/database")
connection = engine.connect()

# Load the data into pandas DataFrames
users = pd.read_sql_table('users', connection)
hotels = pd.read_sql_table('hotels', connection)
flights = pd.read_sql_table('flights', connection)
sessions = pd.read_sql_table('sessions', connection)

