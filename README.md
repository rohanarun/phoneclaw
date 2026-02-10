**PhoneClaw**
PhoneClaw is an Android automation app that runs on-device workflows and lets you generate automation logic at runtime using **ClawScript**, a JavaScript-based scripting language built into the app.

PhoneClaw is inspired by Claude Bot/Claude Code and attempts to rebuild the agent loop for android phones natively to act as your personal assistant with access to all your apps. 
**Demos**

Automating Uploading Videos To Tiktok With Songs:

[![Automating Uploading Videos To Tiktok With Songs:](https://img.youtube.com/vi/TRqPFSixaog/0.jpg)](https://www.youtube.com/watch?v=TRqPFSixaog)


Automating Creating Instagram Accounts:
[![Automating Creating Instagram Accounts](https://img.youtube.com/vi/9zR43vLYCMs/0.jpg)](https://www.youtube.com/watch?v=9zR43vLYCMs)

Automating Captchas:

[![Automating Captchas:](https://img.youtube.com/vi/aBgbr27fR5M/0.jpg)](https://www.youtube.com/watch?v=aBgbr27fR5M)


**ClawScript**
ClawScript is a JS scripting language that runs inside PhoneClaw and allows generating automations at runtime on Android. You can chain UI actions, scrape on-screen data, and build flexible flows without hardcoding coordinates.

**magicClicker(description)**
- Uses an on-screen screenshot plus vision to locate a target described in plain language.
- Taps the best-matching UI element through the Accessibility service.
- Best for repeatable flows where the UI layout may shift between devices.

**magicScraper(description)**
- Uses an on-screen screenshot plus vision to answer a targeted question about what is visible.
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
- Add your Firebase config at `app/google-services.json`.
- Provide your Moondream auth token via Gradle properties (kept out of git):

```properties
# local.properties (project root) OR ~/.gradle/gradle.properties
MOONDREAM_AUTH=YOUR_TOKEN_HERE
```

**Security**
- Do not commit API keys or service credentials. Use `local.properties` or your global Gradle properties for secrets.
