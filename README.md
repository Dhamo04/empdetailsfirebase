
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

## activity_main.xml:
```
Program to print the DatabaseTable using the firebasedatabase”.
Developed by: DHAMODHARAN S
Registeration Number :212225230049

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/editName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:autofillHints="name"
        android:hint="@string/hint_name"
        android:inputType="textPersonName" />

    <EditText
        android:id="@+id/editAge"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:autofillHints="none"
        android:hint="@string/hint_age"
        android:inputType="number" />

    <Button
        android:id="@+id/buttonSave"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="12dp"
        android:text="@string/btn_save" />

</LinearLayout>

```
## MainActivity.java:
```
package com.example.firebase;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;

import java.util.HashMap;

public class MainActivity extends AppCompatActivity {

    EditText editName, editAge;
    Button buttonSave;
    DatabaseReference dbRef;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editName = findViewById(R.id.editName);
        editAge = findViewById(R.id.editAge);
        buttonSave = findViewById(R.id.buttonSave);

        dbRef = FirebaseDatabase.getInstance().getReference("people");

        buttonSave.setOnClickListener(v -> {
            String name = editName.getText().toString().trim();
            String ageText = editAge.getText().toString().trim();

            if (name.isEmpty() || ageText.isEmpty()) {
                Toast.makeText(this, "Please enter name and age", Toast.LENGTH_SHORT).show();
                return;
            }

            HashMap<String, Object> data = new HashMap<>();
            data.put("name", name);
            data.put("age", Integer.parseInt(ageText));

            dbRef.push().setValue(data)
                    .addOnSuccessListener(a -> {
                        Toast.makeText(this, "Saved!", Toast.LENGTH_SHORT).show();
                        editName.setText("");
                        editAge.setText("");
                    })
                    .addOnFailureListener(e ->
                            Toast.makeText(this, "Failed: " + e.getMessage(), Toast.LENGTH_LONG).show());
        });
    }
}

```




## OUTPUT

<img width="432" height="235" alt="Screenshot 2026-10-22 110154" src="https://github.com/user-attachments/assets/f155b04a-3fe9-4cac-8ea8-2f3b1f2bba8f" />
<img width="1917" height="935" alt="Screenshot 2026-10-22 111341" src="https://github.com/user-attachments/assets/1426efa7-5c7c-4f61-9107-dbeefbf8fbd2" />





## RESULT
Thus a Simple Android Application create a firebase database and to display the employee details using Firbase Real Time Database in Android Studio is developed and executed successfully.
