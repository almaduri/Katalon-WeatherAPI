# Katalon-WeatherAPI
# Weather Forecast and Air Pollution API Testing with Katalon Studio

This repository contains automated test cases for testing the OpenWeatherMap API using Katalon Studio. It includes two main test scenarios:

- **Get 5-Day Weather Forecast** for Jakarta Selatan
- **Get Current Air Pollution** for Jakarta Selatan

This project demonstrates how to use Katalon Studio for API testing, including response validation, JSON schema validation, and assertion of critical response elements. This documentation will guide you through setting up and running the tests, as well as understanding the project structure.

---

## Prerequisites

Before running the tests, ensure you have the following installed:

1. **Katalon Studio** - [Download here](https://www.katalon.com/download/)
2. **Git** - [Download here](https://git-scm.com/downloads)

Make sure you have created an account with OpenWeatherMap to obtain an API key. The free tier limits the number of requests, so you should be cautious of that.

---

## Project Structure

Here's the folder structure of the project:
```
├── Test Cases
│   ├── Get 5-Day Forecast
│   └── Get Current Air Pollution
├── Test Suites
│   ├── WeatherAPISuite
├── Test Objects
│   ├── WeatherForecast
│   └── CurrentAirPollution
├── Include
│   └── resources
│       ├── schema_forecast.json
│       └── schema_pollution.json
├── Reports
│   └── (Generated Reports)
└── .gitignore
```

## How to Set Up the Project

### 1. Clone the Repository

Clone this repository to your local machine:

```
git clone https://github.com/almaduri/Katalon-WeatherAPI.git
```

### 2. Open Katalon Studio

1. Open Katalon Studio.

2. Select **File > Open Project**.

3. Navigate to the cloned repository folder and open the project.

---

### 3. Update API Key

In the test objects `WeatherForecast` and `CurrentAirPollution`, you need to replace the **default API key** with your own OpenWeatherMap API key.

- Open the **WeatherForecast** object from the **Test Objects** folder.
- Find the URL in the **Request** field, and replace the `appid=YOUR_API_KEY` part with your personal API key.

Repeat this for the **CurrentAirPollution** test object.

---

## How to Run the Tests

### Step 1: Running Tests via Katalon Studio UI

1. Open Katalon Studio and go to the **Test Cases** folder.

2. Right-click on the test case you want to run (either **Get 5-Day Forecast** or **Get Current Air Pollution**).

3. Select **Run** to execute the selected test case.

---

### Step 2: Running the Test Suite via Katalon Studio UI

If you want to run the entire test suite instead of individual test cases:

1. Open Katalon Studio and go to the **Test Suites** folder.

2. Right-click on **WeatherAPISuite**.

3. Select **Run** to execute the test suite, which will run both test cases (**Get 5-Day Forecast** and **Get Current Air Pollution**) sequentially.

---

## Test Case Details

### 1. **Get 5-Day Weather Forecast**

#### Test Objective:
Validate the response for a 5-day weather forecast for Jakarta Selatan (Latitude: -6.21462, Longitude: 106.845131).

#### Test Steps:
1. **Send Request**: A GET request is made to the OpenWeatherMap API to retrieve the weather forecast data for Jakarta Selatan.
   - Endpoint: `http://api.openweathermap.org/data/2.5/forecast?lat=-6.21462&lon=106.845131&appid=YOUR_API_KEY`
   
2. **Assertions**:
   - Verify the status code is **200** (success).
   - Verify the response contains `cod: 200` to ensure the request was successful.
   - Verify the `city.name` field contains `"Jakarta"`.
   - Validate the JSON response against the `schema_forecast.json` file.

```
response = WS.sendRequest(findTestObject('WeatherForecast'))

WS.verifyResponseStatusCode(response, 200)
WS.verifyElementPropertyValue(response, 'cod', '200')
WS.verifyElementPropertyValue(response, 'city.name', 'Jakarta')

WS.validateJsonAgainstSchema(response, 'Include/resources/schema_forecast.json')
```

---

### 2. **Get Current Air Pollution**

#### Test Objective:
Validate the response for current air pollution data for Jakarta Selatan.

#### Test Steps:

1. **Send Request**: A GET request is made to the OpenWeatherMap API to retrieve the current air pollution data for Jakarta Selatan.
   - Endpoint: `http://api.openweathermap.org/data/2.5/air_pollution?lat=-6.21462&lon=106.845131&appid=YOUR_API_KEY`
   
2. **Assertions**:
   - Verify the **status code** is **200** (indicating the request was successful).
   - Verify that the `list[0].main.aqi` field contains a valid Air Quality Index (AQI) value, such as `1` for good air quality.
   - Validate the **JSON response** against the `schema_pollution.json` file to ensure the response structure matches expectations.

Example code for **Get Current Air Pollution** test case:

```
response = WS.sendRequest(findTestObject('CurrentAirPollution'))

WS.verifyResponseStatusCode(response, 200)

WS.verifyElementPropertyValue(response, 'list[0].main.aqi', 1)

WS.validateJsonAgainstSchema(response, 'Include/resources/schema_pollution.json')
```

---

## How to View Test Reports

After running the test suite or test case, you can view the generated reports in the **Reports** folder.

### Step 1: Locate the Reports Folder

1. Navigate to the `Reports` folder inside your project directory.

2. Inside the `Reports` folder, you will find a subfolder named with the **current date and time** of the test run. This folder contains the reports for your most recent test execution.

### Step 2: Open the HTML Report

1. Inside the subfolder, locate the **HTML report** file (e.g., `index.html` or a similarly named file).
   
2. Open the HTML report file in your preferred browser to view the test results.

### Step 3: Review the Test Results

The generated report will include the following:

- **Execution Status**: 
   - Pass/Fail indicators for each test case.
   - Information on whether each test was successful or failed.
   
- **Detailed Logs**: 
   - Logs for each test step, showing the requests sent, responses received, and any assertion failures or successes.
   
- **Assertions**:
   - Each assertion made during the test (e.g., verifying the status code, checking specific JSON fields, validating JSON schema) will be shown.
   - Whether each assertion passed or failed.

- **Summary of Test Execution**: 
   - A summary showing how many tests were executed, how many passed, and how many failed. 
   - Overall execution status (e.g., whether the test suite passed or failed).

---

### Example of Test Report Layout

- **Test Suite Overview**:
   - A summary of the test suite with details on the number of test cases executed and the results.
   
- **Test Case Details**:
   - For each test case, you will find:
     - The execution time.
     - The result of each step, including any failures or assertion errors.
     - The response body from the API request.
     
- **Test Logs**:
   - Detailed logs, including requests and responses for every step of the test, are included to help diagnose failures.
  
### Step 4: Analyze Failures

If any tests fail:
- The report will highlight the failed test cases.
- The failure logs will provide information on why the test failed (e.g., assertion errors, timeout issues, incorrect responses).
  
You can use these logs to debug and improve the tests.
