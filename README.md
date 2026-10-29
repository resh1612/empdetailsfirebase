
# Ex.No:1 To create a employee details fields and to display the employee details using Firebase Database in Android Studio.


## AIM:

To create and display the employee details using Firebase Database in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as HelloWorld and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display the employee details in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the DatabaseTable using the firebasedatabase”.
Developed by: RESHMITHAA B 
Registeration Number : 212224220080
*/
```

## MainActivity.java

```
package com.example.app1;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;

public class MainActivity extends AppCompatActivity {

    EditText nameInput;
    Button saveButton;
    TextView resultText;

    DatabaseReference database;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Connect the XML views
        nameInput = findViewById(R.id.nameInput);
        saveButton = findViewById(R.id.saveButton);
        resultText = findViewById(R.id.resultText);

        // Connect to Firebase Realtime Database
        database = FirebaseDatabase.getInstance()
                .getReference("Students");

        // Save data when the button is clicked
        saveButton.setOnClickListener(v -> {

            String name = nameInput.getText().toString().trim();

            if (name.isEmpty()) {
                nameInput.setError("Please enter a name");
                return;
            }

            database.child("101").child("name")
                    .setValue(name)
                    .addOnSuccessListener(unused -> {
                        resultText.setText("Saved successfully: " + name);
                        Toast.makeText(
                                MainActivity.this,
                                "Data saved to Firebase",
                                Toast.LENGTH_SHORT
                        ).show();
                    })
                    .addOnFailureListener(error -> {
                        Toast.makeText(
                                MainActivity.this,
                                "Error: " + error.getMessage(),
                                Toast.LENGTH_LONG
                        ).show();
                    });
        });
    }
}
```
 ## activity_main.xml 

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp"
    android:gravity="center_horizontal"
    android:background="#FFFFFF">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Firebase Student App"
        android:textSize="25sp"
        android:textStyle="bold"
        android:textColor="#1565C0"
        android:layout_marginTop="40dp"
        android:layout_marginBottom="30dp" />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Enter Student Name"
        android:textSize="16sp"
        android:textColor="#333333"
        android:layout_marginBottom="8dp" />

    <EditText
        android:id="@+id/nameInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name"
        android:inputType="textPersonName"
        android:padding="12dp"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/saveButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Save to Firebase" />

    <TextView
        android:id="@+id/resultText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="16sp"
        android:textColor="#2E7D32"
        android:gravity="center"
        android:layout_marginTop="24dp" />

</LinearLayout>

```

## OUTPUT


<img width="1366" height="768" alt="Screenshot (450)" src="https://github.com/user-attachments/assets/12ab0351-0b61-4710-bb3b-383302297d87" />


<img width="1366" height="768" alt="Screenshot (449)" src="https://github.com/user-attachments/assets/387bd80c-7616-4431-aeea-af2a553d0834" />


<img width="1366" height="768" alt="Screenshot (447)" src="https://github.com/user-attachments/assets/9195128f-d820-453a-96e0-98917c831d93" />



## RESULT
Thus a Simple Android Application create a firebase database and to display the employee details using Firbase Real Time Database in Android Studio is developed and executed successfully.
