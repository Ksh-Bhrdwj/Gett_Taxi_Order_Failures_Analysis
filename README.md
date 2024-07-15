# Gett Taxi Order Failures Analysis

## Introduction

This project analyzes and visualizes the reasons and patterns behind failed taxi orders for the Gett platform. The goal is to understand why orders are not completed successfully and identify trends in cancellations and order rejections.

## Objectives

1. **Distribution of Orders by Failure Reason**:
   - Categorize the reasons for order failures, including client cancellations before and after driver assignment, and system cancellations (order rejections).

2. **Distribution of Failed Orders by Hour**:
   - Analyze the distribution of failed orders by hour to identify any trends or patterns.

3. **Average Time to Cancellation by Hour**:
   - Plot the average time to cancellation, distinguishing between orders with and without a driver assigned, and identify any hourly trends.

4. **Distribution of Average ETA by Hour**:
   - Examine the distribution of average Estimated Time of Arrival (ETA) by hour.

5. **Geographical Distribution of Failed Orders (Bonus)**:
   - Visualize the geographical distribution of failed orders using hexagons, focusing on areas with the highest failure rates.

## Data Description

The project utilizes two datasets:
- **data_orders**:
  - `order_datetime`: Time of the order.
  - `origin_longitude`: Longitude of the order.
  - `origin_latitude`: Latitude of the order.
  - `m_order_eta`: Estimated time of arrival.
  - `order_gk`: Order number.
  - `order_status_key`: Status (4 - cancelled by client, 9 - cancelled by system).
  - `is_driver_assigned_key`: Whether a driver was assigned (1 - Yes, 0 - No).
  - `cancellations_time_in_seconds`: Time in seconds before cancellation.

- **data_offers**:
  - `order_gk`: Order number.
  - `offer_id`: ID of an offer.

## Key Findings

1. **Distribution of Orders by Failure Reason**:
   - The highest number of failed orders occurred due to clients canceling before a driver was assigned.
   - System cancellations and client cancellations after a driver was assigned were also significant.

2. **Distribution of Failed Orders by Hour**:
   - Failure rates peaked around midnight and early morning hours.
   - Higher failure rates were observed during late evening hours as well.

3. **Average Time to Cancellation by Hour**:
   - Cancellations took longer when a driver was assigned, averaging 120 to 140 seconds.
   - Without a driver, cancellations generally fluctuated around 90 to 110 seconds.

4. **Distribution of Average ETA by Hour**:
   - The lowest average ETA was during early morning hours.
   - Significant increases in ETA were observed during morning peak hours.

5. **Geographical Distribution of Failed Orders**:
   - Using H3 and Folium, hexagons containing 80% of all failed orders were identified and mapped.

## Recommendations

- **Demand Management**: Implement strategies to manage peak hour demand to reduce client cancellations.
- **Driver Availability**: Ensure sufficient driver availability during peak times to improve order acceptance rates and reduce system cancellations.
- **ETA Optimization**: Optimize ETAs during high-demand periods to enhance customer satisfaction and reduce cancellations.

## Usage

To run the analysis, load the provided datasets and execute the Jupyter notebook. The notebook performs the following steps:
1. Loads and inspects the data.
2. Analyzes the distribution of orders by failure reason.
3. Plots the distribution of failed orders by hour.
4. Calculates and plots the average time to cancellation by hour.
5. Examines the distribution of average ETA by hour.
6. (Bonus) Visualizes the geographical distribution of failed orders using H3 and Folium.

## Installation

To run this project, you need the following Python packages:
- `pandas`
- `matplotlib`
- `h3`
- `folium`

Install them using pip:
```sh
pip install pandas matplotlib h3 folium
