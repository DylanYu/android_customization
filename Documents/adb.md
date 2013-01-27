#Android Debug Bridge

Android Debug Bridge ([adb][1]) is a versatile command line tool that lets you communicate with an emulator instance or connected Android-powered device. It is a client-server program that includes three components:

*  A client, which runs on your development machine. You can invoke a client from a shell by issuing an adb command. Other Android tools such as the ADT plugin and DDMS also create adb clients.
*  A server, which runs as a background process on your development machine. The server manages communication between the client and the adb daemon running on an emulator or device.
*  A daemon, which runs as a background process on each emulator or device instance.

##Usage in our project
Use the following command:

    adb shell dumpsys activity  

We could get a lot of information,

and the part of TaskRecord and ProcessRecord are concerned.

Here's an example of TaskRecord:

    Running activities (most recent first):
        TaskRecord{461008f8 #11 A com.android.settings}
          Run #5: HistoryRecord{4616aff8 com.android.settings/.DisplaySettings}
          Run #4: HistoryRecord{461006a8 com.android.settings/.Settings}
        TaskRecord{46305ae0 #3 A com.android.launcher}
          Run #3: HistoryRecord{4627bbb8 com.android.launcher/com.android.launcher2.Launcher}
        TaskRecord{46084970 #10 A android.task.mms}
          Run #2: HistoryRecord{460effe0 com.android.mms/.ui.ComposeMessageActivity}
          Run #1: HistoryRecord{46106608 com.android.mms/.ui.ConversationList}
        TaskRecord{4610a6f0 #9 A android.task.pictures}
          Run #0: HistoryRecord{4610a4e0 com.android.gallery/com.android.camera.GalleryPicker}

Here's an example of ProcessRecord:

    Running processes (most recent first):
        App  #13: adj=vis  /F 461826d0 128:jp.co.omronsoft.openwnn/10023 (service)
                  jp.co.omronsoft.openwnn.OpenWnnJAJP<=ProcessRecord{45fc66f8 66:system/1000}
        App  #12: adj=vis  /F 4618f998 265:com.android.email/10030 (service)
                  com.android.email.service.EasAuthenticatorService<=ProcessRecord{45fc66f8 66:system/1000}
        PERS #11: adj=sys  /F 45fc66f8 66:system/1000 (fixed)
        App  #10: adj=fore /F 460f6580 282:com.android.settings/1000 (top-activity)
        App  # 9: adj=home /B 46266f28 169:com.android.launcher/10025 (home)
        PERS # 8: adj=core /F 4618ec20 133:com.android.phone/1001 (fixed)
        App  # 7: adj=bak  /B 461444f8 249:com.android.mms/10015 (bg-activities)
        App  # 6: adj=bak+1/B 45fcb940 289:com.android.gallery/10002 (bg-activities)
        App  # 5: adj=bak+2/B 45fa8660 235:android.process.media/10002 (bg-empty)
        App  # 4: adj=bak+3/B 461448f8 208:com.android.quicksearchbox/10012 (bg-empty)
        App  # 3: adj=bak+4/B 4626d568 227:com.android.music/10022 (bg-empty)
        App  # 2: adj=bak+5/B 4627c258 217:com.android.protips/10007 (bg-empty)
        App  # 1: adj=bak+6/B 45fc8360 190:com.android.alarmclock/10009 (bg-empty)
        App  # 0: adj=bak  /B 462718b0 180:android.process.acore/10000 (provider)
                  com.android.providers.contacts.ContactsProvider2<=ProcessRecord{461444f8 249:com.android.mms/10015}

----------------------------------
*more on [slideshare][2]*

[1]: http://developer.android.com/tools/help/adb.html "developer.android.com"
[2]: http://www.slideshare.net/tetsu.koba/adbandroid-debug-bridge-how-it-works "Android Debug Bridge: How it works?"
