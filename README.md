# ReachInBox Assignment

## Overview

The ReachInBox assignment aims to build a tool that parses and manages emails from Google and Outlook accounts, using AI to categorize and respond to emails based on their context. This server-based application is built with Node.js and Express, leveraging various APIs and AI services.

![image](https://github.com/Tech-Spookezz/ReachInbox.AI/assets/114910171/442c1ba3-a942-452f-b220-c34fd465f458)


## Technologies Used

- **Node.js**
- **Express.js**
- **OpenAI**
- **Google APIs**
- **Microsoft Graph API**

## npm Packages Used

- **dotenv**: For managing environment variables.
- **axios**: For making HTTP requests.
- **bullMQ**: For task scheduling and processing queues.
- **google-auth-library**: For integrating Google OAuth2.0.
- **ioredis**: Redis client for Node.js.
- **@microsoft/microsoft-graph-client**: Microsoft Graph API client library.
- **@azure/msal-node**: Microsoft Authentication Library (MSAL) for Node.js.

## Installation and Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/shraddha-gawde/reachInbox-assignment.git
   cd reachInbox-assignment/server
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Set Environment Variables:**
   Create a `.env` file in the root directory with the following environment variables:
   ```
   PORT=***
   GOOGLE_CLIENT_ID=***
   GOOGLE_CLIENT_SECRET=***
   GOOGLE_REDIRECT_URI=***
   GOOGLE_REFRESH_TOKEN=***
   OPENAI_API_KEY=***
   redis_port=***
   redis_host=***
   redis_pass=***
   AZURE_CLIENT_ID=***
   AZURE_CLIENT_SECRET=***
   AZURE_TENANT_ID=***
   ```

4. **Run the Server:**
   ```bash
   npm start
   ```

5. **Start the Worker:**
   ```bash
   npm run server
   ```

## API Endpoints

### Google's OAuth2.0:

- **GET** `/auth/google`: Google authentication.
- **GET** `/api/mail/userInfo/:email`: Retrieve user profile information.
- **GET** `/api/mail/allDrafts/:email`: Get all draft emails.
- **GET** `/api/mail/read/:email/message/:message`: Read a specific email by ID.
- **GET** `/api/mail/list/:email`: Get a list of emails.
- **POST** `/api/mail/sendMail`: Send an email with a specified label.
  
  ```json
  {
      "from": "sender@example.com",
      "to": "recipient@example.com",
      "label": "interested/not-interested/more-information"
  }
  ```
- **POST** `/api/mail/sendone/:id`: Send a single email by ID.
  
  ```json
  {
      "from": "sender@example.com",
      "to": "recipient@example.com"
  }
  ```
- **POST** `/api/mail/sendMultiple/:id`: Send an email to multiple recipients by ID.
  
  ```json
  {
      "from": "sender@example.com",
      "to": ["recipient1@example.com", "recipient2@example.com"]
  }
  ```

### Microsoft Azure's OAuth2.0:

- **GET** `/outlook/signin`: Microsoft Azure authentication for Outlook.
- **GET** `/outlook/callback`: Callback for obtaining access tokens.
- **GET** `/outlook/profile`: Get user profile data.
- **GET** `/outlook/all-Mails/:email`: Get all mails of a user.
- **GET** `/outlook/:email/read-Msg/:message`: Read a specific mail by message ID.
- **POST** `/outlook/:email/send-Mail`: Send an email using Outlook.
  
  ```json
  {
      "from": "sender@example.com",
      "to": "recipient@example.com",
      "label": "interested/not-interested/more-information"
  }
  ```
- **POST** `/outlook/sendone/:email/:id`: Send a single email using Outlook with BullMQ.
  
  ```json
  {
      "from": "sender@example.com",
      "to": "recipient@example.com"
  }
  ```

## Additional Links

- **Backend:** [Link](https://documenter.getpostman.com/view/36543316/2sA3dskDUB)
- **API Documentation:** [Link](https://documenter.getpostman.com/view/36543316/2sA3dskDUB)
