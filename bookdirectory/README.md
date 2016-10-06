o222 Workshop - serverless computing
=============

Bookdirectory
-------

This configurations gives you a simple API with some democontent.

DynamoDB
-------

1. Create a Table Books -> Primary Key: Id (Number) -> No sort key
2. Import data using the Books.json from sampledata -> `aws dynamodb batch-write-item --request-items file://[Path to repository]/bookdirectory/sampledata/Books.json`


IAM
-------

*Role Name*
* o222-bookdirectory

*Role Type*
* API Gateway

*Attach Policy*
* none

*Inline Policy*
* Service: Amazon DynamoDB
* Actions: Scan
* ARN: See in your DynamoDB Config
* Policyname: dynamodb-query

API Gateway
-------

1. Create API
2. API name: o222-bookdirectory
3. Create method: GET
4. Integration type: AWS Service
5. AWS region: your region
6. AWS service: DynamoDB
7. HTTP method: POST (this is not the http method of the api, it's how api gateway communicate with DynamoDB) 
8. Action: Scan
9. Execution role: ARN of o222-bookdirectory - Role
10. Body Mapping Templates: Add mapping template -> application/json -> yes -> Code:  `{ "TableName": "Books" }`
11. Actions -> Deploy API
12. Choose new stage -> prod
13. Deploy
14. Copy Invoke URL in your browser

