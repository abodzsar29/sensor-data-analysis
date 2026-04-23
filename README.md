# Sensor Data Analysis

## Andrew Bodzsar - 08.2022

## Overview

This project is a Python script that retrieves sensor data from the Samsara API for a truck and visualizes the results as graphs.

Based on the code in `main.py`, the script works with three kinds of sensor data:
- ambient temperature
- humidity
- door status

The program connects to Samsara endpoints, retrieves historical readings for fixed date ranges, processes the returned values, and plots the results using Matplotlib.

---

## What the Script Does

The script contains two classes:

### `ConnectionTester`
This class is responsible for testing API connectivity.

When initialized, it sends GET requests to the following Samsara sensor endpoints:
- `temperature`
- `humidity`
- `door`
- `list`

It prints the returned JSON responses so the user can inspect whether the sensor data is reachable.

### `DataRetriever`
This class handles historical data retrieval and graphing.

It:
- creates a `ConnectionTester` instance
- retrieves historical temperature data
- retrieves historical humidity data
- retrieves historical door status data
- converts Unix timestamps into date strings
- plots the processed results

---

## Retrieved Data Ranges

The date ranges are hard-coded in the script.

### Temperature and Humidity
The script requests hourly historical values between:
- **2022-06-26 00:00**
- **2022-07-25 00:00**

It then groups the hourly values into daily averages.

### Door Status
The script requests hourly historical values between:
- **2022-06-26 00:00**
- **2022-07-02 23:00**

The returned values are stored as binary door status readings.

---

## Output

Running the script is intended to produce:
- printed API responses from the connectivity test
- a temperature graph
- a humidity graph
- a door status graph

The graphs are displayed with Matplotlib.

---

## Technologies Used

The code imports and uses:
- `requests`
- `json`
- `time`
- `pandas`
- `matplotlib`

---

## Project Files

```text
sensor-data-analysis-main/
├── main.py
└── README.md
````

---

## Running the Project

Install the required Python packages first:

```bash
pip install requests pandas matplotlib
```

Then run:

```bash
python main.py
```

---

## Current Limitation

The script requires a valid Samsara API token, but the token in the source code is a placeholder:

```python
SAMSARA_SENSOR_TOKEN
```

Because of that, the project cannot run successfully without replacing the placeholder with a real token that has access to the relevant Samsara sensor data.


```


