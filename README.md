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

## 🎥 Download Video Files

1. **Open the video** in Google Drive
2. **Open Developer Tools** Network tab (use shortcuts above)
3. **Disable copy protection** by pasting this code in the Console tab:
```javascript
function rtcScript() {
    document.oncontextmenu = null;
    document.onselectstart = null;
    document.onmousedown = null;
    document.onclick = null;
    document.oncopy = null;
    document.oncut = null;
    var elements = document.getElementsByTagName('*');
    for (var i = 0; i < elements.length; i++) {
        elements[i].oncontextmenu = null;
        elements[i].onselectstart = null;
        elements[i].onmousedown = null;
        elements[i].oncopy = null;
        elements[i].oncut = null;
    }
    function preventShareThis() {
        document.getSelection = window.getSelection = function() {
            return {isCollapsed: true};
        }
    }
    var scripts = document.getElementsByTagName('script');
    for (var i = 0; i < scripts.length; i++) {
        if (scripts[i].src.indexOf('w.sharethis.com') > -1) {
            preventShareThis();
        }
    }
    if (typeof Tynt != 'undefined') {
        Tynt = null;
    }
}
rtcScript();
setInterval(rtcScript, 2000);
```

4. **In the Network tab:**
   - Type `mime=video` in the filter box (for video)
   - Or `mime=audio` (for audio track)
   - Look for the largest file size
5. **Get the video URL:**
   - Right-click the largest file
   - Select "Copy" → "Copy URL"
6. **Modify the URL:**
   - Open a new tab
   - Paste the URL
   - ⚠️ Remove everything after `&range=` in the URL
   Example:
   ```
   https://rr1---sn-npoe7nek.c.drive.google.com/videoplayback?expire=1741540955&ei=...
   ```
7. The video will start downloading automatically

## ⚠️ Important Notes

1. This guide is for educational purposes only. Do not use it to violate copyright laws.
2. Always respect the rights of content creators and owners.
3. Use this method responsibly and ethically.

