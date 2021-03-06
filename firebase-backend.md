
Track your progress:

|Step  | Description | Complexity
| :--- | :---         |     :---:   
|1. |[Android Studio](https://scriptionapp.github.io/scriptionpage1/android-studio)  | Simple
|2. |[Firebase Account](https://scriptionapp.github.io/scriptionpage1/firebase-account) | Simple
|**3.** |[**Firebase Back-end**](https://scriptionapp.github.io/scriptionpage1/firebase-backend) | **Advanced**
|4. |[Firebase Back-end](https://scriptionapp.github.io/scriptionpage1/firebase-backend) | Advanced
|5. |[Distribution](https://scriptionapp.github.io/scriptionpage1/distribution) | Advanced
|6. |[Security](https://scriptionapp.github.io/scriptionpage1/secure-scription) | Advanced
|7. |[Customisation](https://scriptionapp.github.io/scriptionpage1/customisation) | Intermediate

[Home](https://scriptionapp.github.io/scriptionpage1/)



# Firebase Back-End 
A serverless back-end for your Scription app.

## Setting up an email account for PIN reset notifications
1. Follow the steps outlined in [Firebase Account](https://scriptionapp.github.io/scriptionpage1/firebase-account).
2. Go to Google Cloud Dashboard: [https://console.cloud.google.com/home/dashboard] and select your project.
3. Click *Go to project settings* at the bottom of the *Project Info* section of the dashboard.
4. Click on the hamburger menu at the top left and select API & Services > Credentials.
5. Create Credentials and choose OAuth client ID.
6. Select Web Application. Name it (e.g. MyScriptionAppNodemailer). 
7. Under restrictions add [https://developers.google.com/oauthplayground]
8. Save the credentials (ID and secret) somewhere secure. Do not share this online.
9. Go to [https://developers.google.com/oauthplayground] and click the settings icon in the top right. Select "Use your own OAuth credentials" and enter your details: client ID and secret. At the bottom left, under "Select and authorize APIs section" enter https://mail.google.com/ and press "Authorize APIs". On the enxt screen, click the Advanced button and select "Go to Your App’s Name (unsafe)". Click "Allow" and go to Step 2 of the sidebar on the left and press "Exchange authorization code for tokens". Copy down the information you see and save somewhere secure.


## Deploying Firebase functions
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
