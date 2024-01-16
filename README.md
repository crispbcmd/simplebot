# simplebot
This is a simple Discord bot using free-tier aws services.

## Pre-reqs:
1. AWS account for setting up Lambda  
2. Discord Developer Portal  
3. Node.js

## To get started:
- Setup of AWS Lambda:
  - Create a Lambda function
  - Runtime set to **Node.js**
  - Architecture set to **x86_64**
  - Open Advanced Settings and check **Enable function URL**
    - Auth type: NONE
    - check Configure cross-origin resource sharing (CORS)
    - leave the rest default

- Setup of Nodejs:  
  - create a new directory i.e. lambda_files to store **node_modules** as well as **.js** files for Lambda
  - on local machine run `npm i tweetnacl`
  - setup your **index.js** and any other files
  - zip within the folder, including node_modules, and upload to Lambda function

- Setup of Discord Application:
   - Create a new Application
   - from Lambda, copy the function URL, into Interactions Endpoint URL
   - from Discord Application, copy the Public Key, into Lambda configuration as an Environment Variable

- Registering Commands:  
   - on local machine, create a new directory separate from lambda_files
   - run `npm i axios dotenv`
   - update the **.env** file with your BOT TOKEN, APP ID, and GUILD ID
   - run `node register.js` script
      - use guild commands for either testing or specific slash commands related to that discord server
      - use global commands for slash commands that apply to everything

### Optionals:
If you plan on using DynamoDB run `npm i @aws-sdk/client-dynamodb`

## Addt. Resources:
- https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/welcome.html#welcome_whats_new_v3
- https://discord.com/developers/docs/interactions/application-commands#slash-commands