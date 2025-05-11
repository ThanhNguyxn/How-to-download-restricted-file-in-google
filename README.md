# 📥 Download Google Drive Protected Files

This guide explains how to download files from Google Drive that are in view-only or protected mode. Please use this responsibly and respect copyright laws.

## 🚀 Quick Start

1. Open your view-only Google Drive file
2. Open browser Developer Tools
3. Follow instructions below for your file type (PDF or Video)

## 💻 Browser Shortcuts for Developer Tools

| Browser | Windows | Mac |
|---------|---------|-----|
| Chrome/Firefox | `Ctrl + Shift + J` | `⌘ + Option + J` |
| Edge | `Ctrl + Shift + I` | - |
| Safari | - | `⌘ + Option + C` |

## 📄 Download PDF Files

1. **Open the PDF file** in Google Drive viewer
2. **Open Developer Console** (use shortcuts above)
3. **Copy and paste this code** into the console:

```javascript
// Add jsPDF library to document
let jspdf = document.createElement("script");
jspdf.onload = function () {
   // Create new PDF document
   let pdf = new jsPDF();
   
   // Get all images from the document
   let elements = document.getElementsByTagName("img");
   
   // Process each image
   for (let i in elements) {
      let img = elements[i];
      if (!/^blob:/.test(img.src)) {
         continue;
      }
      
      // Create canvas and draw image
      let canvasElement = document.createElement('canvas');
      let con = canvasElement.getContext("2d");
      canvasElement.width = img.width;
      canvasElement.height = img.height;
      con.drawImage(img, 0, 0, img.width, img.height);
      
      // Convert to JPEG and add to PDF
      let imgData = canvasElement.toDataURL("image/jpeg", 1.0);
      pdf.addImage(imgData, 'JPEG', 0, 0);
      pdf.addPage();
   }
   
   // Save the PDF file
   pdf.save("download.pdf");
};
jspdf.src = 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js';
document.body.appendChild(jspdf);
```
4. **Wait for Download** - The PDF will start downloading automatically

5. Now, the pdf file start to download. This might take a few minutes depending on the file size.

# How-to-download-protected-view-only-video-from-google-drive??

1. Open or Preview Any view-only or protected files from google drive.

2. Open Developer Console.
    If you are previewing in Google Chrome or Firefox
    Press Shift + Ctrl + J ( on Windows / Linux) or Option + ⌘  + J (on Mac)
    If you are previewing in Microsoft Edge 
    Press Shift + Ctrl + I 
    If you are previewing in Apple Safari
    Press Option + ⌘ + C
    Then you will find yourself inside the developer tools.
    
3.  Navigate to the "network" tab.

4.  Search : 
    mime=video ( video without audio)
    mime=audio ( audio only ) 
    Then you will right click on any file (recommended the largest file size). Select Copy then Copy Url. Finally, open a new browser, paste the copied paragraph and delete from &range onwards. 
   
5. Now, the pdf file start to download. This might take a few minutes depending on the file size.

