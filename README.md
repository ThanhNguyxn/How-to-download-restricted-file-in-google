# How-to-download-protected-view-only-file-from-google-drive??

1. Open or Preview Any view-only or protected files from google drive.

2. Open Developer Console.
    If you are previewing in Google Chrome or Firefox
    Press Shift + Ctrl + J ( on Windows / Linux) or Option + ⌘  + J (on Mac)
    If you are previewing in Microsoft Edge 
    Press Shift + Ctrl + I 
    If you are previewing in Apple Safari
    Press Option + ⌘ + C
    Then you will find yourself inside the developer tools.
    
3.  Navigate to the "Console" tab.

4.  Paste below code and press Enter:

        let jspdf = document.createElement( "script" );
        jspdf.onload = function () {
        let pdf = new jsPDF();
        let elements = document.getElementsByTagName( "img" );
        for ( let i in elements) {
        let img = elements[i];
        if (!/^blob:/.test(img.src)) {
        continue ;
        }
        let canvasElement = document.createElement( 'canvas' );
        let con = canvasElement.getContext( "2d" );
        canvasElement.width = img.width;
        canvasElement.height = img.height;
        con.drawImage(img, 0, 0,img.width, img.height);
        let imgData = canvasElement.toDataURL( "image/jpeg" , 1.0);
        pdf.addImage(imgData, 'JPEG' , 0, 0);
        pdf.addPage();
        }
        pdf.save( "download.pdf" );
        };
        jspdf.src = 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js' ;
        document.body.appendChild(jspdf);

5. Now, the pdf file start to download. This might take a few minutes depending on the file size.

Bonus u can use simpler way https://chromewebstore.google.com/detail/document-preview-exporter/npapjbliocdhineglcjkmmmaddpgeono 

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

# HHow-to-download-protected-view-only-video-from-google-docs??

The script below isn't the fastest way to copy-and-paste from a protected 
Google Doc. Before trying it, I'd suggest following MikoFrosty's advice from 
the comments:
1) Change the end of the document url from `/edit` to `/mobilebasic`.
2) Disable Javascript (as described in steps 2 and 3 below).
3) Keeping the console open, reload the page.
That should be enough to allow you to copy freely. The script here is 
*probably* only necessary if the /mobilebasic view isn't rendering something 
correctly.
HOW TO USE
----------
1) Open the protected Doc using Chrome. Scroll all the way down to the bottom 
to make sure that it is entirely loaded.
2) Open Chrome Developer Tools (<Ctrl+Shift+I>), and click "Console" to open 
the Javascript Console.
3) Open the Command Console (<Ctrl+Shift+P>). Type "javascript", and select 
the option "Disable Javascript" when it appears.
4) Copy the script below into the Javascript console.
5) Leaving the Javascript Console open, you may now copy-and-paste from the 
document as normal. (Some formatting may be broken. Closing the console may 
re-lock copy-and-pasting.)
6) (OPTIONAL) To copy the entire document as plain text (no formatting), type 
the following into the console: 
    document.body.innerText
The text will be loaded into the Console itself; copy it by clicking the 
gray-highlighted "COPY" at the end.
*/
    [code.txt](https://github.com/user-attachments/files/19820856/code.txt)


