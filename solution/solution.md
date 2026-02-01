# 🧠 Solution – (Forensics CTF)

This document explains the complete step-by-step solution to crack the
forensics challenge and retrieve the flag.
-

## 📁 Given File
- `final.png`

At first glance, the file opens as a normal cyber-themed image.

---

## 🔍 Step 1: Analyze the file structure

Open a terminal in the folder containing `final.png` and run:

```bash
binwalk final.png

##📦 Step 2: Extract the hidden ZIP archive

Attempt to extract the ZIP file from the image:

unzip final.png


You will be prompted for a password:

WelcometoSECE


After entering the correct password, a file named inside.jpeg is extracted.

##🖼 Step 3: Inspect the extracted image

The extracted file inside.jpeg also appears to be a normal image.
To check for hidden information, use the strings command:

strings inside.jpeg

##🚩 Step 4: Retrieve the flag

Among the readable strings in the image, the flag can be found:

SECE{image_inside_image}

##✅ Final Flag
SECE{image_inside_image}

