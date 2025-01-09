# NBA Game Updates Lambda Function

AWS Lambda function that fetches NBA game data from SportsData.io and sends formatted daily game updates via SNS notifications.

## Prerequisites

* AWS Account
* SportsData.io NBA API key
* Python 3.9+

## Setup Steps

### 1. Create SNS Topic
1. Go to AWS SNS Console
2. Click "Create topic"
3. Select "Standard"
4. Name: `nba-game-updates` (or your preferred name)
5. Create topic
6. Create subscription:
  * Protocol: Email
  * Enter email address
  * Confirm subscription via email

### 2. Create Lambda Function
1. Go to AWS Lambda Console
2. Click "Create function"
3. Select "Author from scratch"
4. Basic settings:
  * Name: `nba-game-updates`
  * Runtime: Python 3.9+
  * Architecture: x86_64
5. Copy the provided code into function
6. Add environment variables in the configuration section under environment:
- `NBA_API_KEY=your_sportsdata_io_api_key`
- `SNS_TOPIC_ARN=your_sns_topic_arn`

### 3. Set Lambda Trigger

1. Add EventBridge (CloudWatch Events) trigger
2. Create new rule:
  * Rule type: Schedule expression
  * Expression: `rate(1 hour)` (or your preferred schedule)

## Testing

1. Use the test feature in Lambda console
2. Create test event with empty JSON:
  ```json
  {}

## Troubleshooting

1. Check CloudWatch logs for errors
2. Verify SNS topic ARN
3. Confirm API key validity
4. Ensure IAM permissions are correctly set for the lambda function