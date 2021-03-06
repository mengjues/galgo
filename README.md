Galgo
=====
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-Galgo-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/1151)

A tiny Android library for those moments when you want your logs to be displayed on screen. 

### Abstract
<img src="http://i59.tinypic.com/eagm6h.png" align="right" style="float:right" height="200" />
Sometimes we want/need to know what's going on behind the scenes but our app is not always connected to our computer to let us check the logs. Galgo will let you display your log messages as an overlay on top of your UI.

Extremely useful for testers who want to have more insight into what's going on behind the scenes in our apps when it misbehaves.

You can also define some basic settings such as background color, text color, text size and number of lines to display on screen so it better fits your needs.

### How to download and Install
If you're using Android Studio, the simplest way is to download the .aar file and import it as an Android Studio project. Here's how:

Download .aar file here:  **[galgo-release-1.0.aar](https://github.com/inaka/galgo/blob/master/downloads/galgo-release-1.0.aar)**

1. `File --> New Module --> More Modules --> Import .JAR or .AAR Package`
2. Select the file `galgo-release-1.0.aar`. Hit Finish.
3. Add the following to the dependencies section in you project's build.gradle file: `compile project(':galgo-release-1.0')`
4. Add the following to your manifest file: `<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />`
5. Done.

Another option is to simply clone this repo and import it into Android Studio as a module.

### Code Example
```java
public class ExampleActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_example);

        // add some customization to the log messages
        GalgoOptions options = new GalgoOptions.Builder()
                .numberOfLines(15)
                .backgroundColor(Color.parseColor("#D9d6d6d6"))
                .textColor(Color.BLACK)
                .textSize(15)
                .build();
        Galgo.enable(this, options);

        Galgo.log("I am a log message");
    }

    public void onDestroy() {
        super.onDestroy();

        // always call disable to avoid memory leaks
        Galgo.disable(this);
    }
}
```

### Example
Here's an example of the log messages being displayed on top of our Activity:

<img src="http://i61.tinypic.com/2qw3by0.gif" align="center" style="float:center" height="400" />

### Contact Us
For **questions** or **general comments** regarding the use of this library, please use our public
[hipchat room](https://www.hipchat.com/gpBpW3SsT).

If you find any **bugs** or have a **problem** while using this library, please [open an issue](https://github.com/inaka/galgo/issues/new) in this repo (or a pull request :)).

And you can check all of our open-source projects at [inaka.github.io](http://inaka.github.io)
