**PhoneClaw**
PhoneClaw is an Android automation app that runs on-device workflows and lets you generate automation logic at runtime using **ClawScript**, a JavaScript-based scripting language built into the app.

**Demos**


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
