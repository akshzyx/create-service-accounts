# **Create Token.Pickle, Token_sa.Pickle & Service Accounts JSON Files**

**Process for creating Token.Pickle, Token_sa.Pickle & Service Accounts JSON Files from Windows CMD.**



# What are service accounts?

A service account is a special kind of account used by an application or compute workload, such as a Compute Engine virtual machine (VM) instance, rather than a person. Applications use service accounts to make authorized API calls, authorized as either the service account itself, or as Google Workspace or Cloud Identity users through domain-wide delegation.

For example, a service account can be attached to a Compute Engine VM, so that applications running on that VM can authenticate as the service account. In addition, the service account can be granted IAM roles that let it access resources. The service account is used as the identity of the application, and the service account's roles control which resources the application can access.

A service account is identified by its email address, which is unique to the account.




# Why are service accounts useful?

The service accounts can be used to bypass the 750Gb/day upload limit set by google in google drive. It means that you can use them to upload more than 750Gb per day, duplicate hundreds of files...

Each service account has a 750Gb upload limit per day. You can create up to 100 service account per google cloud project. So, with only one project you can upload/duplicate up to 75Tb a day! 



# How to create the files

## Download MLTB Repository to your local PC Storage

- open your github account
- [github.com/akshzyx/create-service-accounts](github.com/akshzyx/create-service-accounts) Download ZIP then extract to your PC folder and rename



## Create credentials.JSON in Google Cloud Console

- Go to the Google Cloud Console and if you don't have an existing project, create a new one
- Go to the OAuth Consent Screen and select "External" and click on "Create"
- Fulfill all required informations (the one with a red *) and click on "Save and Continue" 3 times (the "Scopes" and "Test users" parts do not require any inputs)
- Click on publish and confirm
- On the credentials tab, click on "Create Credentials" then "OAuth client ID"
- Select "Desktop app" & assign any name and proceed
- Click on the download button on the right of your OAuth Client IDs and save the file with the following name :  `credentials.JSON` in the "create-service-accounts" folder


## ENABLE Required API
- Go to console.cloud.google.com/apis/library

  --- ENABLE Google Drive API

  --- ENABLE Identity and Access Management (IAM) API
  
  

## Create Token.Pickle + Token_sa.Pickle + Service Accounts JSON Files from Windows CMD

### Install Python in Windows 10 System (FOLLOW this)
- RUN CMD then type Phyton
- Install it from Microsoft Store
- Close CMD

Now
- Open CMD from mltb folder
- Run the following commands

  - `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`

  - `python get-pip.py`

 - Check if pip is installed properly or not. Run the command
   - `pip -V`
 - Check if it shows somethings like this
   > pip 22.1.2 from C:\Users\aksh\AppData\Local\Programs\Python\Python310\lib\site-packages\pip (python 3.10)
 - If not repeat the process
 - When it's installed properly we are good to go


### Generate Token.pickle

- Run the following command
  - `pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib`


- Now run either of the command
 
  - `python3 generate_drive_token.py`

  or
    
    - `python generate_drive_token.py`

