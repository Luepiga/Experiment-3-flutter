EXPERIMENT 3 – ADD INTERACTIVITY TO APP – INPUT AND
FORMS
Aim
To create an interactive Flutter form with input fields and validation.
Step 1
Create project:
flutter create student_form
cd student_form
code .
Step 2
Open:
lib/main.dart
Step 3 – Create Form
Create:
final _formKey = GlobalKey<FormState>();
Step 4 – Add TextFormField
TextFormField(
decoration: const InputDecoration(
labelText: 'Student Name',
),
validator: (value) {
if (value == null || value.isEmpty) {
return 'Enter student name';
}
return null;
},
),
Step 5 – Add email field
TextFormField(
decoration: const InputDecoration(
labelText: 'Email',
),
keyboardType: TextInputType.emailAddress,

),
Step 6 – Add password
TextFormField(
obscureText: true,
decoration: const InputDecoration(
labelText: 'Password',
),
),
Step 7 – Add Submit button
ElevatedButton(
onPressed: () {
if (_formKey.currentState!.validate()) {
ScaffoldMessenger.of(context).showSnackBar(
const SnackBar(
content: Text('Form submitted successfully'),
),
);
}
},
child: const Text('Submit'),
),
Step 8 – Test validation
Click Submit without entering information.
The application should display validation messages.
Expected Result
A working student registration form with:
• Name
• Email
• Password
• Validation
• Submit button how to do this in vs

Step 1 – Open VS Code
1. Open VS Code.
2. Open Terminal → New Terminal.
3. Select PowerShell.
4. Enter the following command:
flutter create student_form


Wait until the project is created.
Step 2 – Open the project
cd student_form
code .


Your project will open in VS Code.
Step 3 – Open main.dart
In VS Code:
1. Open the lib folder.
2. Click main.dart.
3. Delete the existing code.
4. Copy and paste the complete code below.
Step 4 – Complete Python? No, Flutter Dart code
Copy-paste complete code
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: StudentForm(),
    );
  }
}

class StudentForm extends StatelessWidget {
  StudentForm({super.key});

  final _formKey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Student Registration'),
        backgroundColor: Colors.blue,
      ),
      body: Padding(
        padding: const EdgeInsets.all(20),
        child: Form(
          key: _formKey,
          child: Column(
            children: [
              TextFormField(
                decoration: const InputDecoration(
                  labelText: 'Student Name',
                  border: OutlineInputBorder(),
                ),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'Enter student name';
                  }
                  return null;
                },
              ),
              const SizedBox(height: 15),

              TextFormField(
                decoration: const InputDecoration(
                  labelText: 'Email',
                  border: OutlineInputBorder(),
                ),
                keyboardType: TextInputType.emailAddress,
                validator: (value) {
                  if (value == null || !value.contains('@')) {
                    return 'Enter valid email';
                  }
                  return null;
                },
              ),
              const SizedBox(height: 15),

              TextFormField(
                obscureText: true,
                decoration: const InputDecoration(
                  labelText: 'Password',
                  border: OutlineInputBorder(),
                ),
                validator: (value) {
                  if (value == null || value.length < 6) {
                    return 'Password must be 6 characters';
                  }
                  return null;
                },
              ),
              const SizedBox(height: 20),

              ElevatedButton(
                onPressed: () {
                  if (_formKey.currentState!.validate()) {
                    ScaffoldMessenger.of(context).showSnackBar(
                      const SnackBar(
                        content: Text('Form submitted successfully'),
                      ),
                    );
                  }
                },
                child: const Text('Submit'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}


Step 5 – Run the Flutter application
Open the VS Code terminal and type:
flutter run


If you want to run it in Chrome:
flutter run -d chrome


If Chrome is not enabled, run:
flutter config --enable-web
flutter create .
flutter run -d chrome
