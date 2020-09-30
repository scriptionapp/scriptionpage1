
|Step  | | Complexity
| :--- | :---         |     :---:
|1. |[Home](https://github.com/scriptionapp/scriptionpage1/)  |       
|2. |[Android Studio](https://github.com/scriptionapp/scriptionpage1/android-studio)  | Simple
|3. |[Firebase Account](https://github.com/scriptionapp/scriptionpage1/firebase-account) | Simple
|**4.** |[**Firebase Back-end**](https://github.com/scriptionapp/scriptionpage1/firebase-backend) | **Advanced**
|5. |[Firebase Back-end](https://github.com/scriptionapp/scriptionpage1/firebase-backend) | Advanced
|6. |[Distribution](https://github.com/scriptionapp/scriptionpage1/distribution) | Advanced
|7. |[Security](https://github.com/scriptionapp/scriptionpage1/secure-scription) | Advanced


## Firebase Back-End 
A serverless back-end for your Scription app.

### Setting up an email account for PIN reset notifications
1. Register an account with Google and set up security measures like 2FA.
2. Create a Firebase project for this account.
3. Go to Google Cloud Dashboard: [https://console.cloud.google.com/home/dashboard] and select your project.
4. Click *Go to project settings* at the bottom of the *Project Info* section of the dashboard.
5. Click on the hamburger menu at the top left and select API & Services > Credentials.
6. Create Credentials and choose OAuth client ID.
7. Select Web Application. Name it (e.g. MyScriptionAppNodemailer). 
8. Under restrictions add [https://developers.google.com/oauthplayground]
9. Save the credentials (ID and secret) somewhere secure. Do not share this online.
10. Go to [https://developers.google.com/oauthplayground] and click the settings icon in the top right. Select "Use your own OAuth credentials" and enter your details: client ID and secret. At the bottom left, under "Select and authorize APIs section" enter https://mail.google.com/ and press "Authorize APIs". On the enxt screen, click the Advanced button and select "Go to Your App’s Name (unsafe)". Click "Allow" and go to Step 2 of the sidebar on the left and press "Exchange authorization code for tokens". Copy down the information you see and save somewhere secure.


### Deploying Firebase functions
Prerequisites: Node.js, Firebase CLI.

1. Clone the repository for Scription Firebase Functions.
2. Initialise a Firebase project there (firebase init and select the Firebase project that your Scription app is associated with).
3. cd to folder "functions" and run: 
```
npm install
```
4. In the same folder run these commands:
```
firebase functions:config:set gmail.clientid="your client id"
firebase functions:config:set gmail.clientsecret="your client secret"
firebase functions:config:set gmail.refreshtoken="your refresh token"
firebase functions:config:set gmail.accesstoken="your access token"
```
5. Deploy the Firebase functions by running 
```
firebase deploy --only functions
```
