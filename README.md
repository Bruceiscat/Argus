# Argus
# ARGUS - AI-Powered OSINT Intelligence Platform

## What It Does
ARGUS is an automated Open Source Intelligence (OSINT) tool that investigates email addresses and aggregates breach data from multiple sources. Instead of manually checking multiple websites, ARGUS provides complete intelligence reports in under 30 seconds.

## Problem It Solves
**Manual Investigation:** Security analysts spend 15-30 minutes per target checking:
- Have I Been Pwned for breach data
- Multiple threat intelligence databases
- Manual copy-pasting results into reports

**ARGUS Solution:** Automated investigation in 30 seconds with all data stored in AWS for future reference.

## Current Features (Week 1)
- ✅ Breach detection via Have I Been Pwned API
- ✅ Automatic data storage in AWS DynamoDB
- ✅ Structured intelligence storage
- 🚧 Query past investigations (Day 3 - in progress)
- 🚧 Multi-source intelligence (Days 4-7 - planned)

## Tech Stack
- **Language:** Python 3
- **Cloud:** AWS (DynamoDB, boto3)
- **APIs:** Have I Been Pwned
- **Security:** Environment variables for API keys

## How To Run

### Prerequisites
```bash
pip install boto3 requests python-dotenv
aws configure  # Set up AWS credentials
```

### Setup
1. Create `.env` file with your API key:
```
API_haveI=your_hibp_api_key_here
```

2. Create DynamoDB table:
```bash
aws dynamodb create-table \
    --table-name argus-targets \
    --attribute-definitions AttributeName=target_id,AttributeType=S \
    --key-schema AttributeName=target_id,KeyType=HASH \
    --billing-mode PAY_PER_REQUEST
```

3. Run ARGUS:
```bash
python argus_complete.py
```

## Example Output
```
Enter Email to investigate: test@adobe.com
Status Code: 200

Found 3 breaches:
- Adobe
- LinkedIn
- AntiPublic

✓ Stored email + breaches in DynamoDB!
```

## Roadmap
- **Week 1:** Multi-source data collection (Shodan, Hunter.io)
- **Week 2-3:** AI analysis and pattern recognition
- **Week 4-6:** Memory system and automated responses
- **Week 7-12:** Production UI and advanced features

## Author
Built by [Your Name] - Cybersecurity Student @ USF
