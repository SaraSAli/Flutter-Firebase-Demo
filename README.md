# Flutter Firebase Services (Authentication — Login & Register App)

## Features
* User Registration (Email & Password)
* User Login (Email & Password)
* Firebase Authentication
* Form validation
* Error handling (wrong credentials, weak password, etc.)
* Clean and simple UI
* Firebase Initialization through ``` firebase_core ``` + ``` firebase_options.dart ```

## Project Setup
1. Install Firebase CLI
   Download from the official installer:
   ```
   https://firebase.tools/bin/win/latest
   ```
   Log in:
   ```
   firebase login
   ```

2. Install FlutterFire CLI
   ```
   dart pub global activate flutterfire_cli
   ```
4. Configure Firebase for your project
   Inside your Flutter project folder:
   ```
   flutterfire configure --project=YOUR_PROJECT_ID
    ```
   This will generate:
   ```
   lib/firebase_options.dart
    ```

## Add Required Dependencies
Inside pubspec.yaml:
```
   dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^2.24.2
  firebase_auth: ^4.16.0
```

Run:
 ```
flutter pub get
```

## Firebase Initialization (main.dart)

```
void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
```

## Login Code Snippet (login_screen.dart)
```
  Future<void> login() async {
    try {
      await FirebaseAuth.instance.signInWithEmailAndPassword(
        email: emailController.text.trim(),
        password: passwordController.text.trim(),
      );
      print("Login Successfully");
    } catch (e) {
      print("Login Error: $e");
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text(e.toString())),
      );
    }
  }
```

## Registration Code Snippet (register_screen.dart)
```
  Future<void> register() async {
    try {
      await FirebaseAuth.instance.createUserWithEmailAndPassword(
        email: emailController.text.trim(),
        password: passwordController.text.trim(),
      );
      print("Account Created Successfully");
    } catch (e) {
      print("Registration Error: $e");
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text(e.toString())),
      );
    }
  }
```

