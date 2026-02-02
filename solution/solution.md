🟢 STEP 1: Check the file type
file final.png


Expected output:

final.png: PNG image data

🟢 STEP 2: Inspect image metadata
exiftool final.png


Look carefully for this line:

Comment : U2FsdGVkX1/30fQUBkFIGHKlTiMIG5L3DMDKggCwZGk=

🟢 STEP 3: Decrypt the encrypted metadata

Use OpenSSL to decrypt it.

echo "U2FsdGVkX1/30fQUBkFIGHKlTiMIG5L3DMDKggCwZGk=" | \
openssl enc -aes-256-cbc -a -d -pass pass:SECE_FORENSICS

Output:
WelcometoSECE

🟢 STEP 4: Check for hidden files inside the image
binwalk final.png


You will see:

Zip archive data

🟢 STEP 5: Extract the hidden ZIP
unzip final.png


When prompted for password, type:

WelcometoSECE


After extraction, you get:

inside.jpeg

🟢 STEP 6: Analyze the extracted image
file inside.jpeg


Output:

JPEG image data

🟢 STEP 7: Extract readable strings from the image
strings inside.jpeg


To directly locate the flag:

strings inside.jpeg | grep SECE

🏁 FINAL FLAG
SECE{image_inside_image}
