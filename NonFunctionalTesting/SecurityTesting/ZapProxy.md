# ZAP Proxy

* OWASP (Open Web Application Security Project) is worldwide non-profit organization focused on improving the security of software.
* OWASP ZAP (Zed Attack Proxy) is one of the world’s most popular security tool.


![1](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Proxy_concept_en.svg/1200px-Proxy_concept_en.svg.png)
![1](https://img.wonderhowto.com/img/63/85/63563817867426/0/sploit-make-proxy-server-python.1280x600.jpg)

# Concepts
* [Concepts](https://github.com/zaproxy/zap-core-help/wiki/HelpStartConceptsConcepts)






# Setting up your ZAP Environment
* JAVA 8+ : In order to install ZAP you need to install JAVA 8+ to your Windows or Linux system.
* Download ZAP from here - https://github.com/zaproxy/zaproxy/wiki/Downloads
* Install and open ZAP  
* Foxy Proxy - https://www.youtube.com/watch?v=jHGNLvSpaLs

# Starting OWASP ZAP
* The default install directory **C:\Program Files\OWASP\Zed Attack Proxy\ZAP.exe**
* As it is a Java application, alternatively you can run the following command to start it. What it gives you extra configuration like scheduling your penetration test or starting with a particular URL.

* **java -Xmx512m -jar zap-2.7.0.jar**

# Configuring Zap Proxy & Browser
To kick start the security, the following configuration needs to be don
1. Configuring IP and port number 
2. Configuring the certificate

## Setup Proxy in Zap
* In the ZAP UI, go to Tools>Options>Local Proxy
* Make sure the port is set to 8080 (or the port you have configured in your browser)
![1](https://andrewedstrom.com/assets/images/zap2.jpg)

## Proxy Setup in the browser
* 3.2 Open your preferred browser and set up the proxy as shown here (You can use port 8080 as the port)
![1](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/SettingUpBrowser/images/image02.png)
* How to Change Proxy Settings: https://www.wikihow.com/Change-Proxy-Settings

# Generate Zap Certificate
* 3.1 Go to Tools>Options>Dynamic SSL Certificate. Click Generate and then click Save.
* 3.2 Save the certificate in the desired location

# Installing certificate in Browser
* Next, we need to tell our system to trust messages forwarded to us by the ZAP proxy so that we will be able to visit urls that start with https://. To do this, we need to give the Operating System the ZAP proxy’s certificate.
* 3.3 Open your browser and install the Certificate to your browser (Firefox, Chrome, IE) accordingly 
* Go to Options>Privacy & Security>Certificates>View Certificates>Authorities>Import
* Refer: https://2buntu.com/articles/1517/adding-ssl-certificates-from-owasp-zap-a-visual-walkthrough/
* Should see the OWASP Zap Attach Praxy Root CA certificate in the list

# Verify Zap & Browser Communication
* Hit the URL:, it should return Zap welcome page: https://127.0.0.1:8080 or http://zap/ or https://localhost:8080
* Zap Welcome page should appear
![1](https://wpdevkvk.files.wordpress.com/2017/07/93.png?resize=900%2C497)

# ZAP UI

## Default Startup Dialog of Owasp Zap
![](https://cdn-images-1.medium.com/max/900/1*p5deaD3oyywvFx83fLqOZQ.png)

## Modes
![](https://cdn-images-1.medium.com/max/1125/1*8RMpIlHk1tvDV69rJEaI1Q.png)

There are 4 modes;
* **Standard Mode:** Allows you to do anything to any website.
* **Attack Mode:** Active scans any websites.
* **Safe Mode:** Turns off all the harmful features while scanning.
* **Protected Mode:** Allow you to scan websites in a particular scope. It prevents you to scan an unwanted website

# Enable All Tabs
Go to View->Show all tabs

# Shortcuts
Ctl+Alt+p - Session Properties





# Explore 
What is the purpose of import/export of context?

# Context
* Contexts are a way to group relevant URLs, so that ZAP only shows you the traffic you care about.
* Adding a site to the testing scope
* By telling ZAP what the target site is, ZAP can limit the scope of the scan and only scan the target site for vulnerabilities.

* Open the web application that you want to test.
* In Zap you will find your website/application is displayed under sites.
* To add your site to the scope of the test, right click on the target address and select Include in Context>New Context. This will tell * ZAP to perform scans only on this particular site and ignore all other requests and responses.
* Choose a suitable name and set it as a context name (Eg: testfire)
* If your application has multiple sites you can add all of them by right clicking on the URL and selecting “Include in Context”>”TestFire”

![](https://chrisdecairos.ca/content/images/2015/08/Create_Context.png)
![](https://cdn-images-1.medium.com/max/900/1*tYOWTi-nlbOP6tog-zJF1w.png)
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image10.png)


# User Auto-login if logged out (Only for applications with form based authentication)
* Find the right Login Post request 
* Flag As Context - > Form Based Auth Login Request
* Select the username parameter field
* Select the password parameter field


* If user does get logged out during the course of testing, ZAP can automatically log back in so that it can continue with the tests. This functionality only works if your application has form based authentication.

* Log in to your application
* Check for the request that was sent when the application was authenticated (logged in). Right click on the request select “Flag as Context” > “TestFire: Form-based Auth Login request”
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image05.png)

* In the session properties dialog that pops up make sure the Login URL is the same login URL of the application and the POST data is in the textbox. Make sure the username and password parameters are correct by selecting the appropriate username and password parameters from the list.

![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image13.png)

# Add User
* In the left side bar click “Users” in the left side bar.
* Click Add
* Enter the username and password that your application uses
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image03.png)


* Now click on  “Forced User” in the left bar. This tells ZAP which credentials to use if the user is logged out. You can optionally configure multiple users for the same application, but ZAP will only use the user you chose as “Forced User”
* Make sure the user you have added is selected. Click OK
* If Forced User is configured and logged-out indicator is added, a new button should appear at the top called “Forced User Mode”
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image07.png)



# User Log Out detection
* While ZAP is performing scans on the target sites, the session might become invalidated (ZAP may have visited the logout link or the session may have timed out). 
* To make sure ZAP always has an active session to scan, we need to use the logout detection capability of ZAP.

* Log in to your application
* Click on the logout link
* In Zap, navigate to the page which invokes the logout request. Right click and select “Exclude from” > “Scanner”. Click OK.
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image04.png)

* Again right click on the same link and select “Exclude from” > “Spider”
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image01.png)


* Optionally you may identify part of the page source which signifies that a user has logged out. For example in the testfire website, a “Sign in” link is shown only when the user is not authenticated or when the user is logged out.
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image06.png)

* Find the part of the response in ZAP where the “Sign in” text is displayed. Right click on the source code and select “Flag as Context”> “TestFire: Authentication Logged out indicator”. Click “Ok”.
![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image11.png)





# Starting the Spider
By using the Spider, ZAP will try to build up a detailed site map of your target application. ZAP tries to find each and every link, therefore its important to tell ZAP about the all the use cases before starting the spider.

Once the above steps are done. You are ready to start the spider.
Go through all the use cases of your application while still proxying through zap.
In Zap, right click on your application website in left sidebar. Choose Attack>Spider all in Scope

You will see the progress in the below Spider tab.
Wait for the spider to be 100% complete. You can see the links found by ZAP in the left side bar.

![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image00.png)


# Starting the Scanner
By running the scanner, ZAP will try to find vulnerabilities in your application by performing various attacks. Its important to finish spidering before starting the scanner.

Please make sure the spider is complete before starting the scanner
Make sure the user is logged in (Or make sure auto-login is working fine)
In Zap, right click on your application website in the left sidebar. Choose Attack>Spider all in Scope
The scan might take anywhere from 5 minutes to a few hours depending on the size of your application. Please keep checking on your application (to which the proxy is hooked up) to make sure the user is still logged in and also that the site is still up.
Once the scan is complete, you will find the results in the alerts tab

![](https://security.secure.force.com/resource/1425350868000/ZapTutorialImages/ZapImages/RunningScan/images/image12.png)

# Reference
* https://security.secure.force.com/security/tools/webapp/zaprunningscan






All the sites you access via the ZAP Proxy will be listed here. If your website makes a request to another website, you’ll see that under a separate site.

2.1 — Show Only URLs in Scope: You should toggle this option on because the sites section gets ugly after some test. To focus your target website in the sites you should create a new context of your website and keep In Scope option checked. By doing this you will no longer see other websites that you are not interested in.


# Workspace Window:

The workspace window consists of 3 tabs:

3.1 — Quick Start Window: It’s the direct and fastest way of starting an active scan. Enter the target website address in the URL to attack input and hit the attack button. It first crawls the website then performs active scan.

3.2 — Request & Response Window: These are the most used parts of the UI. In the request tab, you see the window is divided into 2 parts. Upper shows request’s header and cookies and the bottom shows the post parameters as being sent to server. The response windows is similar to the request window. Shows the response header and body.
![](https://cdn-images-1.medium.com/max/1125/1*Ez-q4tA2r5WvrZT-v8SmOQ.png)
![](https://cdn-images-1.medium.com/max/1125/1*YKXJ-f-w1nFE4TSZE4VnCw.png)

# Proxying Your Website: JxBrowser

In the earlier version of OWASP ZAP, you had to configure your browser’s proxy to capture requests. But there’s a new cool feature JxBrowser! This is a Chromium-based browser integrated in OWASP ZAP. By default it has all the proxy configuration set up and lets OWASP ZAP to cross all the traffic over it. Hit the Launch Browser and navigate to your website.

![](https://cdn-images-1.medium.com/max/900/1*I4xL_XOSp8x3NfdAZFvOIw.png)


# Navigating Your Website
In order to extract the tree of your website, you need to crawl the website in JxBrowser. You should hit all the features, go thru all possible actions. This phase is very important!

** The more you explore your website, the more you get efficient results.**


# Spidering Your Website
Spidering a website means crawling all the links and getting structure of the website.


# How to pentest a SPA (Single Page Application) Website?
If it’s a SPA website, then you need to tell ZAP more information, in particular that one, parameters represents application structure rather than application data. To do this:

* Double click your Context (in our test it’s a modern AspNet Zero SPA)
* Select the ‘Structure’ tab
* Add the ‘structural’ parameter(s)



 ![](https://cdn-images-1.medium.com/max/1125/1*1Ik4DzP0XEYtNZhVsSIr8w.png)
 
 If you cover all the features and actions of your SPA website, then you don’t need to spider!
 
 # Extensions
 
 There’s an extension marketplace added by the community. You can click the -3 Colored Boxes- icon to show up the list. To install an extension, click on the Marketplace tab and write extension name in the box. Then the click Install Selected button. That’s it! No need to restart.
 
 
There are useful extensions! Some of them I can suggest;
* Active Scanner rules
* Passive Scanner rules
* FuzzDB

![](https://cdn-images-1.medium.com/max/900/1*TEfm5FlLgeUKfSlYVog6yA.png)


# Configure Scan Policy

Before scanning I recommend to set scan policy like shown below; 
From the Analyse menu, select Scan Policy Manager. Click Modify button. In the Scan Policy window set Low => Threshold To All and click Go button. Same as Insane => Strength To All and click Go button. And to save click OK button. This will go all the attacks in memory and makes the scan robust.

![](https://cdn-images-1.medium.com/max/900/1*lgppXnw1AvZVuUQuVsRZlA.png)

# Save the ZAP session
Once you have manually explored the application it would be a good time to save the ZAP session so that you can look at it again.
If your application has multiple roles then you should explore it with each role and save the sessions in separate files.


# Start Attacking
Attacking the target website is very straight forward.

1 — Add your website to the Context. To do this, right click the target website in the left pane. Choose Include in Context and select Default Context. You can create a new context as well. Now you see there comes a new website URL in the pop-up window which adds your website as regular expression. Asterix (*) in URL, means attack all the URLs under this website. Before attacking, you can go thru the other options in the Default Context to fine tune your settings. Finally we click OK button.

![](https://cdn-images-1.medium.com/max/1125/1*2WOpQfx3eYSWdT7gySc4Ug.png)


2 — Show only the URLs in the current scope. By doing this you hide the other websites and you prevent accidental attacks.

![](https://cdn-images-1.medium.com/max/900/1*EUouLjoVduUVckhPaf2Vuw.png)


3 — Run a spider scan to traverse all paths in the website.
![](https://cdn-images-1.medium.com/max/1125/1*YsTFDKIhfnU8N0x6ykMm3A.png)

4 —Attack! This is the main goal. We’ll start Active Scan. An active scan can insert harmful data into your database. So run it only on the allowed websites. When you click Start Scan, it’ll start a progress which can be time consuming depending on the URL count.
![](https://cdn-images-1.medium.com/max/1125/1*LUf1mHRdy-sm8wB-8i4kEw.png)


# Fuzzer
Fuzzing is sending unexpected or random data to the inputs of a website. Normally we validate inputs on client-side that’s why we ignore some problems in the back-end. When you fuzz key inputs (like a main search input of the website or the login page inputs) you can see coding errors and security loopholes. This is an optional security step. 
If you want to run Fuzzer, locate to the request you want to fuzz from left the pane. Right click and choose Attack, then click Fuzz. In the Fuzzer window, you’ll see the request post data. Click on the post data and highlight the text you want to attack. On the right pane, click Add button. You’ll see Payloads window. Click Add button again. In the Add Payload window, choose File Fuzzers from type combo box. Select the file you want to use. This file is a database that will be used to brute force to the input. When it finishes, the results will be listed on the bottom tab called Fuzzer. The ones tagged with Fuzzed are suspicious and needs to be taken care.


![](https://cdn-images-1.medium.com/max/1125/1*jh33btSXZi39T1StKyqLMQ.png)


# Forced Browse
The spider looks for known, organically linked URLs. But the spider cannot find a URL that’s not mentioned anywhere on the website. In that case, forced browsing comes in. Forced Browsing uses brute force dictionaries to check if there are any other hidden URLs like admin panel or something that can be hacked.

![](https://cdn-images-1.medium.com/max/900/1*J_mVBfyzmFZGXO4oM1OQ-g.png)

# Break

Break is a very good function for intercepting and modifying the requests and responses. If you want to change any particular request post data or response data, right click on the site, choose Break, in the Add Break Point window click Save. Now, on the bottom pane you’ll see breakpoint is enabled. From now on all the requests will be intercepted by OWASP ZAP tool. Whenever you make a request from the original website, the ZAP window will bring to front and allow you to modify the request. After you press the green play button on the toolbar, ZAP brings you the response sent by the server. And you can modify response as well. So your browser will retrieve the altered response.

https://cdn-images-1.medium.com/max/900/1*oWEr1IXHP8N-9n-NoqZP_Q.png


# Results & Report
You made a good job till here. Scanned your website for the known vulnerabilities. But without reporting those issues properly, you are not complete.

You can see the issues on the Alerts tab that is located in the bottom pane. In the following screen, there are 5 alerts with colorized flags. If you have no red flag then you are lucky! For those with red flags, first focus on them and fix them asap.

![](https://cdn-images-1.medium.com/max/900/1*fu5fr-4zQRcvsssxnjAu5A.png)


When you click one of the alerts, it shows the related request & response window. There’s a nice reporting tool that generates a neat report file automatically. You can export reports as HTML, XML, JSON, Markdown … I generated a HTML report. You can see it’s a well-organized final report that you can send to any fellow as is.


![](https://cdn-images-1.medium.com/max/900/1*I-93poX8ipmmcl7mqPdBwQ.png)


![](https://cdn-images-1.medium.com/max/900/1*2DAwIEJhgLQd82t5WTgydA.png)



https://www.pitsolutions.ch/blog/wp-content/uploads/2017/09/8.png


Using ZAP, we can perform three types of automated scanning;

Passive scanning – Passive scanning spiders your web-app and scans the responses without altering them. Only potential hazards can be detected by passive scanning
Active scanning – By active scanning, we can both scan and attacks the web-application
Fuzzing – Fuzzing allows us to modify the response from the web-app and view the results instantly


Flexible Scan Policy Management
ZAP provides the flexibility to compose a  scan policy based on the requirement of the tester for every  application. The Scan Policy Manager can be found at Analyse>>Scan Policy Manager under the menu bar.

https://www.we45.com/hs-fs/hubfs/04_Scan_Policy.png

AJAX spidering

AJAX spidering is performed during a penetration test to discover requests on an AJAX-rich web application, which cannot be discovered with the regular Spidering tool. The AJAX spidering window can be accessed via  ZAP -> Tools ->AJAX Spider (on ZAP’s menu bar). The tool has configuration parameters such as maximum depth to crawl, maximum crawl states, maximum duration and other options to prevent the possibility of infinite crawling.


Context includes:
(i)Authentication
(ii)Session management
(iii)Users management



Context: Form based authentication
(I) log-in from target url: https://pr-uat.iptquote.com/login.php

(ii) Login Request POST Data: username={%username%}&password={%password%}&proceed=login

(iii) Set params as: username =password

(iv) Include regex pattern for logged in or logged out response
Regex pattern for logged in response :- \Qa href=”https://pr-uat.iptquote.com/login.php?proceed=logout\E


https://www.toobler.com/wp-content/uploads/2016/03/blogpic3-650x365.jpg


Context: Session Management
https://www.toobler.com/wp-content/uploads/2016/03/blogpic4-650x365.jpg


Context: User management
For user management, we can add 2 users, one valid user let it be the “Existing user” here “superadmin” in our example and other is “Test User” invalid user.

https://www.toobler.com/wp-content/uploads/2016/03/blogpic5-650x365.jpg


# Authentication in ZAP

https://www.swtestacademy.com/zap-authentication/

# Using Your Android Device with OWASP ZAP
https://simplysecure.blog/2017/06/21/using-your-android-device-with-owasp-zap/

Ref:
https://medium.com/volosoft/running-penetration-tests-for-your-website-as-a-simple-developer-with-owasp-zap-493d6a7e182b


Cloth Bleach
Carpet clearner
Plastic bucket
Paste - Aque fressh extra clean pure breath action



Running Penetration Tests for your Website as a Simple Developer with OWASP ZAP
https://medium.com/volosoft/running-penetration-tests-for-your-website-as-a-simple-developer-with-owasp-zap-493d6a7e182b

Good One - Dynamic Scanning with OWASP ZAP for Identifying Security Threats
https://medium.com/@PrakhashS/dynamic-scanning-with-owasp-zap-for-identifying-security-threats-complete-guide-52b3643eee04



https://medium.com/@ethicalevil/how-http-proxies-read-tls-traffic-from-browsers-f15364e91226

OWASP Top 10 2017 — Web Application Security Risks
https://medium.com/@infosecsanyam/owasp-top-10-2017-web-application-security-risks-31f356491712


https://www.slideshare.net/hacker0x01/owasp-top-10-2017-84029876


Automating Security Testing of web applications using OWASP Zed Attack Proxy in Jenkins
https://medium.com/@PrakhashS/automating-security-testing-of-web-applications-using-owasp-zed-attack-proxy-in-jenkins-aa0f9eafdcba

ZAP Penetration Testing Tutorial to Detect Vulnerabilitie
https://medium.com/@Toobler/zap-penetration-testing-a-simple-tutorial-to-detect-vulnerabilities-e9a8311182a9


OWASP Security Knowledge Framework
https://www.peerlyst.com/posts/introduction-owasp-security-knowledge-framework-project

SQL Injection in API - Time and Boolean based
https://medium.com/bugbountywriteup/sql-injection-time-and-boolean-based-27239b6a55e8


APIdays Paris 2018 - Business Security vs. OWASP Top 10, Jean-Baptiste Aviat, CTO, Sqreen
https://www.youtube.com/watch?v=JLZKKTgU30o


Security Champions Playbook
https://www.peerlyst.com/posts/security-champions-playbook-alexander-antukh



Catch vulnerabilities before pushing to production
Avoid PHP SQL injections
Automate security testing in your CI
Integrate security tools in your workflow
How to secure your infrastructure
How to meet your application security needs


https://code.likeagirl.io/links-for-getting-started-in-application-security-cc529d969cc6



https://blog.appsecco.com/automating-discovery-and-exploiting-dom-client-xss-vulnerabilities-using-sboxr-part-1-2e55c120c9e1


Getting Started with AppSec
https://medium.com/faun/getting-started-with-appsec-1dfaf1181e53


https://code.likeagirl.io/pushing-left-like-a-boss-part-4-secure-coding-3a544dd30e20



XSS : Crash Course
https://medium.com/blue-space/xss-crash-course-aee555d525d3


Using Retire.js with ZAP to identify vulnerabilities in JavaScript libraries
https://medium.com/@PrakhashS/using-retire-js-with-zap-to-identify-vulnerabilities-in-javascript-libraries-7baad56690aa


Security Testing for APIs using ZAP
https://medium.com/@PrakhashS/security-testing-for-apis-using-zap-5df8ec07a131


Automating the boring stuff in development using ZAP and Jenkins : continuous Integration
https://medium.com/@PrakhashS/automating-the-boring-stuffs-using-zap-and-jenkins-continues-integration-d4461a6ace1a


Automating Security Testing of web applications using OWASP Zed Attack Proxy in Jenkins
https://medium.com/@PrakhashS/automating-security-testing-of-web-applications-using-owasp-zed-attack-proxy-in-jenkins-aa0f9eafdcba


OWASP Top 10: Real-World Examples (Part 1)
https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-1-a540c4ea2df5

OWASP Top 10: Real-World Examples (Part 2)
https://medium.com/@cxosmo/owasp-top-10-real-world-examples-part-2-3cdb3bebc976

Owasp-Security Knowledge Framework (SKF) Installation Guide
https://medium.com/@priyankajain997/installing-security-knowledge-framework-skf-233f08a6c1ff


OWASP ZAP  Automated Pen Test with Jenkins
https://medium.com/@priyank.it/owasp-zap-automated-pen-test-with-jenkins-e4f155a33f6f


OWASP ZAP — Security testing technique
https://medium.com/@suthagar23/owasp-zap-security-testing-technique-3c6966d1b50


Mubbing system

http://www2.imm.dtu.dk/pubdb/views/edoc_download.php/6823/pdf/imm6823.pdf

Dynamic Scanning with OWASP ZAP for Identifying Security Threats
https://medium.com/@PrakhashS/dynamic-scanning-with-owasp-zap-for-identifying-security-threats-complete-guide-52b3643eee04

https://medium.com/blue-space/xss-crash-course-aee555d525d3


https://medium.com/@PrakhashS/using-retire-js-with-zap-to-identify-vulnerabilities-in-javascript-libraries-7baad56690aa

https://medium.com/@PrakhashS/overview-cross-site-request-forgery-csrf-recommended-approach-for-wso2-products-bb0e2437307

https://www.coveros.com/scripting-authenticated-login-within-zap-vulnerability-scanner/

https://www.coveros.com/running-selenium-tests-zap/
https://medium.com/@PrakhashS/automating-the-boring-stuffs-using-zap-and-jenkins-continues-integration-d4461a6ace1a

https://medium.com/@PrakhashS/automating-security-testing-of-web-applications-using-owasp-zed-attack-proxy-in-jenkins-aa0f9eafdcba


https://medium.com/@Toobler/zap-penetration-testing-a-simple-tutorial-to-detect-vulnerabilities-e9a8311182a9


https://www.we45.com/blog/how-to-integrate-zap-into-jenkins-ci-pipeline-we45-blog


https://cyberarms.wordpress.com/2015/05/03/automatic-web-app-security-testing-with-owasp-zap/


https://dzone.com/articles/scripting-authenticated-login-within-zap-vulnerabi



