# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Step 1: Create a New Project in Android Studio

Step 2: Working with the activity_main.xml File

Step 3: Working with the MainActivity File

Step 4: Working with the activity_main2.xml File

Step 5: Working with the MainActivity2 File


## PROGRAM:
```
/*
Program to find the factorial of a number using explicit intent.
Developed by: Sabitha P
Registeration Number : 212222040137
*/
```
### In activity1.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#BB9DF1"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/input_field"
        android:layout_width="252dp"
        android:layout_height="48dp"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/factorial_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="#3F51B5"
        android:text="FIND FACTORIAL"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/input_field" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="217dp"
        android:layout_height="46dp"
        android:text="FACTORIAL FINDER"
        android:textColor="#673AB7"
        android:textSize="24sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toTopOf="@+id/input_field"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### In MainActivity.java
```
package com.example.explicitintent;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity1);

        // Get references to UI elements
        final EditText inputField = findViewById(R.id.input_field);
        Button factorialButton = findViewById(R.id.factorial_button);

        // Set up the "Explicit Intent" button
        factorialButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the input number from the text field
                int inputNumber = Integer.parseInt(inputField.getText().toString());

                // Create an Intent to start the FactorialActivity
                Intent explicitIntent = new Intent(MainActivity.this, MainActivity2.class);
                // Pass the input number as an extra
                explicitIntent.putExtra("input_number", inputNumber);

                // Start the FactorialActivity
                startActivity(explicitIntent);
            }
        });
    }
}
```

### In activity_main1.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout2"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#BB9DF1"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/result_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="#9C27B0"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.3" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="BACK"
        android:onClick="back"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/result_text_view" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### In MainActivity2.java
```

package com.example.explicitintent;


import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

import java.math.BigInteger;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Get the input number from the Intent extra
        int inputNumber = getIntent().getIntExtra("input_number", 0);

        // Calculate the factorial of the input number using BigInteger
        BigInteger factorial = BigInteger.ONE;
        for (int i = 2; i <= inputNumber; i++) {
            factorial = factorial.multiply(BigInteger.valueOf(i));
        }

        // Display the factorial result in a TextView
        TextView resultTextView = findViewById(R.id.result_text_view);
        resultTextView.setText("Factorial of " + inputNumber + " is: " + factorial);
    }

    public void back(View view) {
        Intent i = new Intent(getApplicationContext(), MainActivity.class);
        startActivity(i);
    }
}
```
## OUTPUT
![WhatsApp Image 2024-03-17 at 21 14 40_65d4e92a](https://github.com/sabithapaulraj/ExplicitIntent-MAD/assets/118343379/accd5111-a814-45e7-89a8-810b6681c688)
![WhatsApp Image 2024-03-17 at 21 14 40_bdd2071b](https://github.com/sabithapaulraj/ExplicitIntent-MAD/assets/118343379/706c629c-6d07-4d95-a665-3e6c8ff790dd)


## RESULT
Thus a Simple Android Application to find factorial of a given number using Explicit Intents in Android Studio is developed and executed successfully.


