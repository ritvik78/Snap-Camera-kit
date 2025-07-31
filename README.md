# Snap-Camera-kit
# Camera Kit Unity Template (Simplified)

> **Note:** This example project helps you integrate Snap’s Camera Kit into Unity apps. Use at your own risk—it’s not production supported.

## ✅ Requirements

* **Unity:** 2022.3.17f1
* **Camera Kit SDK:** 1.26.1
* **Android:** Android Studio (min SDK 22, target 33), Gradle 7.2
* **iOS:** XCode 15, Cocoapods

## 📁 Project Structure

* `unity/`: Main Unity project
* `android-app/`: Android wrapper
* `ios-app/`: iOS wrapper
* `lenses/`: Sample lenses

## 🚀 Getting Started

### Step 1: Set Up Your Snap Account

* Create a [Camera Kit developer account](https://camera-kit.snapchat.com/)
* Get: **App ID**, **API Token**, **Lens Group ID**

---

### Step 2: Android Setup

1. In Unity:

   * Open `unity/`, go to **Camera Kit Settings**, and enter App ID + API Key
   * Build Settings → Platform: Android, check **Export Project**
   * Output to `unity/exports/unity-android-export/`
2. In Android Studio:

   * Open `android-app/`

---

### Step 3: iOS Setup

1. In Unity:

   * Platform: iOS → Build → Export to `exports/unity-ios-export/`
2. In XCode:

   * Open `main.xcworkspace`, set up signing and capabilities for `UnityWithCameraKit`

---

## 🧠 Development Flow

* Use Unity for development.
* Export to native build tools (Android Studio / XCode) for deployment.

---

## 📦 Example Code

### Launch Camera Kit

```csharp
var config = new CameraKitConfiguration() {
    LensId = "abc123",
    LensGroupId = "group123"
};
CameraKitHandler.InvokeCameraKit(config);
```

### Handle Capture Result

```csharp
void OnEnable() {
    CameraKitHandler.OnCaptureFinished += OnCaptured;
}
void OnCaptured(string filePath) {
    Debug.Log("Captured: " + filePath);
}
```

---

## 📡 Remote API (Unity ↔ Lens)

1. Define API in [Snap Portal](https://my-lenses.snapchat.com/apis)
2. Use JavaScript in Lens to send/receive data
3. Handle data in Unity C# via event callbacks

---

## 🧩 API Summary

### Key Events:

* `OnCaptureFinished`
* `OnResponseFromLensEvent`
* `OnLensRequestedUpdatedState`

### Key Methods:

* `InvokeCameraKit(config)`
* `DismissCameraKit()`
* `UpdateLensState(state)`

---

## 📚 Resources

* [Snap Camera Kit Docs](https://docs.snap.com/camera-kit)
* [Lens Studio](https://lensstudio.snapchat.com)

---

Let me know if you want an even shorter quickstart, or a PDF/exportable version.
