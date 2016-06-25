# AndSes5Ass3
MainActivity.jama
package me.rk.andses3ass3;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    private Button mandroidbutton;
    private Button mjavabutton;
    private Button mpythonbutton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mandroidbutton=(Button) findViewById(R.id.androidButton);
        mandroidbutton.setOnClickListener(this);

        mjavabutton=(Button) findViewById(R.id.javaButton);
        mjavabutton.setOnClickListener(this);

        mpythonbutton=(Button) findViewById(R.id.pythonButton);
        mpythonbutton.setOnClickListener(this);
    }

    @Override
    public void onClick(View v) {
        int id=v.getId();
        Intent intent=new Intent(MainActivity.this, SecondActivity.class);

        switch (id){
            case R.id.androidButton:
                intent.putExtra("name", "Akilesh");
                startActivity(intent);
                break;

            case R.id.javaButton:
                intent.putExtra("name", "Priyanka");
                startActivity(intent);
                break;

            case R.id.pythonButton:
                intent.putExtra("name", "Ankita");
                startActivity(intent);
                break;
        }
    }
}

SecondActivity.java
package me.rk.andses3ass3;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

/**
 * Created by airodyra on 6/25/2016.
 */
public class SecondActivity extends Activity {
    private TextView mdataTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.second_layout);

        mdataTextView=(TextView) findViewById(R.id.textview);

        Intent intent=getIntent();
        String name=intent.getStringExtra("name");

        mdataTextView.setText(name);
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="me.rk.andses3ass3.MainActivity">

    <Button
        android:id="@+id/androidButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Android course"
        android:layout_centerHorizontal="true" />

    <Button
        android:id="@+id/javaButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Java course"
        android:layout_below="@id/androidButton"
        android:layout_alignEnd="@+id/androidButton"
        android:layout_alignStart="@+id/pythonButton" />

    <Button
        android:id="@+id/pythonButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Python course"
        android:layout_centerHorizontal="true"
        android:layout_below="@id/javaButton"/>

</RelativeLayout>

second_layout.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="25sp"
        android:layout_centerInParent="true"/>
</RelativeLayout>
