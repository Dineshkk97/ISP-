# ISP-
Detecting Phishing Websites Using Machine Learning 

1.Open the Chrome browser on your computer.

2.Access the Extensions page: Type "chrome://extensions" in the address bar and press Enter. This will take you to the Chrome Extensions page.

3.Enable Developer Mode: In the top-right corner of the Extensions page, toggle the "Developer mode" switch to enable it. This allows you to load unpacked extensions.

4.Load your extension: Click on the "Load unpacked" button that appears after enabling Developer mode. A file selection dialog will open.

5.Locate your extension directory: Browse to the directory where you have stored your extension files and select it. Click "OK" to proceed.

6.Confirm installation: After selecting your extension directory, Chrome will load and install the extension. Once the process is complete, your extension will appear in the list of installed extensions on the Extensions page.

The Phishing Detection Chrome Extension aims to classify, every browsed URL, under phished and non-phished category(on page load).
thereby, alerting the user of any malicious activity and prevent intrusion.

 
**1. manifest.json:**
It provides Chrome with the basic information about the extension like name, permissions, associated scripts and files.

**2.content.js:**
It runs in separate unprivileged javscript environment and has complete access to the DOM.
Here, the trained 'SVM model' (weights calculated in ./ML Algorithm Evaluation/run_algorithms.py) has been used as a persistent model to classify websites.
Below functions compute feature vector for the portal under analysis:
- isIPInURL()
- isLongURL()
- isTinyURL()
- isAlphaNumericURL()
- isRedirectingURL()
- isHypenURL()
- isMultiDomainURL()
- isFaviconDomainUnidentical()
- isIllegalHttpsURL()
- isImgFromDifferentDomain()
- isAnchorFromDifferentDomain()
- isScLnkFromDifferentDomain()
- isFormActionInvalid()
- isMailToAvailable()
- isStatusBarTampered()
- isIframePresent()

The evaluated feature vector, further, passed to predict(data) function reckons the prediction for the website.

**3. background.js:**
In case, we need access to external extensions or APIs, it is a requisite to create means of communication between the content.js and privileged parts of the our extension, and this interaction is termed as message passing. Message passing allows different components of our extension to collabrate.
