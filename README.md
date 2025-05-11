# 📥 How to Download Protected View-Only Files from Google Drive

This guide shows you how to download files from Google Drive that are in view-only or protected mode.

## 📄 Downloading PDF Files

### Prerequisites
- A Google Drive file in view-only or protected mode
- A modern web browser (Chrome, Firefox, Edge, or Safari)

### Steps

1. 🔍 **Open the File**
   - Open or preview the view-only file in Google Drive

2. 🛠️ **Open Developer Console**
   | Browser | Windows/Linux | macOS |
   |---------|--------------|--------|
   | Chrome/Firefox | `Shift + Ctrl + J` | `Option + ⌘ + J` |
   | Microsoft Edge | `Shift + Ctrl + I` | - |
   | Safari | - | `Option + ⌘ + C` |

3. ⌨️ **Execute the Code**
   - Navigate to the "Console" tab
   - Copy and paste the following code:

   ```javascript
   let jspdf = document.createElement("script");
   jspdf.onload = function () {
       let pdf = new jsPDF();
       let elements = document.getElementsByTagName("img");
       for (let i in elements) {
           let img = elements[i];
           if (!/^blob:/.test(img.src)) {
               continue;
           }
           let canvasElement = document.createElement('canvas');
           let con = canvasElement.getContext("2d");
           canvasElement.width = img.width;
           canvasElement.height = img.height;
           con.drawImage(img, 0, 0, img.width, img.height);
           let imgData = canvasElement.toDataURL("image/jpeg", 1.0);
           pdf.addImage(imgData, 'JPEG', 0, 0);
           pdf.addPage();
       }
       pdf.save("download.pdf");
   };
   jspdf.src = 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js';
   document.body.appendChild(jspdf);
   ```

4. ⏳ **Wait for Download**
   - The PDF file will start downloading automatically
   - Download time depends on the file size

## 🎥 Downloading Video Files

### Steps

1. 🔍 **Access the Video**
   - Open or preview the video file in Google Drive

2. 🛠️ **Open Developer Tools**
   - Use the same keyboard shortcuts as above to open Developer Tools
   - Navigate to the "Network" tab

3. 🔎 **Find the Video Source**
   - Search for:
     - `mime=video` (for video without audio)
     - `mime=audio` (for audio only)
   - Right-click on the largest file
   - Select "Copy" then "Copy URL"

4. 🔗 **Modify the URL**
   - Open a new browser tab
   - Paste the copied URL
   - ⚠️ **Important**: Remove everything from `&range` onwards in the URL
   
   Example:
   ```
   https://rr1---sn-npoe7nek.c.drive.google.com/videoplayback?expire=1741540955&ei=...
   ```

5. ⏬ **Download**
   - The video will start downloading automatically
   - Download time varies based on file size

> ⚠️ **Note**: This guide is for educational purposes only. Please respect copyright and terms of service when downloading files.

