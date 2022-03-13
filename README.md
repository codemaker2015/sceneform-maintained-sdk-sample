Sceneform Maintained SDK Sample
====================================

<img src="demo/demo.gif" width="240" height="520" />

## Setup the project

### Dependencies

Add sceneform dependency in the `app/build.gradle`

```gradle
dependencies {
     implementation "com.gorisse.thomas.sceneform:sceneform:1.20.5"
}
```

Update the `AndroidManifest.xml` wth arcore metadata

```xml
<uses-permission android:name="android.permission.CAMERA" />

<application>
    ...
    <meta-data android:name="com.google.ar.core" android:value="optional" />
</application>
```

### Setup the layout (`main_activity.xml`)

```xml
<androidx.fragment.app.FragmentContainerView
    android:id="@+id/arFragment"
    android:name="com.google.ar.sceneform.ux.ArFragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

### Load the models

Add the `setOnTapPlaneGlbModel` method in the ` MainActivity.java` to load the model

```java

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import com.google.ar.sceneform.ux.ArFragment;
public class MainActivity extends AppCompatActivity {
    ArFragment arFragment;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        // Load model.glb from assets folder or http url
        arFragment = (ArFragment) getSupportFragmentManager().findFragmentById(R.id.arFragment);
        arFragment.setOnTapPlaneGlbModel("model.glb");
        //        arFragment.setOnTapPlaneGlbModel("https://github.com/codemaker2015/3d-models/blob/master/glb_files/model.glb?raw=true");
    }
}
```