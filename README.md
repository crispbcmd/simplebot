# Simplebot
This is a simple Discord bot using free-tier aws services.

# To get started:
## Pre-reqs:
- AWS account for setting up Lambda  
-  Discord Developer Portal  
-  Node.js

### 1. Setup of AWS Lambda:
- Create a Lambda function
- Runtime set to **Node.js**
- Architecture set to **x86_64**
- Open Advanced Settings and check **Enable function URL**
  - Auth type: NONE
  - check Configure cross-origin resource sharing (CORS)
  - leave the rest default

### 2. Setup of Nodejs:  
- On local machine, create a new directory i.e. lambda_files to store **node_modules** as well as **.js** files for Lambda
  - run `npm i tweetnacl`
- Setup your **index.js** and any other files
- Zip within the folder, including node_modules, and upload to Lambda function

### 3. Setup of Discord Application:
> **NOTE:**
> Assign permissions based on the needs of your function, DO NOT grant Administrator.
- Create a new Application
- OAuth2, URL Generator Scopes
  - application.commands
  - bot
- Bot Permissions
    - use slash commands
- from Discord Application, copy the Public Key, into Lambda configuration as an Environment Variable "PUBLIC_KEY"
- from Lambda, copy the function URL, into Discord Interactions Endpoint URL

### 4. Registering Commands:
> **NOTE:**
> use guild_commands for either testing or specific commands related to that discord server 
> and use global commands for slash commands that apply to everything.
- On local machine, create a new directory separate from lambda_files
  - run `npm i axios dotenv`
- update the **.env** file with your BOT TOKEN, APP ID, and GUILD ID
- run `node register.js` script

## Optionals:
If you plan on using DynamoDB run `npm i @aws-sdk/client-dynamodb`

# Addt. Resources:
- https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/welcome.html#welcome_whats_new_v3
- https://discord.com/developers/docs/interactions/application-commands#slash-commands