## Infrastructure

This application uses three main AWS services to host it:

1. AWS S3 for hosting the app's frontend built with Angular, which acts as the main entry point to the app that the user can access
2. AWS Elastic Beanstalk for hosting a Nodejs server and handling incoming http requests from the frontend
3. AWS RDS hosting a postgres database which interacts with the server to retrieve data and persist data 

## App Dependencies

- Node v16.14.12 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 8.5.0 (LTS) or more recent

- AWS CLI v2

- EB CLI 3.20.3

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

## Pipeline Process

The pipeline process consists of the following steps:

- A developer makes changes locally and pushes their code to master branch on Github
- The CircleCi workflow listening on changes in the master branch gets triggered
- The workflow has two jobs, a build job and a deploy job. The deploy job is dependent on the build job
- The build job runs first and executes the following scripts
    - Install frontend dependencies
    - Install backend dependencies
    - Build the frontend app
    - Build the backend server
- Upon successfull completion of the build job, the deploy job runs
- The deploy job deploys the frontend build to an AWS S3 bucket