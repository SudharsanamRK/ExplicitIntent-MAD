# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED

Latest Version Android Studio

## ALGORITHM
Step 1: Create a New Project in Android Studio

Step 2: Working with the activity_main.xml File

Step 3: Working with the MainActivity File

Step 4: Working with the activity_main2.xml File

Step 5: Working with the MainActivity2 File


## PROGRAM
```
Program to print the text “ExplicitIntent”.
Developed by:  Sudharsanam R K
Registeration Number : 212222040163
```
## In MainActivity.java
```java
package com.example.explicitintent;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    private EditText editTextNumber;
    private Button buttonFactorial;
    private Button buttonExplicit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextNumber = findViewById(R.id.editTextNumber);
        buttonFactorial = findViewById(R.id.buttonFactorial);
        buttonExplicit = findViewById(R.id.buttonExplicit);

        buttonFactorial.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculateFactorial();
            }
        });

        buttonExplicit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                openSecondActivity();
            }
        });
    }
```
```

    private void calculateFactorial() {
        int number = Integer.parseInt(editTextNumber.getText().toString());
        int factorial = 1;
        for (int i = 1; i <= number; i++) {
            factorial *= i;
        }
        openSecondActivityWithFactorial(factorial);
    }

    private void openSecondActivityWithFactorial(int factorial) {
        Intent intent = new Intent(this, SecondActivity.class);
        intent.putExtra("factorial", factorial);
        startActivity(intent);
    }

    private void openSecondActivity() {
        Intent intent = new Intent(this, SecondActivity.class);
        startActivity(intent);
    }
}
```

## In SecondActivity.java
```java
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

    private TextView textViewResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        textViewResult = findViewById(R.id.textViewResult);

        Bundle extras = getIntent().getExtras();
        if (extras != null && extras.containsKey("factorial")) {
            int factorial = extras.getInt("factorial");
            textViewResult.setText("Factorial: " + factorial);
        } else {
            textViewResult.setText("Factorial not calculated");
        }
    }
}
```
## In activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"/>

    <Button
        android:id="@+id/buttonFactorial"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Calculate Factorial"
        app:icon="@android:drawable/star_big_on" />

    <Button
        android:id="@+id/buttonExplicit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent"/>

</LinearLayout>
```
## In acitvity_second.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:backgroundTint="@color/design_default_color_error"
    android:padding="16dp"
    tools:context=".SecondActivity">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:textSize="20sp" />

</RelativeLayout>
```

## OUTPUT
![request](https://github.com/SudharsanamRK/ExplicitIntent-MAD/assets/115523484/53c48597-078e-42d9-a200-39bd42ad72ed)

![factorial i/p](https://github.com/SudharsanamRK/ExplicitIntent-MAD/assets/115523484/86727777-d6ac-47cf-9436-625226ed2aa3)

![factorial o/p](https://github.com/SudharsanamRK/ExplicitIntent-MAD/assets/115523484/d6182352-4055-4f0a-8847-655824559a6b)

![if error](https://github.com/SudharsanamRK/ExplicitIntent-MAD/assets/115523484/61ff1aa2-91bd-4a60-a95a-6d5a7c5d22e6)


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
