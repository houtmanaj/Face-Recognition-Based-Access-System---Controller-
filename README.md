# Face Recognition-Based Access System (Command-Line Version)

## 📌 Project Overview

This project is a **Face Recognition Access Control System (without GUI)** that runs directly from the terminal. It is designed for **real-world security applications**, with advanced features like:

* Real-time face recognition
* Access control (granted/denied)
* WhatsApp & Telegram alerts
* Image upload to cloud (Imgur)
* Offline mode with automatic syncing
* Sound alerts for access decisions
* Logging of all activities

This version is more **automation-focused** and suitable for:

* Security checkpoints
* Smart door systems
* Surveillance setups

---

## 🧠 How the System Works (Beginner Friendly)

1. **Camera starts**
2. **Face is detected**
3. **Face is aligned** (to improve accuracy)
4. **Features are extracted** using a deep learning model
5. **SVM classifier predicts identity**
6. System decides:

   * ✅ Access Granted
   * 🚨 Access Denied
7. Alerts are sent and logs are saved

---

## ⚙️ Key Features Explained

### 🔹 1. Face Recognition

* Uses **MobileNetV2** to extract facial features
* Uses **SVM (Support Vector Machine)** to classify identities

---

### 🔹 2. Smart Alerts System

* Sends alerts via:

  * 📱 WhatsApp (CallMeBot API)
  * 📩 Telegram Bot

---

### 🔹 3. Image Upload

* Captured images are uploaded to **Imgur**
* A link is sent with the alert message

---

### 🔹 4. Offline Mode (Very Important 🚀)

If internet is NOT available:

* Alerts are saved locally
* Images are queued

When internet returns:

* All pending alerts and uploads are automatically sent

---

### 🔹 5. Sound Feedback

* Plays sound when:

  * Access is granted
  * Access is denied

---

### 🔹 6. Logging System

* Saves all attempts in:

```id="logfile"
access_log.csv
```

Includes:

* Timestamp
* Name
* Confidence
* Status (GRANTED / DENIED)

---

## 🛠️ Requirements

### 📦 Install Python Libraries

Run this:

```bash id="installcmd"
pip install opencv-python numpy tensorflow scikit-learn mediapipe pygame requests joblib cvlib
```

---

## 📁 Project Structure

```id="structure"
project_folder/
│
├── face_access_control.py        # Main script
├── model/
│   ├── embedding_model.keras
│   ├── svm_classifier.pkl
│   ├── label_encoder.pkl
│
├── granted_photos/               # Saved images (granted)
├── denied_photos/                # Saved images (denied)
├── access_log.csv                # Logs
├── pending_alerts.txt            # Offline alert queue
├── pending_uploads.txt           # Offline image queue
│
├── access_granted.wav            # Sound file
├── access_denied.wav             # Sound file
```

---

## 🔐 Configuration (VERY IMPORTANT)

Before running, update these in the code:

### 1. 🖼️ Imgur Client ID

```python id="imgur"
IMGUR_CLIENT_ID = 'your_client_id'
```

👉 Get it from: https://api.imgur.com/

---

### 2. 📱 WhatsApp (CallMeBot)

```python id="whatsapp"
CALLMEBOT_PHONE = 'your_number'
CALLMEBOT_API_KEY = 'your_api_key'
```

👉 Setup guide: https://www.callmebot.com/

---

### 3. 📩 Telegram Bot

```python id="telegram"
TELEGRAM_BOT_TOKEN = 'your_bot_token'
TELEGRAM_CHAT_ID = 'your_chat_id'
```

👉 Create bot via Telegram BotFather

---

## 🚀 How to Run the Project

1. Open terminal in project folder

2. Run:

```bash id="runproj"
python face_access_control.py
```

---

## 🎥 What Happens When You Run It

1. System checks internet connection
2. Starts webcam
3. Shows preview for a few seconds
4. Attempts to detect a face (3 tries)
5. If face is found:

   * Recognizes user
   * Grants or denies access
   * Sends alerts
   * Saves image
6. If no face:

   * Denies access
   * Sends alert

---

## 🔑 Access Control Logic

Access is granted ONLY if:

* Confidence > **90%**
* Name is in authorized list

Example in code:

```python id="authlogic"
AUTHORIZED_NAMES = ["Jerome"]
```

👉 You can add more names:

```python id="authlogic2"
AUTHORIZED_NAMES = ["Jerome", "Alice", "Bob"]
```

---

## 📊 Understanding Output

### Example (Granted):

```
ACCESS GRANTED: Jerome (95.3%)
```

### Example (Denied):

```
ACCESS DENIED
```

---

## ⚠️ Common Issues & Fixes

### ❌ Webcam not opening

* Ensure no other app is using camera
* Try changing camera index

---

### ❌ No face detected

* Improve lighting
* Face camera directly
* Avoid blur

---

### ❌ Alerts not sending

* Check internet connection
* Verify API keys

---

### ❌ Model not loading

* Ensure files exist in `model/` folder

---

## 💡 Best Practices

* Train your model using the GUI version first
* Use high-quality images
* Add multiple users
* Ensure good lighting conditions

---

## 🔄 Workflow Recommendation

1. Use GUI version → collect and train data
2. Use this script → deploy for real-world usage

---

## 🔐 Security Notes

⚠️ Important:

* Do NOT expose your API keys publicly
* Use `.env` or config files for production
* Restrict access to your system

---

## 🚀 Future Improvements

* Add live video streaming
* Integrate with IoT door lock
* Add facial liveness detection
* Deploy on Raspberry Pi

---

## 👨‍💻 Author

Face Recognition Access Control System built using:

* Computer Vision
* Deep Learning
* Automation APIs

---

## 📜 License

Free to use for educational and personal projects.

---

## 🙌 Final Note

This project is more advanced than the GUI version because it includes:

* Automation
* Networking
* Real-world deployment features

If you're a beginner:

1. Understand the flow
2. Test each feature step by step
3. Start with small modifications

You’ll learn a lot about **AI + Security Systems + Automation** 🚀
