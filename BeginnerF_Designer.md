# MIT App Inventor: BeginnerF - Designer View

This document provides detailed instructions for setting up the Designer view of the BeginnerF MIT App Inventor project.

## Screen Properties

1. Set Screen title to "BeginnerF Login"
2. Set Screen's AlignHorizontal property to "Center"
3. Set Screen's ScreenOrientation to "Portrait"

## Component Structure

### 1. VerticalArrangement (Main Container)
- Name: LoginContainer
- Width: Fill parent
- Height: Fill parent
- AlignHorizontal: Center
- AlignVertical: Center

### 2. Label (Title)
- Name: TitleLabel
- Text: "Firebase Login"
- TextAlignment: Center
- FontSize: 24
- FontBold: True
- Width: Fill parent

### 3. TextBox (Email Input)
- Name: EmailTextBox
- Hint: "Enter your email"
- Width: 300 pixels
- TextAlignment: Left

### 4. TextBox (Password Input)
- Name: PasswordTextBox
- Hint: "Enter your password"
- PasswordVisible: True (this makes the text appear as dots)
- Width: 300 pixels
- TextAlignment: Left

### 5. Button (Login Button)
- Name: LoginButton
- Text: "Login"
- Width: 200 pixels
- TextAlignment: Center

### 6. Notifier (for feedback)
- Name: Notifier1
- (No visible properties to set)

### 7. Web (for API calls)
- Name: Web1
- (No visible properties to set)

## Component Hierarchy

