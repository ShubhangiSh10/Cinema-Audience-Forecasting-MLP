🎬 Cinema Audience Forecasting using Machine Learning
A time-series forecasting project built for predicting daily theatre audience counts.

📌 Project Overview
This project aims to forecast the daily audience count for multiple cinema theatres using historical booking and visit data. The dataset includes information from two platforms:

BookNow – online ticket booking platform
CinePOS – theatre point-of-sale (POS) bookings

The goal is to predict future audience numbers using past trends, booking activity, and theatre information.

📂 Dataset Description
The project uses the following files:

booknow_visits.csv – Daily audience count (main target)
booknow_booking.csv – Online ticket bookings
cinePOS_booking.csv – On-site ticket sales
booknow_theaters.csv – Details about theatres
movie_theater_id_relation.csv – Mapping between CinePOS & BookNow theatres
date_info.csv – Calendar features (holidays, weekdays)
sample_submission.csv – Required output format

🔍 Exploratory Data Analysis

Some key insights from EDA:

Weekends show higher audience counts.
Booking trends strongly correlate with audience numbers.
Certain theatre types/areas consistently attract more visitors.
Strong patterns exist with lags (previous day/week audiences).

Visualizations used include:
✔ Distribution plots
✔ Trend plots
✔ Boxplots
✔ Monthly audience trends
✔ Correlation heatmaps

🛠 Preprocessing Steps
Merged all datasets on book_theater_id and show_date
Filled missing values for categorical & numeric features
Extracted time-features: weekday, weekend, month, season indicators
Encoded categorical columns using factorization

🚀 Feature Engineering
Created predictive features such as:

Lag features: audience of previous 1, 7, 14, 28 days
Rolling averages for audience trends
Rolling sums of BookNow & CinePOS bookings
Date-based features like day, month, day-of-year
Geographical features: latitude and longitude

🤖 Modeling
Three models were trained and compared:

| Model             | RMSE (Validation) |
| ----------------- | ----------------- |
| **LightGBM**      | ~22.56            |
| **Random Forest** | ~22.54            |
| **XGBoost**       | ~22.19            |

🔁 Recursive Forecasting
For test data:

Start from the last known date of each theatre
Predict the next day’s audience
Update lag & rolling features
Repeat day-by-day until all required dates are predicted
If a theatre has no history, use median fallback.

This ensures predictions follow realistic time-series patterns.
