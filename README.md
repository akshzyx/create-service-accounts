# Here We Go

- **Process for creating _Token.Pickle_, _Token_sa.Pickle_ & _Service Accounts_ JSON Files from Windows CMD.** 

- **Also adding service accounts into a Shared Drive (Team Drive)**



# What are service accounts?

A [service account](https://cloud.google.com/iam/docs/service-accounts) is a special kind of account used by an application or compute workload, such as a Compute Engine virtual machine (VM) instance, rather than a person. Applications use service accounts to make authorized API calls, authorized as either the service account itself, or as Google Workspace or Cloud Identity users through domain-wide delegation.

For example, a service account can be attached to a Compute Engine VM, so that applications running on that VM can authenticate as the service account. In addition, the service account can be granted IAM roles that let it access resources. The service account is used as the identity of the application, and the service account's roles control which resources the application can access.

A service account is identified by its email address, which is unique to the account.




# Why are service accounts useful?

The service accounts can be used to bypass the 750Gb/day upload limit set by google in google drive. It means that you can use them to upload more than 750Gb per day, duplicate hundreds of files...

Each service account has a 750Gb upload limit per day. You can create up to 100 service account per google cloud project. So, with only one project you can upload/duplicate up to 75Tb a day! 



# How to create the files

## Download "create-service-accounts" Repository to your local PC Storage

- open your github account
- [github.com/akshzyx/create-service-accounts](https://github.com/akshzyx/create-service-accounts) download ZIP then extract to your PC folder







## Create credentials.JSON in Google Cloud Console

- Go to the [Google Cloud Console](https://console.cloud.google.com/) and if you don't have an existing project, create a new one
- Go to the [OAuth Consent Screen](https://console.cloud.google.com/apis/credentials/consent) and select "External" and click on "Create"
- Fulfill all required informations (the one with a red *) and click on "Save and Continue" 3 times (the "Scopes" and "Test users" parts do not require any inputs)
- Click on publish app and confirm
- On the [credentials](https://console.cloud.google.com/apis/credentials) tab, click on "Create Credentials" then "OAuth client ID"
- Select "Desktop app" & assign any name and proceed
- Click on the download button on the right of your OAuth Client IDs and save the file with the following name :  `credentials.JSON` in the "create-service-accounts" folder



## ENABLE Required API

  - Go to [console.cloud.google.com/apis/library](https://console.cloud.google.com/apis/library)

  - ENABLE Google Drive API

  - ENABLE Identity and Access Management (IAM) API
  

## Create Token.Pickle + Token_sa.Pickle + Service Accounts JSON Files from Windows CMD

### Install Python in Windows 10 System (FOLLOW this)
- RUN CMD then type Phyton
- Install it from Microsoft Store
- Close CMD

Now
- Open CMD from create-service-accounts folder 
 
   >click on the "This PC > New Volume (F) > create-service-accounts" something like this at the top then type "cmd" there and press enter


- Run the following commands

  - `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`

  - `python get-pip.py`

 - Check if pip is installed properly or not. Run the command
   - `pip -V`
<!--  - Check if it shows somethings like this
   > pip 22.1.2 from C:\Users\aksh\AppData\Local\Programs\Python\Python310\lib\site-packages\pip (python 3.10)
 - If not repeat the process -->
 
 - When it's installed properly we are good to go


### Generate Token.pickle

- Run the following command
  - `pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib`


- Now run either of the command
 
  - `python3 generate_drive_token.py`

  or
    
    - `python generate_drive_token.py`

 - Now copy paste the URL in browser for authentication

Now you would see **Token.pickle** saved in your folder



### Generate Token_sa.pickle + SA Accounts folder


- Run the following command
  - `python -m pip install progress`


- Now run either of the command
 
  - `python3 gen_sa_accounts.py --quick-setup 1 --new-only`

  or
    
    - `python gen_sa_accounts.py --quick-setup 1 --new-only`

 - Now copy paste the URL in browser for authentication

Now you would see **SAs (service accounts) folder and token_sa.pickle** saved in your folder



### Creating the service accounts

- Open POWERSHELL from the "accounts" folder

>click on the "This PC > New Volume (F) > create-service-accounts > accounts" something like this at the top then type "POWERSHELL" there and press enter

- Copy Paste this command 
   - Windows users
     - `$emails = Get-ChildItem .\**.json |Get-Content -Raw |ConvertFrom-Json |Select -ExpandProperty client_email >>emails.txt`

   - Linux / MacOs users 
     - `grep -oPh '"client_email": "\K[^"]+' *.json > emails.txt`

- After completion you'll see a text document "emails" in the "accounts" folder
- Open the text document "emails" and you'll have your service accounts



## Add Service Account to SHARED DRIVE / TEAM DRIVE

In order to manage the files (copy, duplicate...) into your shared drives with the service accounts, you must create a google group 

- Go to [groups.google.com](https://groups.google.com/)

- create a new group (configure it as you wish) [DON'T add SA in the 3rd step while creating group]

- open your group, go to members tab and press 'Add Members'

- Copy all mails from \accounts\emails.txt and paste in 'Group members' field, then press 'Add Members'

- Now go to your SHARED DRIVE / TEAM DRIVE & add your google group email address (it will be something like blahblah@googlegroups.com) to your team drive !
  - It's Upto you whether to add google group as 'Content Manager', 'Viewer' etc...

## If you don't have SHARED DRIVE / TEAM DRIVE

   - **Create one here - [https://td.msgsuite.workers.dev](https://td.msgsuite.workers.dev)**
