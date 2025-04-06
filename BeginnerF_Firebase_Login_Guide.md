# MIT App Inventor Firebase Authentication Guide

This guide provides step-by-step instructions for implementing Firebase Authentication in your MIT App Inventor project.

## Prerequisites

1. A Firebase project with Authentication enabled
2. Access to MIT App Inventor (https://ai2.appinventor.mit.edu/)

## Firebase Configuration

Use the following Firebase configuration values:
- API Key: Your Firebase API Key
- Project ID: Your Firebase Project ID
- App ID: Your Firebase App ID

## Project Setup in MIT App Inventor

### Step 1: Create a New Project

1. Go to MIT App Inventor: https://ai2.appinventor.mit.edu/
2. Create a new project named "BeginnerF"

### Step 2: Design the User Interface

#### Add the following components:

1. **VerticalArrangement (Main Container)**
   - Name: `LoginContainer`
   - Width: Fill parent
   - Height: Fill parent
   - AlignHorizontal: Center
   - AlignVertical: Center

2. **Label (Title)**
   - Name: `TitleLabel`
   - Text: "Firebase Login"
   - TextAlignment: Center
   - FontSize: 24
   - FontBold: True
   - Width: Fill parent

3. **TextBox (Email Input)**
   - Name: `EmailTextBox`
   - Hint: "Enter your email"
   - Width: 300 pixels
   - TextAlignment: Left

4. **TextBox (Password Input)**
   - Name: `PasswordTextBox`
   - Hint: "Enter your password"
   - PasswordVisible: True (this makes the text appear as dots)
   - Width: 300 pixels
   - TextAlignment: Left

5. **Button (Login Button)**
   - Name: `LoginButton`
   - Text: "Login"
   - Width: 200 pixels
   - TextAlignment: Center

6. **Notifier (for feedback)**
   - Name: `Notifier1`
   - (No visible properties to set)

7. **Web (for API calls)**
   - Name: `Web1`
   - (No visible properties to set)

### Step 3: Implement the Login Logic (Blocks)

1. **When LoginButton.Click Event**:
   - Add checks for empty email/password fields
   - Set Web1.Url to: 
     ```
     https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=[YOUR_FIREBASE_API_KEY]
     ```
     (Replace `[YOUR_FIREBASE_API_KEY]` with your actual Firebase API key)
   
   - Set Web1.RequestHeaders to:
     ```
     Content-Type: application/json
     ```
     (Use a "make a list" block with "make a name value pair" block)
   
   - Set Web1.PostText to a JSON string with email and password:
     ```json
     {"email":"[EmailTextBox.Text]","password":"[PasswordTextBox.Text]","returnSecureToken":true}
     ```
     (Use a "join" block and replace placeholders with actual blocks for EmailTextBox.Text and PasswordTextBox.Text)
   
   - Call Web1.PostText to send the request

2. **When Web1.GotText Event**:
   - Check responseCode:
     - If = 200 (success):
       - Parse responseContent (JSON) using Web1.JsonTextDecode to get idToken and localId
       - Show Notifier1.ShowAlert with "Login Successful" message
     - Else (error):
       - Parse responseContent to extract the error message
       - Show Notifier1.ShowAlert with the error message

## Testing the Project

1. Register a test user in Firebase Console:
   - Go to Firebase Console > Authentication > Users > Add User
   - Add a test email and password

2. Test the application:
   - Enter the test credentials in your app
   - Click "Login"
   - Verify that the login is successful and shows the success message

## Troubleshooting

- **Error: "INVALID_PASSWORD"**: This means the password is incorrect.
- **Error: "EMAIL_NOT_FOUND"**: This means the email is not registered.
- **Error: "TOO_MANY_ATTEMPTS_TRY_LATER"**: This means too many failed login attempts. Wait before trying again.

## Next Steps

After successful authentication, you might want to:
1. Store the authentication token for future API calls
2. Navigate to a different screen in your app
3. Load user-specific data from Firebase Realtime Database or Firestore