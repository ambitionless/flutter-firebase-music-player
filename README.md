# 🎵 Spotify Clone in Flutter — Built with Firebase & just_audio 🎧

This is a Spotify-inspired music streaming app built with **Flutter**, powered by **Firebase** and the `just_audio` + `audio_service` libraries for seamless audio playback — even in the background!

> Developed & Maintained by [Hemant Kumar](https://github.com/your-github-username)

---

## ✨ Features
- 🎨 **Beautiful UI** with Flutter – Playlist & Song views
- 🎧 **Background Music Playback** – using `just_audio` + `audio_service`
- ☁️ **Firebase Integration** – Firestore for data + Cloud Storage for songs
- 🧠 Clean & scalable code structure

---

## 📽️ Video Demo
Check out the full video tutorial and walkthrough:  
[▶️ Watch on YouTube](https://youtu.be/DSrOgDzghJk)

---

## 🚀 Getting Started

Before running the app, set up Firebase & upload your assets.

### Step 1: Set up Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Firestore & Storage
4. Add Android/iOS support and download the `google-services.json` / `GoogleService-Info.plist`

---

### Step 2: Upload Songs to Firebase Storage
- Navigate to `Build > Storage`
- Upload your `.mp3` or `.wav` files

---

### Step 3: Add Playlist & Song Data to Firestore

Here’s how you can push your playlists and song metadata into Firestore:

```dart
Future<String> set({
  required String id,
  required String entity,
  required Map<String, dynamic> data,
}) async {
  try {
    return await _firestore.collection(entity).doc(id).set(data);
  } catch (err) {
    throw Exception('Error adding document: $err');
  }
}

To add recommendations:
Future createUserRecommendations() async {
  dbClient.set(
    entity: 'userRecommendations',
    data: UserRecommendations.sampleUserRecommendations.toJson(),
  );
}

Call this in your main app startup:
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );

  final dbClient = FirestoreDbClient();
  final playlistRepo = PlaylistRepository(dbClient: dbClient);
  playlistRepo.createUserRecommendations();

  runApp(const MyApp());
}

Run the App
flutter pub get
flutter run

Folder Structure (Brief Overview)
lib/
├── models/         # Data models for Song, Playlist, etc.
├── services/       # Firebase, audio player services
├── ui/             # Screens and UI components
├── repository/     # Handles Firestore data operations
└── main.dart       # App entry point

About Me
Hi, I’m Hemant Kumar – a passionate Flutter & AI Developer.
📫 Reach me at: hk078085@gmail.com
🌐 GitHub: github.com/your-github-username

⭐ Credits
Special thanks to the original inspiration from @JohannesMilke and the open-source Flutter community. 🙌

📝 License
This project is open-sourced under MIT License — use, modify, and build on it freely.

