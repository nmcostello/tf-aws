# Terraform AWS Deployment

## Prerequisite
- An active AWS Account (Free Tier is sufficient)
- Terraform CLI
- AWS CLI

## Overview
The goal of this repo is to create a Terraform manifest that will deploy infrastructure to AWS for a simple data based microservice. The Terraform configuration will create an RDS database, S3 bucket, Lambda function and other necessary infrastructure components. The microservice will pull a sample dataset from a file stored in S3 to RDS and provide an API to view the data.

- Creates a Terraform manifest that will provision an RDS database, S3 bucket, Lambda microservice and other required components for access.
- Writes a Lambda microservice that consumes any files uploaded to a designated S3 bucket and ingests them into an RDS database.
- Writes a Lambda API endpoint that provides a JSON summary of the data, including how many rows are ingested and other useful metrics. If the provided dataset is used, these metrics could look like:
  - row_count: The number of rows in the RDS table for the dataset
  - last_transponder_seen_at: The maximum value for lastseen in the data
  - most_popular_destination: The most commonly seen value for destination
  - count_of_unique_transponders: a unique count of the icao24 field
- Writes a basic shell script that uses the Terraform & AWS CLIs to initialize, provision and deploy these resources. It should will handle uploading the chosen dataset to S3 after completion.

## How to Use
