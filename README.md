📌 **Pinned File:** [Women.ipynb](Women.ipynb)

# Women Safety Analytics System 🚀

An AI-powered **video surveillance system** that processes real-time video to detect persons and vehicles, classify gender, recognize emotions, and detect potential **SOS situations** using advanced AI models.

🔗 **Jupyter Notebook**: [Women.ipynb](https://github.com/ManojM786/Women-Safety-Analytics-System/blob/main/Women.ipynb) (Click to view the full implementation)

---



## 📌 Features
✅ **Person & Vehicle Detection** using **YOLOv8**  
✅ **Gender Classification** using **EfficientNet** (trained on PETA dataset)  
✅ **Facial Emotion Recognition** using **FER Model**  
✅ **Automatic Number Plate Recognition (ANPR)** using **EasyOCR**  
✅ **SOS Gesture Recognition** using **MediaPipe Pose & Hands**  
✅ **Lone Woman Tracking** for enhanced safety analytics  
✅ **Processed Output Video & Reports**  

---

## 🚀 Algorithm

### 🛠 Step 1: Initialization  
- Load **YOLOv8** for detecting persons and cars.  
- Load **EfficientNet Gender Classifier** (trained on PETA dataset).  
- Load **YOLO Face Detector** (for emotion recognition).  
- Load **DeepSORT** for object tracking.  
- Load **Facial Emotion Recognition (FER) Model**.  
- Initialize **EasyOCR** for **Automatic Number Plate Recognition (ANPR)**.  
- Set up **MediaPipe Pose & Hands** for **SOS gesture recognition**.  

### 🎥 Step 2: Process Video Frame-by-Frame  
- Read each frame from the input video.  
- Run **YOLOv8** to detect objects (**persons & cars**).  
- Pass detected objects to **DeepSORT** to track them over time.  

### 🧑‍🤖 Step 3: Process Each Tracked Object  
#### 👥 If the object is a person:  
✔️ Classify **Gender** (Man/Woman) using **EfficientNet**.  
✔️ Store **track ID & gender** to ensure consistency.  
✔️ Draw Bounding Boxes:  
  - 🟦 **Blue** for **Men**  
  - 🟩 **Green** for **Women**  

✔️ If the person is a **woman**:  
  - 🎭 Detect **face** using YOLO (if visible).  
  - 🎭 Classify **facial emotion** using FER.  
  - 🚨 If emotion is **Sad, Fear, Disgust, or Angry** → **Perform SOS detection**.  

#### 🚗 If the object is a car:  
✔️ Extract the bounding box.  
✔️ Run **ANPR** (Automatic Number Plate Recognition).  
✔️ Store detected **license plate numbers**.  

### 🚨 Step 4: SOS Gesture Recognition for Women  
📌 **Performed only if emotion is negative.**  
- Extract **body pose** using **MediaPipe Pose Estimation**.  
- Detect **hand gestures** using **MediaPipe Hands** (**Raised Hand, Waving, etc.**).  
- Detect **running or sudden movements**.  
✔️ **If at least 2 out of 3 conditions are met → Mark as "SOS Detected".**  
✔️ **Draw 🟥 Red bounding box** & log the SOS event.  

### 👤 Step 5: Lone Woman Tracking  
- Track **women who are alone** for **10+ seconds**.  
- If a woman remains alone beyond the threshold, **flag her as Lone Woman**.  

### 📄 Step 6: Generate Outputs  
📌 **Processed Output Video** with bounding boxes.  
📌 **Report (`report.txt`)** including:  
  - Total **Men & Women detected**  
  - Total **SOS cases**  
  - Total **License plates identified**  
  - **Lone women tracking results**  
📌 Car **license plate data** saved in (`car_results.csv`).  

### 🏁 Step 7: Final Processing & Cleanup  
- Release video resources.  
- Print **"Detection Completed"** message.  

---

## 💡 Key Features & Optimizations  
✅ **Gender classification happens immediately** after person detection (**EfficientNet**).  
✅ **Face detection is used ONLY for emotion recognition** (**not gender classification**).  
✅ **DeepSORT ID consistency is improved** (`max_age=90`) to prevent misclassification.  

---

## 📥 Installation  

**Clone the Repository**
```bash
git clone https://github.com/ManojM786/Women-Safety-Analytics-System.git
cd Women-Safety-Analytics-System
```

# Create and Activate a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```
# Install Dependencies

```bash
pip install -r requirements.txt
```
# 🔧 Usage
## Run the Main Notebook

```bash

jupyter notebook Women.ipynb
```
Follow the notebook cells to execute:

✅ Object detection & tracking
✅ Gender classification
✅ Facial emotion recognition
✅ SOS detection & lone woman tracking

# 📊 Results

This system processes real-time video and generates reports detailing:

**✅ Number of detected men & women
✅ Identified SOS cases
✅ Detected vehicle license plates
✅ Tracking lone women in public spaces**


All results are stored in:

**✅Processed output video
✅Report file (report.txt)
✅License plate data (car_results.csv)** 


# 🤝 Contributing

Contributions are welcome! If you want to enhance the system, follow these steps:

**1. Fork the Repository
2. Create a New Branch**
```bash
git checkout -b feature-branch
```
**3. Commit Your Changes**
```bash
git commit -m "Added new feature"
```
**4. Push the Branch**
```bash
git push origin feature-branch
```
**5. Open a Pull Request describing your changes.**


# 📜 License

This project is licensed under the MIT License. See the LICENSE file for details.

# 📩 Contact
For any questions or feedback, feel free to reach out:
**📧 Email: manojdatascientist7@gmail.com
🔗 GitHub: ManojM786**
