**PhoneClaw**
PhoneClaw is an Android automation app that runs on-device workflows and lets you generate automation logic at runtime using **ClawScript**, a JavaScript-based scripting language built into the app.

PhoneClaw is inspired by Claude Bot/Claude Code and attempts to rebuild the agent loop for android phones natively to act as your personal assistant with access to all your apps. 

**Docs**

https://rohanarun-phoneclaw.mintlify.app/

**Demos**

Live demo: getsupers.com

Automating Twitter In A Waymo With Android XR

[![Automating Twitter In A Waymo:](https://img.youtube.com/vi/_F5Wfbragh8/0.jpg)](https://www.youtube.com/watch?v=_F5Wfbragh8)


Automating Uploading Videos To Tiktok With Songs:

[![Automating Uploading Videos To Tiktok With Songs:](https://img.youtube.com/vi/TRqPFSixaog/0.jpg)](https://www.youtube.com/watch?v=TRqPFSixaog)


Automating Creating Instagram Accounts With 2FA From Email:

[![Automating Creating Instagram Accounts](https://img.youtube.com/vi/9zR43vLYCMs/0.jpg)](https://www.youtube.com/watch?v=9zR43vLYCMs)

Automating Captchas:

[![Automating Captchas:](https://img.youtube.com/vi/aBgbr27fR5M/0.jpg)](https://www.youtube.com/watch?v=aBgbr27fR5M)

**Updates**
- 2/19/26 updated to allow selecting the openrouter model 


**What It Can Do**
- Automate multi-step app workflows on Android using the Accessibility service.
- Generate scripts at runtime for flexible, adaptive automations.
- Use vision-assisted UI targeting to click controls without hardcoded coordinates.
- Read visible on-screen text and values for branching, validation, and handoffs.
- Schedule automations with cron-like timing for recurring tasks.
- Chain actions across apps (browser, email, media, messaging) inside a single flow.
- Build flows that adapt to different device sizes, layouts, and language settings.

**Setup Instructions**
1) The cheapest phone is a $30 Moto G play you can buy at Walmart in the US. It is the phone used in the demos.
2) Enable developer mode on your android. You do not need to root the device.
3) Download Android Studio, download this Repo, open the Repo, and click Build > Generate Bundles or APKs > Generate APKs. 
4) Sideload the APK by downloading it or transferring it to your android and clicking install. Click allow when it asks for permissions.
5) When the app opens, use the voice commands to generate a simple automation like "open twitter and click the blue post button every hour"
6) It will run the agent, schedule it, then output a file you can edit in simple language like below.

**ClawScript**
ClawScript runs inside PhoneClaw using an embedded JS engine and exposes helper functions for automation, scheduling, and screen understanding. It is designed for fast iteration: write or generate small scripts at runtime, execute them immediately, and adjust based on UI feedback.

**ClawScript API (Core Helpers)**
- `speakText(text)` — Reads out text using on-device TTS to confirm state or provide progress.
- `delay(ms)` — Pauses execution for a specific number of milliseconds.
- `schedule(task, cronExpression)` — Registers a task string to run on a cron-like schedule.
- `clearSchedule()` — Removes all scheduled tasks.
- `magicClicker(description)` — Finds a UI element by natural-language description and taps it.
- `magicScraper(description)` — Answers a targeted question about what is visible on screen.
- `sendAgentEmail(to, subject, message)` — Sends an email from the device for notifications or handoffs.
- `safeInt(value, defaultVal)` — Safely parses values to integers with a fallback.

**magicClicker**
- Uses a screenshot plus vision to locate a target described in plain language.
- Taps the best-matching UI element through the Accessibility service.
- Best for repeatable flows where the UI layout may shift between devices.

**magicScraper**
- Uses a screenshot plus vision to answer a targeted question about what is visible.
- Returns a concise string that you can parse or branch on in your script.
- Best for reading text like OTP codes, status labels, or field values.

**Example Script**
```js
magicClicker("Create account")
delay(1500)
magicClicker("Email address field")
// ... type text via your own input helpers
magicClicker("Next")
const otp = magicScraper("The 2FA code shown in the SMS notification")
// ... submit otp
```

**Setup**
- Provide your Moondream auth token via Gradle properties (kept out of git):

```properties
# local.properties (project root) OR ~/.gradle/gradle.properties
MOONDREAM_AUTH=YOUR_TOKEN_HERE
```

**Community**

Discord: https://discord.gg/n9nbZUrw

Youtube: https://www.youtube.com/@getsuperpowers

Twitter: [https://x.com/i/communities/2025816983716184465](https://x.com/i/communities/2026071470741635468)



