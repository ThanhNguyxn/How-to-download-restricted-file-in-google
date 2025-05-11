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

4. **Wait** for the PDF to download automatically

## 🎥 Download Video Files

1. **Open the video** in Google Drive
2. **Open Developer Tools** Network tab (use shortcuts above)
3. **In the Network tab:**
   - Type `mime=video` in the filter box (for video)
   - Or `mime=audio` (for audio track)
   - Look for the largest file size
4. **Get the video URL:**
   - Right-click the largest file
   - Select "Copy" → "Copy URL"
5. **Modify the URL:**
   - Open a new tab
   - Paste the URL
   - ⚠️ Remove everything after `&range=` in the URL
   Example:
   ```
   https://rr1---sn-npoe7nek.c.drive.google.com/videoplayback?expire=1741540955&ei=...
   ```
6. The video will start downloading automatically

## ⚠️ Important Notes

- This tool is for educational purposes only
- Always respect copyright and terms of service
- Download times depend on file size
- Make sure you have enough storage space
- Some files may be protected by additional security measures

## 🤝 Contributing

Feel free to contribute to this project by:
- Reporting issues
- Suggesting improvements
- Creating pull requests

## 📝 License

This project is for educational purposes. Use responsibly and respect intellectual property rights.

