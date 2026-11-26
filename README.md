# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## NAME : AADHITHYAA L
## REGISTER NUMBER : 212224220003

## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: AADHITHYAA L
Registeration Number : 212224220003
*/
```


activity_main.xml :
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Audio Player"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_marginBottom="40dp"/>

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btnPlay"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Play"
            android:layout_margin="5dp"/>

        <Button
            android:id="@+id/btnPause"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Pause"
            android:layout_margin="5dp"/>

        <Button
            android:id="@+id/btnStop"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Stop"
            android:layout_margin="5dp"/>

    </LinearLayout>

</LinearLayout>
```


MainActivity.java :
```
package com.example.audioplayer;

import android.media.MediaPlayer;
import android.media.PlaybackParams;
import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private static final String TAG = "MainActivity";
    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnPlay = findViewById(R.id.btnPlay);
        Button btnPause = findViewById(R.id.btnPause);
        Button btnStop = findViewById(R.id.btnStop);

        mediaPlayer = MediaPlayer.create(this, R.raw.arasan_str_theme_bgm);

        // Play Button
        btnPlay.setOnClickListener(v -> {
            if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                mediaPlayer.start();
                setNormalPlaybackSpeed();
            }
        });

        // Pause Button
        btnPause.setOnClickListener(v -> {
            if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                mediaPlayer.pause();
            }
        });

        // Stop Button
        btnStop.setOnClickListener(v -> {
            if (mediaPlayer != null) {
                mediaPlayer.stop();

                try {
                    mediaPlayer.prepare();
                } catch (Exception e) {
                    Log.e(TAG, "Error preparing MediaPlayer", e);
                }
            }
        });
    }

    private void setNormalPlaybackSpeed() {
        if (mediaPlayer != null) {
            try {
                PlaybackParams params = mediaPlayer.getPlaybackParams();
                params.setSpeed(1.0f);
                params.setPitch(1.0f);
                mediaPlayer.setPlaybackParams(params);
            } catch (Exception e) {
                Log.e(TAG, "Error setting playback speed", e);
            }
        }
    }

    // Release MediaPlayer
    @Override
    protected void onDestroy() {
        super.onDestroy();

        if (mediaPlayer != null) {
            mediaPlayer.release();
            mediaPlayer = null;
        }
    }
}

```

## OUTPUT

<img width="1917" height="1141" alt="image" src="https://github.com/user-attachments/assets/7c59401f-d47a-476e-b609-5bd4e41e804c" />

<img width="1917" height="1145" alt="image" src="https://github.com/user-attachments/assets/1873e119-c520-4edf-b9e8-4862881703b2" />


## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
