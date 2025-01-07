# Weather Dashboard

A Python application that fetches weather data from OpenWeather API and stores it in AWS S3.

## Features

* Fetches current weather data for multiple cities
* Stores weather data in AWS S3 bucket  
* Displays temperature, feels-like temperature, humidity, and weather conditions
* Automatic S3 bucket creation if not exists

## Prerequisites

* Python 3.6+
* AWS account with appropriate permissions 
* OpenWeather API key

## Installation

1. Clone the repository
2. Install required packages from requirements.txt:
   ```
   pip install -r requirements.txt
   ```

## Configuration

1. Sign up for an OpenWeather API key at: https://openweathermap.org/api
   * Create a free account
   * Navigate to "API Keys" section  
   * Copy your API key

2. Create a `.env` file in the project root with the following variables:
   ```
   OPENWEATHER_API_KEY=your_api_key_here
   AWS_BUCKET_NAME=your_bucket_name_here
   ```

3. Ensure your AWS credentials are configured either via:
   * AWS CLI (`aws configure`)
   * Environment variables
   * IAM role

## Usage

Run the script:
 ```
 python weather-api-app.py
 ```

By default, the script fetches weather data for:
* Philadelphia
* Seattle  
* New York

To modify the cities list, edit the `cities` variable in the `main()` function.

## Output

The script will:
1. Create an S3 bucket if it doesn't exist
2. For each city:
    * Display current weather information in the console
    * Save complete weather data to S3 as JSON file
    * Files are saved with pattern: `weather-data/[city]-[timestamp].json` in the s3 bucket

## Error Handling 

The script includes error handling for:
* API request failures
* S3 bucket creation/access issues
* Data storage problems

## Dependencies

Dependencies are listed in requirements.txt:
* `boto3`: AWS SDK for Python
* `requests`: HTTP library for API calls
* `python-dotenv`: Environment variable management