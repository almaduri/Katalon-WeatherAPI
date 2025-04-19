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
│   ├── WeatherAPI_Tests
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

2. Right-click on **WeatherAPI_Tests**.

3. Select **Run** to execute the test suite, which will run both test cases (**Get 5-Day Forecast** and **Get Current Air Pollution**) sequentially.

---

