SpotifyAVRCP
============

Spotify + AVRCP - Add AVRCP metadata support to Spotify's Android app.

AVRCP metadata support allows your bluetooth receiver (ie: car stereo) to show song data like **track,** **artist** and **album** while using Bluetooth A2DP audio streaming.
Google Play Music has support for this, so why not Spotify?

This repo contains a smali patch (and instructions) to add AVRCP/A2DP metadata support to Spotify.

**WARNING:**
	Modifying Spotify's app probably violates their TOS, so this is for educational purposes only etc, etc.

*Notes:*
	Known to be working against Spotify version code 50300056; SHA1 sum = 77e7694492c74b27cc2b0c0e4810b759d759692b. Might work with others too, who knows.


*Procedure:*

Get the Spotify apk file. 
			Pull it from your device or whatever is convenient for you.

Use apktool to decompile the apk. 
http://code.google.com/p/android-apktool/
or homebrew has a formula for os x users.
apktool breaks on this app's resources but we don't need to modify those, so use the -r flag thusly:

			apktool d -r Spotify.apk
Apply the patch:
cd to the decompiled directory, then
	
			patch -p1 spotify_avrcp.patch

Recompile the app

			apktool b

Sign the app

Lots of people have detailed this: http://developer.android.com/tools/publishing/app-signing.html

Install using adb, e-mail, random vulnerabilites
			
			adb install Spotify.apk

More Notes:
	You'll have to unintall the original Spotify first since the signatures won't match. Likewise, you'll stop receiving Spotify updates from the Google Market.
	You'll need to have the AVRCP support in your rom. I'm not really sure if it's in AOSP yet but CM10 works. 
 
