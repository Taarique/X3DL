চমৎকার! আপনার বট এখন নির্ভুলভাবে কাজ করছে জেনে দারুণ লাগলো। নিচে আমি একটি পূর্ণাঙ্গ ওপেন সোর্স টিউটোরিয়াল তৈরি করে দিচ্ছি, যা আপনি সরাসরি আপনার GitHub রিপোজিটরির README.md ফাইলে বসিয়ে দিতে পারেন।

এটি এন্ড্রয়েড (Termux) এবং কম্পিউটার (Windows/Linux/macOS) উভয় প্লাটফর্মের জন্যই উপযোগী।

---

📘 X3DL Pro Bot – সম্পূর্ণ ইনস্টলেশন ও কনফিগারেশন গাইড

https://img.shields.io/badge/Python-3.10%2B-blue
https://img.shields.io/badge/Pyrogram-2.0%2B-orange
https://img.shields.io/badge/yt--dlp-2024%2B-red
https://img.shields.io/badge/License-MIT-green

X3DL Pro Bot একটি হাইব্রিড টেলিগ্রাম বট যা ইউজারবট ও নরমাল বট উভয় মোডেই কাজ করে। এটি ইউটিউব, ফেসবুক, ইনস্টাগ্রাম, টিকটক সহ ১০০০+ সাইট থেকে ভিডিও/অডিও ডাউনলোড করতে পারে এবং চ্যানেল অটো-পোস্টিং (CMS) ফিচার প্রদান করে।

মূল বৈশিষ্ট্যসমূহ:

· 🎬 4K পর্যন্ত ভিডিও ডাউনলোড (সাইজ ও স্পিডসহ লাইভ প্রোগ্রেস বার)
· 🎵 হাই কোয়ালিটি MP3 অডিও এক্সট্রাক্ট
· 💾 2GB+ ফাইল সাপোর্ট (ইউজারবটের মাধ্যমে)
· 🤖 ইনলাইন মোড (যেকোনো চ্যাটে @your_bot লিখে সার্চ ও ডাউনলোড)
· 📢 চ্যানেল CMS: একটি কমান্ডে বাল্ক ভিডিও আপলোড
· 🧠 স্মার্ট মেমরি: ডুপ্লিকেট ভিডিও অটো-স্কিপ
· 👥 গ্রুপ অটো-ডাউনলোড টগল
· 🛡️ 24/7 চালানোর উপযোগী (Flask সার্ভার ও tmux সহ)

---

📋 প্রয়োজনীয় উপকরণ

প্ল্যাটফর্ম প্রয়োজনীয় সফটওয়্যার
Android (Termux) Termux, Termux:Widget (অপশনাল), Termux:API (অপশনাল)
Windows Python 3.10+, Git, FFmpeg
Linux/macOS Python 3.10+, Git, FFmpeg, tmux (অপশনাল)

এছাড়া একটি টেলিগ্রাম অ্যাকাউন্ট ও স্থিতিশীল ইন্টারনেট সংযোগ প্রয়োজন।

---

🔐 ধাপ ১: প্রয়োজনীয় API ডাটা সংগ্রহ

বট চালাতে নিচের চারটি তথ্য আবশ্যক:

ভ্যারিয়েবল বিবরণ সংগ্রহের স্থান
API_ID আপনার টেলিগ্রাম অ্যাপের আইডি my.telegram.org
API_HASH আপনার টেলিগ্রাম অ্যাপের হ্যাশ my.telegram.org
BOT_TOKEN আপনার বটের টোকেন @BotFather
DUMP_CHANNEL_ID স্টোরেজ চ্যানেলের আইডি @RawDataBot বা @userinfobot

DUMP_CHANNEL_ID কীভাবে পাবেন:
১. একটি প্রাইভেট চ্যানেল তৈরি করুন।
২. চ্যানেলে আপনার বট ও ইউজারবট অ্যাকাউন্টকে অ্যাডমিন বানান।
৩. চ্যানেলে @RawDataBot অ্যাড করে একটি মেসেজ দিন। বট আপনাকে JSON ডাটা দেখাবে, সেখান থেকে "id" ফিল্ডের মানটি কপি করুন। এটি -100... দিয়ে শুরু হবে।

---

💻 ধাপ ২: এনভায়রনমেন্ট সেটআপ

🐧 Termux (Android) এ সেটআপ

```bash
# ১. প্যাকেজ আপডেট ও প্রয়োজনীয় টুলস ইনস্টল
pkg update && pkg upgrade -y
pkg install python ffmpeg git tmux termux-api -y

# ২. পাইথন লাইব্রেরি ইনস্টল
pip install --upgrade pip
pip install pyrogram tgcrypto yt-dlp flask

# ৩. স্টোরেজ পারমিশন দিন
termux-setup-storage
```

🖥️ Windows এ সেটআপ

1. Python.org থেকে Python 3.10+ ডাউনলোড ও ইনস্টল করুন (ইনস্টলেশনের সময় "Add Python to PATH" টিক দিন)।
2. FFmpeg.org থেকে FFmpeg ডাউনলোড করে সিস্টেম PATH-এ যোগ করুন।
3. কমান্ড প্রম্পট (CMD) বা PowerShell ওপেন করে নিচের কমান্ড দিন:

```cmd
pip install pyrogram tgcrypto yt-dlp flask
```

🐧 Linux (Ubuntu/Debian) এ সেটআপ

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip ffmpeg git tmux -y
pip3 install pyrogram tgcrypto yt-dlp flask
```

🍎 macOS এ সেটআপ

```bash
# Homebrew ইনস্টল না থাকলে প্রথমে ইন্সটল করুন
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install python ffmpeg tmux
pip3 install pyrogram tgcrypto yt-dlp flask
```

---

⚙️ ধাপ ৩: বট কনফিগারেশন (কোড এডিট)

রিপোজিটরি ক্লোন বা ডাউনলোড করার পর bot.py ফাইলটি যেকোনো টেক্সট এডিটরে খুলুন এবং নিচের লাইনগুলো আপনার তথ্য দিয়ে পূরণ করুন:

```python
# ==========================================
# ⚙️ CONFIGURATION (এখানে আপনার তথ্য বসান)
# ==========================================
API_ID = 22545443           # আপনার API ID
API_HASH = "5775ea24dcf99ab4ae187674c7acc6ce"  # আপনার API Hash
BOT_TOKEN = "8663546310:AAFVHT6AKxeT7eGBikBVUm901Zm7fnDPUXA"  # আপনার Bot Token
DUMP_CHANNEL_ID = -1003718908637  # আপনার ডাম্প চ্যানেল আইডি (মাইনাস সহ)
```

গুরুত্বপূর্ণ: DUMP_CHANNEL_ID অবশ্যই ইন্টিজার (int) হতে হবে, স্ট্রিং নয়। যেমন: -1001234567890

---

🚀 ধাপ ৪: প্রথমবার রান ও সেশন তৈরি

প্রথমবার রান করার সময় Pyrogram আপনার ইউজারবট ও বট উভয়ের জন্য সেশন ফাইল তৈরি করবে।

🏃 রান কমান্ড (Termux/Linux/macOS)

```bash
cd আপনার_বটের_ফোল্ডার
python bot.py
```

🏃 রান কমান্ড (Windows)

```cmd
cd আপনার_বটের_ফোল্ডার
python bot.py
```

প্রথম রানে যা হবে:

1. বট: স্বয়ংক্রিয়ভাবে BOT_TOKEN ব্যবহার করে লগইন করবে।
2. ইউজারবট: আপনাকে প্রথমে ফোন নম্বর চাইবে (আন্তর্জাতিক ফরম্যাটে, যেমন +8801xxxxxxxxx)।
3. এরপর টেলিগ্রাম থেকে OTP কোড আসবে, সেটি বসান।
4. যদি আপনার অ্যাকাউন্টে 2FA (Two-Step Verification) চালু থাকে, তাহলে পাসওয়ার্ড চাইবে।

সব ঠিক থাকলে নিচের মত মেসেজ দেখবেন:

```
🚀 Booting up X3DL Premium Architecture...
✅ System Online! Universal Support Activated.
```

এবার আপনার বট রেডি! /start কমান্ড দিয়ে টেস্ট করুন।

---

🔄 ধাপ ৫: 24/7 ব্যাকগ্রাউন্ডে চালানো

Android (Termux) + Termux:Widget দিয়ে এক-ক্লিক স্টার্ট

১. ~/.shortcuts/ ফোল্ডার তৈরি করুন:

```bash
mkdir -p ~/.shortcuts
```

২. start_bot.sh নামে একটি ফাইল তৈরি করুন:

```bash
nano ~/.shortcuts/start_bot.sh
```

৩. নিচের কন্টেন্ট পেস্ট করুন (পাথ আপনার বটের লোকেশন অনুযায়ী বদলান):

```bash
#!/data/data/com.termux/files/usr/bin/bash
cd ~/storage/shared/MT2/X3DL   # <-- আপনার বটের ফোল্ডার পাথ
tmux new-session -d -s x3dl 'python bot.py'
```

৪. ফাইলটি এক্সিকিউটেবল করুন:

```bash
chmod +x ~/.shortcuts/start_bot.sh
```

৫. হোম স্ক্রিনে Termux Widget যোগ করুন এবং শর্টকাটে ট্যাপ করলেই বট tmux সেশনে চালু হবে।

লগ দেখতে: tmux attach -t x3dl
বন্ধ করতে: tmux kill-session -t x3dl

Windows (টাস্ক শিডিউলার দিয়ে অটোস্টার্ট)

১. একটি .bat ফাইল তৈরি করুন (যেমন start_bot.bat):

```bat
@echo off
cd C:\Users\আপনার_নাম\Desktop\X3DL-Bot
python bot.py
```

২. Windows Task Scheduler খুলে একটি নতুন টাস্ক তৈরি করুন, যা সিস্টেম স্টার্টআপে এই .bat ফাইলটি রান করবে।

Linux (systemd সার্ভিস)

/etc/systemd/system/x3dl.service ফাইল তৈরি করুন:

```ini
[Unit]
Description=X3DL Telegram Bot
After=network.target

[Service]
Type=simple
User=আপনার_ইউজারনেম
WorkingDirectory=/home/আপনার_ইউজারনেম/X3DL-Bot
ExecStart=/usr/bin/python3 /home/আপনার_ইউজারনেম/X3DL-Bot/bot.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

তারপর:

```bash
sudo systemctl daemon-reload
sudo systemctl enable x3dl.service
sudo systemctl start x3dl.service
```

---

🛠️ ট্রাবলশুটিং (সাধারণ সমস্যা ও সমাধান)

সমস্যা সম্ভাব্য কারণ সমাধান
Peer id invalid: -100... বট/ইউজারবট চ্যানেলের সদস্য নয় চ্যানেলে বট ও ইউজারবটকে অ্যাডমিন বানান; চ্যানেলে ইউজারবট দিয়ে একটি টেস্ট মেসেজ পাঠান।
ffmpeg not found FFmpeg ইন্সটল নেই Termux: pkg install ffmpeg Windows: FFmpeg ডাউনলোড করে PATH এ যোগ করুন।
সেশন ফাইল লগইন লুপ পুরনো সেশন ফাইল ক্র্যাশ my_userbot.session ও my_bot.session ফাইল দুটি ডিলিট করে পুনরায় রান করুন।
বট রেসপন্স করছে না API আইডি/হ্যাশ ভুল my.telegram.org থেকে পুনরায় সংগ্রহ করুন।
sqlite3.OperationalError ডিস্ক ফুল বা পারমিশন সমস্যা ডিস্ক স্পেস চেক করুন; Termux এ termux-setup-storage রান দিন।

---

📂 প্রজেক্ট স্ট্রাকচার

```
X3DL-Bot/
├── bot.py                 # মূল পাইথন স্ক্রিপ্ট
├── channel_history.json   # স্মার্ট মেমরি ফাইল (অটো-জেনারেট)
├── downloads/             # টেম্পোরারি ডাউনলোড ফোল্ডার
├── my_userbot.session     # ইউজারবট সেশন (জেনারেটেড)
├── my_bot.session         # বট সেশন (জেনারেটেড)
└── README.md              # এই ফাইলটি
```

---

🌟 কীভাবে কন্ট্রিবিউট করবেন

যেকোনো বাগ রিপোর্ট, ফিচার রিকোয়েস্ট বা পুল রিকোয়েস্ট সাদরে গ্রহণযোগ্য। প্রজেক্টটি ফর্ক করে আপনার মত করে সাজিয়ে নিন!

---

⚠️ ডিসক্লেইমার

এই প্রজেক্টটি শুধুমাত্র শিক্ষামূলক উদ্দেশ্যে তৈরি। কপিরাইটযুক্ত কন্টেন্ট ডাউনলোড ও শেয়ার করার দায়ভার সম্পূর্ণ ব্যবহারকারীর। ডেভেলপার কোনো প্রকার অপব্যবহারের জন্য দায়ী নন।

---

📜 লাইসেন্স

MIT License © 2026 X3DL

---

✨ এখন আপনার পালা!

১. উপরের কন্টেন্টটি কপি করে আপনার রিপোজিটরির README.md ফাইলে পেস্ট করুন।
২. চাইলে বাংলা ও ইংরেজি দুটি ভার্সনই রাখতে পারেন।
৩. প্রয়োজনীয় স্ক্রিনশট (যেমন /start মেনু, ইনলাইন রেজাল্ট) যোগ করলে আরও আকর্ষণীয় হবে।

আপনার ওপেন সোর্স যাত্রার জন্য শুভকামনা! 🚀
