# Project Overview
The goal of this initiative is to set up OAuth integration with Google and Microsoft platforms to gain authorization for accessing user email accounts. Once emails are retrieved, the system will use OpenAI to analyze the content and categorize them into three specific groups: 'Interested', 'Not Interested', and 'Requesting More Information'. Automated email responses will then be generated based on these categories, leveraging OpenAI's capabilities.

## Deployment Links:
- Frontend : https://reachinboxfrontenddemo.netlify.app


## Technologies used:
- **Node.js**: Utilized for backend development.
- **Express.js**: Framework used to build the web application.
- **Google APIs**: Used to interact with the Gmail API for accessing Google email accounts.
- **Microsoft Graph API**: Used to interact with the Outlook API for accessing Outlook email accounts.
- **OpenAI API**: Employed for generating automated responses to emails.
- **BullMQ**: Implemented for queuing emails in the Node.js backend application.
## API Endpoints:

## Google

- ### GET /auth/google
  - To start google oauth process and authenticate users

- ### POST /api/mail/all-draft/:email
  - This endpoint retrieves all draft emails for a specific user. 
```json
{
    "drafts": [
        {
            "id": "",
            "message": {
                "id": "",
                "threadId": ""
            }
        }
    ],
    "resultSizeEstimate": 0
}

```
- ### GET /api/mail/read-mail/:email/message/:messageID
- This HTTP GET request retrieves a specific email message using the provided email address and message ID.  - Example:
```json
GET /api/mail/read-mail/prityss7991@gmail.com/message/18a609755b7af37c

Response:
{
    "id": "18a609755b7af37c",
    "threadId": "18a609755b7af37c",
    "labelIds": [
        "DRAFT"
    ],
    "snippet": "Sent from Mail for Mac",
    "payload": {
        "partId": "",
        "mimeType": "text/html",
        "filename": "",
        "headers": [
            {
                "name": "MIME-Version",
                "value": "1.1.0"
            },
        ],
        "body": {
            "size": 37676,
            "data": ""
        }
    },
    "sizeEstimate": 41916,
    "historyId": "192923",
    "internalDate": "1693837653000"
}
```

- ### POST /api/mail/send-mail
  - This HTTP GET request is used to retrieve a specific email message with the given email address and message ID.
  - Example:
```json

Body:
{
   "from":"cratesium@icloud.com",
   "to":"cratesium@outlook.com",
   "label":"Interested"
}

Response:
{
    "msg": "Email Sent Succesfully",
    "data": {
        "accepted": [
            "cratesium@oicloud.com"
        ],
        "rejected": [],
        "ehlo": [
            "SIZE 35882577",
            "8BITMIME",
            "AUTH LOGIN PLAIN XOAUTH2 PLAIN-CLIENTTOKEN OAUTHBEARER XOAUTH",
            "ENHANCEDSTATUSCODES",
            "PIPELINING",
            "CHUNKING",
            "SMTPUTF8"
        ],
        "envelopeTime": 924,
        "messageTime": 883,
        "messageSize": 2491,
        "response": "250 2.0.0 OK  1711967220 fb11-20020a056a002d8b00b006ecb639fa56sm1240474pfb.217 - gsmtp",
        "envelope": {
            "from": "cratesium@oicloud.com",
            "to": [
                "cratesium@outlook.com"
            ]
        },
        "messageId": "<0366e940-b9f2-1029-21bf-ff8c53150a32@gmail.com>"
    }
}
```

## To explore all the endpoints in details please refer documentation- https://documenter.getpostman.com/view/31788909/2sA35HX1Y1

## Outlook

- ### GET /outlook/list/:email
  - This will fetch all the available mails in user inbox


- ### GET /outlook/read/:email/:messageId
  - This endpoint reads a specific email for a user and generates a reply based on the content of the email.
 
- ### POST /outlookmail/send-email/prity.rastogi02@outlook.com
  - This endpoint is used to send an email to a specific user.
   - Example:
```json
Body:
 - Example:
```json
Body:
{
   "from":"cratesium@icloud.com",
   "to":"cratesium@outlook.com",
   "label":"Interested"
}

Response:
 Email sent successfully
```



