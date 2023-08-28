# Find Jobs to find jobs
This repository contains programs to automatically find and collect new job postings based on specified search queries. The programs utilize AWS Lambda functions to query job sites, store results in a database, and populate a Google Sheet with new job links.

# Tech stack
Overview
The repository contains the following key components:
I created two Lambda Functions
### Lambda 1
* Triggers every few hours (configurable cron schedule)
* Runs search queries against job sites like Indeed, LinkedIn, etc.
* Stores any new results in a DynamoDB table
* Only indexes each job link once to avoid duplicates

![Lambda 1](https://github.com/Searching-Jobs/.github/assets/19263085/854ad449-ff33-4e6d-9a35-5729810fed18)

### Lambda 2
* Triggers when the DynamoDB table receives new items
* Retrieves new job links from the table
* Adds the links to a Google Sheet for viewing
* Sorts the sheet so newest links appear at the top

![lambda 2](https://github.com/Searching-Jobs/.github/assets/19263085/0bd1267b-1162-45cc-840c-44f461673fa5)


#### DynamoDB
* Free version comes upto a certain bandwidth limit on AWS
* NoSQL based database which has been programmed to have the links as unique
* Stores list of already indexed job links
* Triggers Lambda 2 when new items are added


I am still thinking of ideas on how to improve this, any ideas are welcome
