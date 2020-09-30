# Setting up an email account that will be sending PIN reset notifications

Comment: I recommend to have a separate email account for this functionality for security purposes.

1. Register an account with Google and set up security measures like 2FA.
2. Create a Firebase project for this account.
3. Go to Google Cloud Dashboard: https://console.cloud.google.com/home/dashboard and select your project
4. Click *Go to project settings* at the bottom of the *Project Info* section of the dashboard.
5. Click on the hamburger menu at the top left > API & Service > Credentials
6. Create Credentials and choose OAuth client ID
7. Select Web Application. Name it (e.g. LegalAppNodemailer). 
8. Under restrictions add https://developers.google.com/oauthplayground
9. Save the credentials (ID and secret) somewhere secure. Do not share this online.
10. Go to https://developers.google.com/oauthplayground and click the tools icon in the top right. Check the box that says Use your own OAuth credentials and enter your client ID and secret. Without closing out of the settings, enter https://mail.google.com/ into the box in the Select and authorize APIs section and press Authorize APIs. You should get a very scary-looking screen.
Nothing to worry about, this just means Google hasn’t confirmed our app is okay to use (duh, we just made it). Click the Advanced button on the left and then press Go to Your App’s Name (unsafe). We get another, less intimidating screen.
Click Allow and you should get redirected back to the OAuth page. Now go to Step 2 of the sidebar on the left and press Exchange authorization code for tokens.
This should populate the two boxes below called Refresh token and Access token with a couple of strings. Copy down the Refresh token as we’ll need it for later!
11. npm install googleapis
12. It is generally not a good practic to store yuor secters hard-coded, so do the following:
using Firebase CLI:

firebase functions:config:set gmail.clientid="your client id"
firebase functions:config:set gmail.clientsecret="your client secret"
firebase functions:config:set gmail.refreshtoken="your refresh token"
firebase functions:config:set gmail.accesstoken="your access token"
