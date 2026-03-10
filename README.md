# Go-Safe 🛡️

## What it does
Go-Safe is a personal safety and emergency response application designed to keep users secure. It allows users to instantly alert nearby people and trusted emergency contacts when they are in trouble. By utilizing real-time location tracking and a simple "Help/Safe" toggle, the app ensures that distress signals are quickly broadcasted to surrounding users within a 2km radius, fostering a community-driven safety network.

## Features
- **Real-Time Distress Beacon:** Broadcast your live location and "help needed" status to nearby users instantly.
- **2km Proximity Alerts:** Notifications are smartly routed only to people within a 2000-meter radius to avoid notification spam.
- **Emergency Contacts Management:** Easily add and manage trusted contacts who you can reach out to in critical moments.
- **In-App Messaging:** Secure chat functionality with nearby users responding to your distress signal.
- **"Mark as Safe" Toggle:** Instantly disable the distress beacon and notify responders that you are no longer in danger.

## How I built it
**Stack:** Flutter, Firebase (Authentication, Firestore, Cloud Messaging), Google Maps API
I chose Flutter to easily build a cross-platform mobile application for both iOS and Android from a single codebase, which is crucial for accessibility in emergencies. Firebase handles all backend operations: user authentication, real-time Firestore database for storing user location and distress states, and Cloud Messaging for instant push notifications. A key technical decision was to design a geo-querying logic that selectively fetches and alerts only users within a 2000-meter radius.

## What was hard
One of the main challenges was managing real-time location processing and distance calculation without rapidly depleting the user's battery or hitting Firebase read quota limits. Accurately determining the distance between users and synchronizing state changes (such as toggling between Help and Safe mode and clearing emergency chat states) required careful state management. Additionally, handling background location fetching and ensuring reliable distress status propagation was technically demanding.

## Results / Impact
- Built a fully functional MVP with real-time distress broadcasting capability.
- Optimized the nearby-user query to only sync within a 2km radius, significantly reducing unnecessary database reads and computation overhead.
- Achieved sub-second latency for updating "Help/Safe" status across active nearby clients.

## Prerequisites
Before you begin, ensure you have met the following requirements:
*   [Flutter SDK](https://docs.flutter.dev/get-started/install) (version >=2.12.0 <3.0.0)
*   [Android Studio](https://developer.android.com/studio) or [VS Code](https://code.visualstudio.com/) with Flutter plugins.
*   A Firebase project set up for this application.
*   A Google Maps API Key.

## Installation and Setup
1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/Go-Safe.git
   cd Go-Safe
   ```

2. **Install Flutter Dependencies:**
   ```sh
   flutter pub get
   ```

3. **Configure Firebase & Google Maps:**
   - Create a Firebase project and enable Authentication, Firestore, and Cloud Messaging.
   - Add your `google-services.json` (Android) and `GoogleService-Info.plist` (iOS) to the respective directories.
   - Enable the Maps SDK for Android/iOS in the Google Cloud Console.
   - Insert your Google Maps API key in `android/app/src/main/AndroidManifest.xml` and `ios/Runner/AppDelegate.swift` (or `Info.plist`).

4. **Run the Application:**
   ```sh
   flutter run
   ```

## Usage
1. First-time users will need to register and allow location permissions.
2. Add your emergency contacts using the "Add Contact" feature.
3. In case of an emergency, toggle the switch on the home screen from "Safe" to "Help".
4. Users within a 2km radius will be notified and can contact you or view your location to assist.
