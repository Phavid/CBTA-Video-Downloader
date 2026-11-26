# CBTA Media Center (កម្មវិធីទាញយកវីដេអូ/អូឌីយ៉ូ ដូច YTDLnis)

Kotlin + Jetpack Compose + Room + youtubedl-android (yt-dlp, FFmpeg, aria2c). Android 7.0+ (minSdk 24).

## មុខងារ / Features
- បិទភ្ជាប់តំណ ឬចែករំលែកតំណមកកម្មវិធី (Share menu) / paste or share a link; search words use `ytsearch10:`
- អូឌីយ៉ូ (mp3, m4a, opus, aac, flac, wav) / វីដេអូ (mp4, mkv, webm) / ពាក្យបញ្ជា yt-dlp (custom command)
- ជ្រើសគុណភាព និង format ជាក់លាក់ / choose quality or a specific format id
- Playlist: ជ្រើសធាតុ ហើយទាញយកច្រើន / select items, download many
- ជួរទាញយក + ទាញយកព្រមគ្នា (១–៥) / queue with 1–5 simultaneous downloads, Foreground Service + notification
- កំណត់ពេលទាញយក (AlarmManager) / schedule downloads by date and time
- នាំចូលតំណច្រើនពីឯកសារ .txt (មួយបន្ទាត់មួយតំណ ឬពាក្យស្វែងរក)
- Templates ពាក្យបញ្ជា + នាំចេញ/នាំចូល JSON backup
- Terminal mode (yt-dlp CLI)
- Cookies, subtitles (embed), cover image (embed), split chapters, aria2c, concurrent fragments
- ជ្រើសថតរក្សាទុក (SAF) ឬ Downloads/CBTA Media Center
- ធ្វើបច្ចុប្បន្នភាព yt-dlp ក្នុងកម្មវិធី / in-app yt-dlp update
- ភាសា ខ្មែរ + អង់គ្លេស, ប៊ូតុងទាំងអស់មានអក្សរសម្រាប់ TalkBack

## របៀបបង្កើត APK ដោយឥតគិតថ្លៃ (GitHub Actions — មិនបាច់ដំឡើង Android Studio)
1. បង្កើតគណនី GitHub និង repository ថ្មី (Public ឬ Private)
2. Upload ឯកសារទាំងអស់ក្នុង zip នេះ (រួមទាំងថត `.github`) ទៅ repository
3. ចូលផ្ទាំង **Actions** → ជ្រើស **Build APK** → **Run workflow** (ឬវាដំណើរការដោយខ្លួនឯងពេល upload)
4. ពេលរួច ទាញយក artifact ឈ្មោះ **CBTA-Media-Center-apk** → ដំឡើង `app-debug.apk` លើទូរស័ព្ទ

## ឬប្រើ Android Studio
Open folder → រង់ចាំ Gradle sync → Build > Build APK(s)។ ឬ command line: `gradle assembleDebug`

## ចំណាំ / Notes
- កូដនេះត្រូវបានសរសេរដោយមិនទាន់បាន compile ក្នុងបរិយាកាសសរសេរ (គ្មាន Android SDK/អ៊ីនធឺណិត)។
  ប្រសិនបើ build មានកំហុស សូមចម្លងសារកំហុសមកខ្ញុំ ដើម្បីកែ។ ចំណុចដែលត្រូវពិនិត្យមុនគេ (ទាក់ទងនឹង API របស់បណ្ណាល័យ youtubedl-android 0.17.4):
  `YoutubeDL.getInstance().execute(request, processId) { progress, eta, line -> }` និង `YoutubeDL.UpdateChannel.STABLE` ក្នុង `MainVM.updateYtdlp()`។
- ABI: arm64-v8a និង armeabi-v7a (ទូរស័ព្ទ)។ បន្ថែម x86_64 ក្នុង `app/build.gradle.kts` ប្រសិនបើប្រើ emulator។
- APK ប្រហែល ៨០–១២០MB ព្រោះមាន Python + FFmpeg + aria2c។
- មិនទាន់មាន "bottom card" ពេលចែករំលែក ដូច YTDLnis (ចែករំលែកតំណនឹងបើកកម្មវិធីនេះ)។
- ប្រើតែជាមួយមាតិកាដែលអ្នកមានសិទ្ធិទាញយក។ បណ្ណាល័យ youtubedl-android និង yt-dlp ប្រើអាជ្ញាបណ្ណ GPL/Unlicense ដែលអ្នកគួរពិនិត្យប្រសិនបើចែកចាយកម្មវិធី។
