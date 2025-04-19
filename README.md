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

