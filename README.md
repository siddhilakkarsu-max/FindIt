# FindIt

**FindIt helps blind and low-vision people find everyday objects and read labels, just by taking a photo and asking.**

Take a photo, then tap a button, type, or say what you're looking for ("where are my keys?", "my Tylenol", "the book titled Blank"). FindIt outlines the item and tells you out loud where it is. It also reads medicine and food labels, books and mail aloud and in large print. Everything runs on your computer: no account, and photos never leave your device.

## How to launch FindIt

### 1. Download the app
1. In this repository, **Download** **`findit-app.zip`**.
2. Find the zip in your **Downloads** folder and **double-click it to unzip**. You'll get a folder called **`findit-app`**.

### 2. Check that you have Python 3
FindIt uses a tiny Python web server to run in your browser.
- **Mac:** Python 3 is usually already installed. If a window asks to install "command line developer tools", click **Install** and wait for it to finish.
- **Windows:** install Python 3 from [python.org](https://www.python.org/downloads/). During setup, **tick "Add python.exe to PATH"**.

### 3. Start FindIt
Open the **`findit-app`** folder and:
- **Mac:** double-click **`Start FindIt (Mac).command`**.
  - The first time, macOS may say it can't be opened. If so, **right-click** the file, choose **Open**, then click **Open** again.
- **Windows:** double-click **`Start FindIt (Windows).bat`**.
  - If Windows shows "Windows protected your PC", click **More info**, then **Run anyway**.

Your browser opens **http://localhost:8765** with FindIt.
**Keep the terminal window open** while you use FindIt. Closing it stops the app.

> Don't double-click `index.html` directly. Browsers block the camera and AI models for files opened that way, so the app will get stuck on "Starting…". Always use the Start file.

### 4. First-time setup (needs internet once)
- **Reading text** works right away. The text reader is included in the folder.
- **Finding objects** (keys, glasses, books…) needs the object finder. Tap **Download the object finder** once (about 150 MB). After that, FindIt works **offline**.

### 5. Use it
1. Click **Take a photo** to choose a photo, or **Use live camera** for your webcam, then **Capture**.
2. **Find:** tap an item button (Keys, Glasses…), or type or say what you're looking for, then tap **Find**. Example: *the book titled Blank*.
3. **Read:** switch to the **Read** tab, choose the type (Medicine, Food, Book…), and tap **Read it**.
4. Results are spoken aloud, so turn your sound on.

Small or sideways text can take 10–60 seconds while FindIt zooms in. Progress is shown.

### Stopping FindIt
Close the browser tab, then close the terminal window. If FindIt is already running when you start it again, close the old terminal window first.

## How it works: ML pipeline

1. **Image model:** OWL-ViT, a zero-shot object detector, draws boxes around anything matching the words you asked for.
2. **OCR:** Tesseract reads text in the photo and on each object found, upright and sideways, and fuzzy-matches it to the name you asked for.
3. **Zooming and augmentation:** for small text, FindIt splits the full-resolution photo into overlapping sections, enlarges and rotates them, and converts them to black and white, then re-reads the most promising spots up close.

## Built with
JavaScript, HTML, CSS and Python · [Transformers.js](https://github.com/huggingface/transformers.js) running OWL-ViT · [Tesseract.js](https://github.com/naptha/tesseract.js) · Web Speech API.

## Important
FindIt uses small on-device models and can make mistakes. **Always check medicine names, doses and expiry dates with a pharmacist or someone you trust.**

Licenses: Transformers.js, ONNX Runtime Web, Tesseract.js, the Tesseract English model and OWL-ViT are Apache-2.0 (license files are in `vendor/`).

*Created by Siddhi Lakkarsu for the Congressional App Challenge.*
