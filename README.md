# Fasting Reminder

A comprehensive iOS shortcut that automatically notifies you at Suhoor and Iftar times based on your location and manages alarms accordingly — so you never miss a fast.


## Features

- **Location-Based Prayer Times** — Automatically fetches accurate Suhoor and Iftar timings tailored to your current coordinates using the [AlAdhan API](https://aladhan.com).
- **Smart Alarm Automation** — Seamlessly schedules and cleans up fasting alarms without requiring manual updates.
- **iOS Shortcuts Integration** — Runs unobtrusively in the background via automated iOS Shortcuts routines.
- **Customizable Fast Tracking** — Flexible configuration allowing you to toggle tracking for specific obligatory or voluntary observances.


## Supported Fasts

| Fast / Observance | Hijri Timing | Classification |
| :--- | :--- | :--- |
| **Ramadan** | Full Month (Month 9) | Obligatory (*Fard*) |
| **Day of Arafah** | 9th Dhul Hijjah | Voluntary (*Sunnah*) |
| **Day of Ashura** | 10th Muharram | Voluntary (*Sunnah*) |
| **Ayyam al-Beed** | 13th, 14th, & 15th of each Hijri month | Voluntary (*Sunnah*) |
| **Mondays & Thursdays** | Weekly recurring | Voluntary (*Sunnah*) |
| **Six Days of Shawwal** | Post-Eid al-Fitr (Manual Mode) | Voluntary (*Sunnah*) |


## Installation & Setup

### Step 1: Install Required Apps

- Download **[Scriptable](https://apps.apple.com/us/app/scriptable/id1405459188)** from the iOS App Store.
- Download the **[Fasting Reminder Shortcut](https://github.com/iamrayyaann/fasting-ios-shortcut/blob/main/Fasting%20Reminder.shortcut)** or import it using the link provided in the repo description.

### Step 2: Initial Configuration

- Open the imported shortcut and scroll down to the **setup section**.
- Set the value for **`setupState`** to **`True`**.

![Setup State Configuration](images/setup-state.png)

- Navigate to **Settings > Apps > Shortcuts > Advanced** on your iOS device and enable:
   - **Allow Running Scripts**
   - **Allow Deleting Without Confirmation**

![Shortcuts Configuration](images/shortcuts-config.png)

- Run the shortcut manually for the first time.
- When the iOS permissions dialog appears, tap **"Delete Always"** to grant necessary alarm management permissions.

![Delete Permission Dialog](images/delete-permission.png)

- Return to the shortcut setup section and set **`setupState`** back to **`False`**.
   - *Optional:* Run the shortcut once more to confirm permissions are saved and prompts no longer appear.

### Step 3: Customize Your Fasts

- Scroll through the shortcut logic to locate the **list of Islamic fasts**.
- Disable or remove any fasts you do not intend to observe (you can re-enable them anytime).

![Fasting List](images/fasting-list.png)

### Step 4: Set Up Automations

1. Open the **Shortcuts** app and navigate to the **Automation** tab.
2. Create **three separate daily time-based automations**:

| Automation | Suggested Time Window | Target Action |
| :--- | :--- | :--- |
| **Automation 1** | **2:00 AM – 4:00 AM** (e.g., 3:00 AM) | Sets the daily Suhoor alarm |
| **Automation 2** | **4:00 PM – 6:00 PM** (e.g., 5:00 PM) | Sets the daily Iftar alarm |
| **Automation 3** | **8:00 PM – 9:00 PM** (e.g., 8:30 PM) | Deletes expired alarms |

3. For each of the three automations, configure the following settings:
   - Set to **Run Immediately**
   - Toggle **off** "Notify When Run"
   - Select the action to run the **Fasting Reminder** shortcut

![Automation Configuration](images/automation-config.png)


## Usage

Once fully configured, the shortcut operates automatically in the background. No daily manual interaction is necessary — alarms are generated and deleted based on your scheduled fasts.

### Manual Mode (Fast Everyday)

For voluntary fasts such as the **Six Days of Shawwal** or continuous fasting periods:

1. Open the shortcut and set **`Fast Everyday`** to **`True`**.
2. The shortcut will calculate and trigger alarms for every consecutive day.
3. **Remember** to set **`Fast Everyday`** back to **`False`** once your fasting period concludes.


## Known Limitations

| Issue | Description |
| :--- | :--- |
| **Shawwal Fast Tracking** | The Six Days of Shawwal are not automatically scheduled since they can be observed on any six days throughout the month. Use **Fast Everyday** mode as a workaround. |
| **Scriptable Dependency** | The shortcut requires the Scriptable app to handle background logic and API processing. |
| **Internet Dependency** | Prayer times are fetched dynamically via network requests; offline execution is not supported. |
| **Location Access** | Location permissions must be granted to accurately compute local Suhoor and Iftar timings. |


## License

This project is open source and available under the [MIT License](LICENSE).
