# create-service-accounts
create service accounts (sa)

download mtlb and create a folder "Bot credentials"

# How to create the accounts

## Create credentials.JSON in Google Cloud Console

Go to the Google Cloud Console and if you don't have an existing project, create a new one

Then, enable the google drive api

Go to the OAuth Consent Screen and select "External" and click on "Create"

Fulfill all required informations (the one with a red *) and click on "Save and Continue" 3 times (the "Scopes" and "Test users" parts do not require any inputs) 

Click on publish and confirm

On the credentials tab, click on "Create Credentials" then "OAuth client ID", select "Desktop app"

give any name

Click on the download button on the right of your OAuth Client IDs and save the file with the following name :  credentials.JSON and "Bot credentials" folder


## ENABLE Required API
- Go to console.cloud.google.com/apis/library

--- ENABLE Google Drive API

--- ENABLE Identity and Access Management (IAM) API

## Create Token.Pickle + Token_sa.Pickle + Service Accounts JSON Files from Windows CMD
