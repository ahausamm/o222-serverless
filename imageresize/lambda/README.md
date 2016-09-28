o222 Workshop - serverless computing
=============

Imageresize - Lambdafunction
-------

This function automatically resizes an image from the source bucket. After resizing the function uploads the smaller image in the bucket with  "-resized" at the end.

S3
-------

1. Create a bucket
2. Create a bucket with the same name and "-resized" at the end

IAM
-------

*Role Name*
* o222-imageresize

*Role Type*
* AWS Lambda

*Attach Policy*
* AWSLambdaExecute

Lambda
-------

1. Create function
2. Skip blueprint
3. Add Trigger -> S3 -> Select your bucket -> Event "Object created (all)" -> enable trigger
4. Function name: o222-imageresize
5. Upload zipped code
6. Role: Choose existing role -> o222-imageresize
7. Timeout: 10s
8. Create Function

