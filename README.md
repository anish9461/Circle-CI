# Circle-CI-
Circle-CI config files for continuous Integration and deployment

- - - -

## [MQTT-Adapter for armv5](https://github.com/anish9461/Circle-CI-/blob/master/mqtt-adapter-armv5)
This circle CI config file builds a binary in Golang and deploys it to Amazon AWS S3 bucket. The yml file has two workflows, one for building the binary in Docker and then deploying it to the S3 bucket. [mqtt-Adapter for armv5](https://github.com/anish9461/Circle-CI-/blob/master/mqtt-adapter-armv5) can be hooked with a github repository and can be triggered by branch changes.

- - - -

### What is happening in the config file?
- - - -
1. **Build**
    * In the build workflow, the circle CI is accessing its repository to bring in the docker image of the Golang.
    * The working directory is set as mqtt-adapter, attached to a workspace and made persistant so as to have the same workspace between  workflows
    * The checkout configures the git source code to the working directory
    * The MQTT adapter dependencies are installed.
    * The binary is generated for the armv5 architecture.
  
2. **Deploy**
    * The deploy flow uses context to access the environment variables private to the user. ( used for AWS account, Google chats, etc)
    * The binary is deployed from the machine. (In our case, it is linux OS)
    * The working directory and workspace is set for this workflow
    * The contents in the workflow are synced with the AWS S3 bucket
    * There is also chat notification to the user via Google Chats if deployment has succedded or failed
