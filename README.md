# How-to-download-protected-view-only-fvideiles-from-google-drive??

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
    For example : https://rr1---sn-npoe7nek.c.drive.google.com/videoplayback?expire=1741540955&ei=K6TNZ4e8J56vp84P5oDR8QY&ip=14.231.194.51&id=01683c99c2e038ff&itag=136&source=webdrive&requiressl=yes&xpc=EghonaK1InoBAQ==&met=1741530155,&mh=3C&mm=32,26&mn=sn-npoe7nek,sn-oguelnzr&ms=su,onr&mv=m&mvi=1&pl=23&rms=su,su&sc=yes&ttl=transient&susc=dr&obr=https://drive.google.com&driveid=1whxKtEJMndQGX528Ut_RHnxE6g-ALzAj&app=explorer&eaua=okVpjC1Pk3A&mime=video/mp4&vprv=1&prv=1&rqh=1&gir=yes&clen=18751411&dur=1464.433&lmt=1709909850965142&mt=1741529804&fvip=4&subapp=DRIVE_WEB_FILE_VIEWER&txp=0000224&sparams=expire,ei,ip,id,itag,source,requiressl,xpc,ttl,susc,obr,driveid,app,eaua,mime,vprv,prv,rqh,gir,clen,dur,lmt&sig=AJfQdSswRgIhAPRegWaDI8_6AVzRewGK_hbzPHI6PutJsZdlxRqZ_-BAAiEApshjp8nVQyg2El49pJ5RJjNE0sDINTs_SwmkD4JYaTE=&lsparams=met,mh,mm,mn,ms,mv,mvi,pl,rms,sc&lsig=AFVRHeAwRQIhAMoPlya6tzdV99QNfTyTWgPJY8IQYJdzRFgL8S3YKUcNAiAOh1Iuq7oDYXYa_PWV09bzMpYtuITHWc-WkO-_bVZNiw==&alr=yes&cpn=y_UXF2r7KqcrC99X&c=WEB_EMBEDDED_PLAYER&cver=1.20250304.00.00(&range=0-131954&rn=1&rbuf=0&ump=1&srfvp=1) 
    YOU MUST REMOVE INSIDE THE BRACKETS

5. Now, the pdf file start to download. This might take a few minutes depending on the file size.

