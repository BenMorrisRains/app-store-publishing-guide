# ULC App Store Publishing Guide 
This is a comprehensive guide to publishing apps on the Apple App Store and Google Play Store. 
## Apple App Store 

### X-Code Archive Publish 

 1. In X-Code, open the iosApp directory and then click on the `Smart Drainage System Control.xcodeproj` file. This should be located under `agridrain/ulc-compose-app/iosApp` 
 2. This will launch the X-Code project for the application. 
 3. In the Project Navigator view (folder icon), click on the project name ("Smart Drainage System Control"). 
 4. In the right panel, click on "Info" 
 5. Find the `Bundle Version String` and double click on the value to update the version. Please use semantic versioning for the app version (Apple requires this as well). ie: If the version is `0.2.0` and you are not fixing a bug but implemented a new feature or a refactor, bump it to `0.3.0`. Bugs should bump the patch version ie: `0.2.1` would signify a bug fix. THIS MATTERS FOR THE STORES! App reviews go faster for bug fixes. 
 6. Bump the version to a major version once the app is ready for primetime, ie: `1.0.0`![Bumping Version](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/version-bump.png)
 7. In the X-Code toolbar go to Publish -> Archive ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/publish-archive.png)
 8. This will begin the build of the binary for the App Store. This can take a few minutes to a half an hour. 
 9. If you run into Java heap space issues, update the `gradle.properties` file to this: 
```properties  
#Kotlin  
kotlin.code.style=official  
kotlin.daemon.jvmargs=-Xmx4096M  
  
#Gradle  
org.gradle.jvmargs=-Xmx4096M -Dfile.encoding=UTF-8  
  
#Android  
android.nonTransitiveRClass=true  
android.useAndroidX=true  
  
#Ktor  
io.ktor.development=true  
  
kotlin.native.cacheKind=none  
kotlin.native.binary.memoryModel=experimental  
kotlin.native.binary.freezing=disabled  
```
 11. After it is done you will see a dialog that looks like this: ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/distribute-dialog.png)
 12. Click on the version you just built (the top one in the list) then click "Distribute App"
 13. That takes you to this dialog. To distribute to Test Flight for internal users to test, click on "TestFlight Internal Only"![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/testflight-distribute.png)
 14. **To actually publish the app to the app store click on App Store Connect, then Distribute** ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/appstore-distribute.png)
 15. This will begin the app store upload. 
 16. After it has completed head to https://appstoreconnect.apple.com/
 17. Select the Smart Drainage Control System App (Ignore the other two) 
 18. For Test Flight, click on Test Flight 
 19. Your new version should appear. 
 20. You will need to select it from the build list. 


## Google Play Store 

 1. You will need the keystore file for this. 
 2. In Android Studio, open up the project and head to the `build.gradle.kts` file here: `composeApp/build.gradle.kts` 
 3. For Android you will need to update the version just like for iOS. Please keep the semantic versioning schema. 
 4. Important: You will also need to bump the versionCode! ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/version-versioncode.png)
 5. Now sync the gradle project. 
 6. Now in the Android Studio toolbar, go to Build -> Generate Signed App Bundle or APK... ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/android-build.png)

 7. Ensure the Android App Bundle option is selected and then click next: ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/appbundle.png)
 8. Ensure the next screen appears like in the image. You will need to select the keystore file that you saved on your machine (locally). You will also need the key store password and the key password, which I will send to you: ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/bundle-gen.png)
 9. Now you will go to the Google Play Developer Console: Ensure you have access and can login to https://play.google.com/console/
 10. Click on the AgriDrain profile 
 11. From the console click on the Smart Water 1000 app 
 12. Then click on Test and Release 
 13. For a real release, click on Production. For Testing click on Testing -> Internal Testing 
 14. Click on "Create new release" 
 15. Here you will need to drag or upload the app bundle you generated from Android Studio. ![enter image description here](https://raw.githubusercontent.com/BenMorrisRains/app-store-publishing-guide/refs/heads/main/new-release.png)


