# Android Material Intro Screen
Material intro screen is inspired by https://github.com/HeinrichReimer/material-intro/ and developed with love from scratch. I decided to rewrite completely almost all features in order to make Android intro screen easy to use for everyone and extenisble as possible.
## Features
  - Easly add new slides
  - Custom slides
  - Parallax slides
  - Easy extensible api
  - Material design as it's best!!!

## Usage
First your class intro activity class need to extend MaterialIntroActivity
```java
public class IntroActivity extends MaterialIntroActivity
```
Step 2: Add slides
```java
 addSlide(new SlideFragmentBuilder()
                .primaryColor(R.color.colorPrimary)
                .secondaryColor(R.color.colorAccent)
                .possiblePermissions(new String[]{Manifest.permission.CALL_PHONE, Manifest.permission.READ_SMS})
                .neededPermissions(new String[]{Manifest.permission.CAMERA, Manifest.permission.ACCESS_FINE_LOCATION, Manifest.permission.ACCESS_COARSE_LOCATION})
                .image(agency.tango.materialintroscreen.R.drawable.ic_next)
                .messageButtonText("Android")
                .messageButtonClickListener(new View.OnClickListener()
                {
                    @Override
                    public void onClick(View v)
                    {
                        Toast.makeText(getApplicationContext(), "Hate eating apples.", Toast.LENGTH_SHORT).show();
                    }
                })
                .title("title 3")
                .description("Description 3")
                .build());
```
Step 3: Customize Intro Activity
  - setSkipButtonVisible -> show skip button instead of back button on the left bottom of screen
  - hideBackButton -> hides any button on the left bottom of screen
  - enableLastSlideAlphaExitTransition -> set if the last slide should disapear with alpha hiding effect

Explanation of SlideFragment usage:
  - primaryColor -> color of the slides background
  - secondaryColor -> color of the slides buttons
  - possiblePermissions -> permissions which are not necessary to be granted
  - neededPersmissions -> permission which are needed to be granted to move further from that slide
  - messageButtonClickListener -> implement only if you want to have custom action on message button

## Custom slides
Of course you are able to implement completely custom slides. You only need to extend SlideFragment and override functions:
 - primaryColor()
 - secondaryColor()
 - canMoveFurther() (only if You want to stop user from being able to move further before he will do some action)
 - cantMoveFurtherErrorMessage() (as above)
 
If you want to use parallax in fragment please use one of below views:
  - ParallaxFrameLayout
  - ParallaxLinearLayout
  - ParallaxRelativeLayout

And set there attribute app:layout_parallaxFactor
```xml
<agency.tango.materialintroscreen.parallax.ParallaxLinearLayout
xmlns:android="http://schemas.android.com/apk/res/android">

    <ImageView
        android:id="@+id/image_slide"
        app:layout_parallaxFactor="0.6"/>
```

All features not available in simple Slide Fragment are shown here: [Custom Slide]
[Custom Slide]: <https://github.com/TangoAgency/material-intro-screen/blob/master/app/src/main/java/agency/tango/materialintro/CustomSlide.java>
