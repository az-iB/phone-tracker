phone-tracker
=============

Phone-tracker driver for ninjablock.
This driver make it possible to track your phone in realtime from the ninja dashboard.

How it works
--------------
This driver creates an device on your ninjablock. That device then makes it possible to receive lat/long coordinates from your phone.
This only works on Android phones. That is because the use of On{x} app on your phone. The On{x} app makes it possible to send the phones location to the ninja device.

How to use
--------------
**What you will need**
- A phone that runs Android.
- On{x} account and their application on your Android phone. http://onx.ms/

**STEP 1.**
Clone the this driver and install it.
The driver basically adds an device to your ninjablock.
Check out the quickstarts if you don't know how to install a driver:
http://docs.ninja.is/quickstarts/driverrealm/installdrivers.html


**STEP 2:**
Enable Webhooks and Twilio on the service page in the dashboard.
Then add your phone number in the Twilio widget.

Then add 2 inbound webhooks.
Name them "Start phone tracking" and "Stop phone tracking".

**STEP 3:**
Now enable the beta dashboard if you haven't already done so.
Add a new widget and use this gist:
	https://gist.github.com/jenslind/6210665

Now get your webhooks links and insert them in the top of the javascript code.
The "Start phone tracking" webhook in the WEBHOOK_START variable and the "Stop phone tracking" webhook in the WEBHOOK_STOP variable.

Then assign the "sandbox" device to this widget.

If you are new to the beta dashboard. Check this out:
http://forums.ninjablocks.com/index.php?p=/discussion/1581/screencast-custom-widgets-on-the-beta-dashboard

**STEP 4:**
Now, create a new rule on http://www.onx.ms/ with this code:
	https://gist.github.com/jenslind/6211667
Make sure to change the variables at the top.

**STEP 5:**
Last step! :)
Now we need to create two rules in the ninja dashboard.

First rule:
1. Choose your webhook named "Start phone tracking" as a sensor.
2. Choose the sms as the event. And in the body type: "StartTracking".
Save the rule.

Second rule:
1. Choose your webhook named "Stop phone tracking" as a sensor.
2. Choose the sms as the event. And in the body type: "StopTracking".
Save the rule.

You are done!
Hopefully this will now work for you!
To test it out go to the widget and click the green button "Start track". You should receive an sms and your location should be updated on the map in a few seconds.


**Ninjablock forums link**
http://forums.ninjablocks.com/index.php?p=/discussion/1606/how-to-track-your-lost-phone-in-real-time
