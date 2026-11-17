ROBIN SMART HOME — ফোন থেকে APK তৈরি

এই ZIP-এ Android WebView প্রজেক্ট ও GitHub Actions build workflow আছে।
এটি APK নয়। GitHub-এর সার্ভার ব্যবহার করে APK তৈরি হবে।

গুরুত্বপূর্ণ: ZIP-টি সরাসরি GitHub-এ upload করবেন না। আগে Extract করুন।
তারপর Extract করা ফোল্ডারের ভেতরের সব ফাইল/ফোল্ডার Repository-র root-এ upload করুন।
নিশ্চিত করুন:
1) app ফোল্ডার আছে
2) build.gradle ও settings.gradle root-এ আছে
3) .github/workflows/build-apk.yml ঠিক ওই path-এ আছে

ধাপ:
1. github.com এ account খুলুন / sign in করুন।
2. New repository তৈরি করুন: Robin-Smart-Home
3. Extract করা project-এর সব ফাইল upload করুন (hidden .github ফোল্ডারসহ)।
4. Actions tab খুলুন। "Build Robin Smart Home APK" workflow দেখা যাবে।
5. Run workflow চাপুন (অথবা main branch-এ push হলে নিজে build হবে)।
6. Build শেষ হলে সবুজ Success দেখাবে।
7. Workflow run-এর নিচে Artifacts থেকে Robin-Smart-Home-APK ডাউনলোড করুন।
8. ZIP extract করে app-debug.apk ফোনে install করুন।

অ্যাপের কাজ:
- ৪টি রিলের GPIO নির্বাচন
- ESP8266-এর জন্য Arduino sketch তৈরি ও .ino download
- ESP8266 local HTTP endpoint-এ relay command পাঠানো

সীমাবদ্ধতা ও নিরাপত্তা:
- অ্যাপ নিজে ESP8266-এ firmware upload করে না।
- ESP8266-এ generated sketch Arduino IDE/সমর্থিত uploader দিয়ে flash করতে হবে।
- Relay control-এর জন্য ESP8266 firmware-এ /api/set?relay=1&state=1 এবং /api/status endpoint থাকতে হবে।
- এই starter firmware-এ authentication নেই এবং HTTP cleartext; ইন্টারনেটে expose করবেন না।
- প্রথমে low-voltage load দিয়ে পরীক্ষা করুন। মেইনস বিদ্যুতের wiring দক্ষ ইলেকট্রিশিয়ান দিয়ে করান।
- রিলে Active-LOW ধরে sketch তৈরি হয়।
