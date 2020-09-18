# AppyhighUtils

To import this library, Add the following line to your app level build.gradle file.

implementation 'com.github.PrasadVennamAppy:AppyhighUtils:{latestVersion}

This library consists of following modules

    1)CleverTap Events
    2)Push Notifications (CleverTap and Firebase)
    3)InApp Notifications (CleverTap and Firebase)
    4)Ads (Interstitial and Native)
    5)Dynamic Linking
    6)Apxor Events
  
## CleverTap Events

A boolean value 'onlyFirebase' needs to be provided as parameter while using this module

'onlyFirebase'  - true  - Only Firebase Cloud Messaging is used for events
'onlyFirebase'  - false - Both CleverTap and Firebase Cloud Messaging can be used for events

## Push Notifications (CleverTap and Firebase)

CleverTap and Firebase can be used for push notifications in this library.




## InApp Notifications (CleverTap and Firebase)

## Ads (Interstitial and Native)

Add the following lines to your app level build.gradle file.
```
implementation 'com.github.PrasadVennamAppy:AppyhighUtils:{latestVersion}
implementation 'com.google.android.gms:play-services-ads:{latestVersion}

```
Add the following lines inside the application tag in *AndroidManifest.xml* file
```
<meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ca-app-pub-3940256099942544~3347511713"/>

```
### Interstitial Ads

1.To create a new Interstitial Ad, call the *newInterstitialAd* method as shown

```
newInterstitialAd(adId: String,activity: AppCompatActivity,screen: String, closeListener: AdCloseListener): InterstitialAd

return type : InterstitialAd

params:
adId          - String,
activity      - AppCompatActivity,
screen        - String,
closeListener - AdCloseListener

```
2.To load an Interstitial Ad, call the *loadInterstitial* method as shown

```
loadInterstitial(mInterstitialAd: InterstitialAd)

params:
mInterstitialAd - InterstitialAd

```
#### Example
```
 ad = newInterstitialAd(resources.getString(R.string.test_interstitial),this@MainActivity, "app_exit", this)
 loadInterstitial(ad)
 if (ad.isLoaded) {
    ad.show()
  }
```

### Native Ads

#### Template Native Ad of corresponding activity/fragment
1.Add the following lines inside the layout of a corresponding activity/fragment
```
<com.appyhigh.mylibrary.ads.TemplateView
        android:id="@+id/template_ad_small"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:gnt_template_type="@layout/gnt_medium_template_view" />
```

2.To load the template of Native Ad, call the *loadTemplateNativeAd* method as shown
```
loadTemplateNativeAd(context: Context, adId: String, templateView: TemplateView, screen: String)

params:
context       - Context,
adId          - String,
templateView  - TemplateView,
screen        - String
```
#### UnifiedNativeAd
1.To load the Unified Native Ad, call the *loadUnifiedNativeAd* method as shown
```
loadUnifiedNativeAd(context: Context, adId: String, nativeAdArea: LinearLayout, screen: String)

params:
context       - Context,
adId          - String,
nativeAdArea  - LinearLayout,
screen        - String
```

## Dynamic Linking

1. Create a Domain Link in your linked firebase account to use Dynamic Linking

2. To receive Dynamic Links, add the following intent-filter to your *AndroidManifest.xml* file

```
<intent-filter>
    <action android:name="android.intent.action.VIEW"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <category android:name="android.intent.category.BROWSABLE"/>
    <data
        android:host="your_domainLink"
        android:scheme="https"/>
</intent-filter>
```

3. To create and share dynamic links that opens the link on your app, call the *createShortLink* method as shown
```
createShortLink(link: String, domain: String, packageName: String?, linkMessage: String, context: Context)

params:
link        - deepLink of your project
domain      - domainLink of your project which you already created on the linked firebase account
packageName - packageName of your project
linkMessage - extra message that you want while sharing your link
context     - Context

```

4. To receive the deep link, call the *getDynamicLink* method as shown
```
getDynamicLink(intent: Intent):Uri?

return type : Uri

params:
intent      - Intent
```
  

## Apxor Events
