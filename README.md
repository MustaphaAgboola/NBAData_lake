# Building an NBA Analytics Data Lake with AWS Services

## Overview
This project demonstrates how to build a serverless data lake for NBA analytics using AWS services and the SportsData.io API. The solution automatically fetches NBA player data, stores it in S3, and makes it queryable through AWS Athena.

## Architecture
The system uses several AWS services:
- **Amazon S3**: Raw data storage
- **AWS Glue**: Data catalog and metadata management
- **Amazon Athena**: SQL query service for data analysis
- **SportsData.io API**: Source for NBA player data

## Prerequisites

### AWS Setup
1. AWS Account with appropriate permissions
2. AWS CLI installed and configured
3. Access to S3, Glue, and Athena services

### API Access
1. SportsData.io API key
2. NBA endpoint access

### Python Environment
```bash
# Install required packages
pip install -r requirements.txt
```

## Project Structure

### Environment Configuration
Create a `.env` file:
```
SPORTS_DATA_API_KEY=your_api_key_here
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
```

## Implementation Steps

1. **Install Dependencies**
```bash
pip install -r requirements.txt
```

2. **Configure Environment**
   - Set up AWS credentials
   - Create `.env` file with API keys
   - Verify service access

3. **Run the Application**
```bash
python nba_datalake.py
```

### Main Components

1. **S3 Bucket Creation**
   - Creates a dedicated bucket for NBA data
   - Handles regional configurations
   - Ensures proper data storage organization

2. **Glue Database Setup**
   - Creates a metadata database
   - Defines table schema for NBA player data
   - Enables data catalog functionality

3. **Data Pipeline**
   - Fetches NBA player data from API
   - Processes data into line-delimited JSON
   - Uploads to S3 in organized structure

4. **Athena Configuration**
   - Sets up query capabilities
   - Configures output location
   - Enables SQL-based analysis

## Data Schema
```sql
CREATE TABLE nba_players (
    PlayerID int,
    FirstName string,
    LastName string,
    Team string,
    Position string,
    Points int
)
```

## Future Enhancements
1. Add data transformation capabilities
2. Implement automated scheduling
3. Add more sports data sources
4. Create visualization layer
5. Add real-time data processing

## Benefits
- **Scalability**: Handles growing data volumes
- **Cost-Effective**: Pay-per-use AWS services
- **Queryable**: SQL access to sports data
- **Maintainable**: Serverless architecture
- **Extensible**: Easy to add new data sources

## Conclusion
This project provides a foundation for building a comprehensive sports analytics platform. By leveraging AWS services and modern data lake architecture, it enables efficient storage and analysis of NBA player data while maintaining flexibility for future enhancements.

## Resources
- [AWS Documentation](https://docs.aws.amazon.com/)
- [SportsData.io API Docs](https://sportsdata.io/developers/api-documentation/nba)
- [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
- [DevOpsAllStarsChallenge](https://youtu.be/RAkMac2QgjM?si=176AlkYqCxR_v5wl)