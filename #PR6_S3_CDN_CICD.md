# PR Contribution to Code Repo

- **PR Link**: [My PR](https://github.com/dishak/Collaborative-code-editor/pull/4)
- **Code Repo**: [Code Repository](https://github.com/dishak/Collaborative-code-editor/tree/s3_cdn_cicd)

## Task: Formulating a CI/CD pipeline for deploying frontend in S3 and backend to EC2 & making the frontend available via CDN of AWS i.e CloudFront

### Description
Frontend is usually served via CDN deploying frontend on S3 V/s Deploying it on EC2 the reason being that when the users hit the website then, every request goes to the server where frontend is hosted causing delay in response time and overload on ther server as to hwere the frontend is hosted to avoid this usually its good to deploy frontend on s3 & access via CDN . Here CDN is like a delivery network of the content and usually also caches the request for some duration to increase data availability and avoid hitting the s3 multiple times for same data.

### Analysis
The CI/CD in the code repo tries to login in using user aws credentials created using IAM from the console. The user in this case is givenn programatic access which in turn has to prove its validity using AWS access key & id. In our case the user is our github action which will login by passing the secrets (access key & id) stored and deploy the react build file from the project to S3 bucket.

### Issue Addressed in PR
- **PR Contribution**: [PR Contribution](https://github.com/dishak/Collaborative-code-editor/pull/4)
