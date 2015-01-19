# Push-Notification-using-GCM-New-API
==========================

# About Application

1. This application shows how can we integrate PushNotification using App42 Android SDK in Android application.
2. Here We are using new Google Cloud Messaging API provided by Google as we know old one are depricated.
3. How we can send PushNotification using App42 PushNotification API.


# Running Sample
This is a Android sample app made by using App42 API. It uses PushNotification API of App42 platform.
Here are the few easy steps to run this sample app.

1. [Register] (https://apphq.shephertz.com/register) with App42 platform.
2. Create an app once, you are on Quick start page after registration.
3. If you are already registered, login to [AppHQ] (http://apphq.shephertz.com) console and create an app from App Manager Tab.
4. Create a project and get your Project Id from [Google developer console] (https://cloud.google.com/console/project). It would be available in Overview section of your created project..
5. Select your created project and click on APIs option in Google developer console and enable Google Cloud Messaging for Android service.
6. Click on Credentials from left menu -> Create New Key -> Server Key.
7. Keep Accept requests from these server IP addresses as blank and click on Create button
8. Go to [AppHQ] (http://apphq.shephertz.com) console and click on PushNotification and select Android Settings in Settings option.
9. Select your app, select the GCM under Provider section and copy server key under push key section which is generated in Google developer console in above step and submit it.
10. [Download] sample project (https://github.com/VishnuGShephertz/Push-Notification-using-GCM-New-API/archive/master.zip) and import it in the eclipse.
11. Add google Play Service as a library project.
10. Open MainActivity.java  file in sample project and make following changes.

```
A. Replace api-Key and secret-Key that you have received in step 32 or 33 at line number 51.
B. Replace your user-id by which you want to register your application for PushNotification at line number 34.
C. Replace your user-id by which you want to register your application for PushNotification at line number 19.

```
12.Build your android application and install on your android device.

__Test and verify PushNotification from AppHQ console__
 
```
A. After registering for PushNotification go to AppHQ console and click on PushNotification and select
  application after selecting User tab.
B. Select desired user from registered User-list and click on Send Message Button.
C. Send appropriate message to user by clicking Send Button.

```
# Design Details:
__Initializing App42API in JavaScript to send PushNotification :__ To Send PushNotification using APP42 JavaScript API we have to initialize first using Api-Key and Secret-Key in index.html file.
 
```
	function intializeApp42API() {
			App42.initialize('<YOUR API KEY>', '<YOUR SECRET KEY>');
			App42.setLoggedInUser('<Your User Id>');
		}

```







__Customize PushNotification Message:__ You can also customize your PushNotification message by changing following code in GCMIntentService.java file accordingly.
 
```
     

```




__AndroidManifest.xml file Changes:__ If you are customizing your own Android application that is built using PhoneGap API.
So make following changes in your AndroidManifest.xml using this sample's AndroidManifest.xml file.

1. Add following permission in your AndroidManifest.xml file.

```
 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.VIBRATE" />
     <uses-permission android:name="android.permission.WAKE_LOCK" />
     
      <permission
        android:name="com.shephertz.app42.android.phonegap.push.permission.C2D_MESSAGE"
        android:protectionLevel="signature" />

    <uses-permission android:name="com.shephertz.app42.android.phonegap.push.permission.C2D_MESSAGE" />
     <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />

```

2.Add Receiver component in your Androidmanifest.xml file.

```
    <receiver
            android:name="com.google.android.gcm.GCMBroadcastReceiver"
            android:permission="com.google.android.c2dm.permission.SEND" >
            <intent-filter>

                <!-- Receives the actual messages. -->
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
                <!-- Receives the registration id. -->
                <action android:name="com.google.android.c2dm.intent.REGISTRATION" />

                <category android:name="com.shephertz.app42.android.phonegap.push" />
            </intent-filter>
        </receiver>

```
3.Declare Service in your AndroidManifest.xml file.

```
  <service android:name="com.shephertz.app42.android.phonegap.push.GCMIntentService" >
        </service>
```
4.Replace "com.shephertz.app42.android.phonegap.push" with your application package name in AndroidManifest.xml file.
