# Web Application Security Engineer Public Training Resources
This project is focused on providing resources to equip developers or new application security hires for self study and to grow their basic application-layer security testing skills. It is used as a complement to Security PS's 1 on 1 internal, proprietary training. This resource is intended to be minimal but high value. If you are interested in working for Security PS and live in the Kansas City area, please visit [www.securityps.com](https://www.securityps.com) and click "Contact Us" to inquire about a job.

## Building a Foundation For Security Testing
The foundation of a great application security engineer is his or her ability to observe, dissect, and analyze an application. The engineer must understand how an application works. Dynamic scanning and static analysis tools can hunt for vulnerabilities. But, they can't think or make connections between observations. If you, instead, start by gaining a thorough understanding of an application's architecture and construction, severe vulnerabilities will seem to fall in your lap. Ask your self, what happens when you initially visit the application? What do you see in an HTTP proxy in terms of cookies, headers, and request parameters? What steps are involved in logging in, using the forgot password process, and registering? Which cookies and headers does the application use and for what purpose? How much of what you are observing is part of the default framework or template used to develop the application, and how much of it did a developer intentionally design and implement? Try skipping process steps, modifying session cookies, altering URL and POST parameters - Not to find vulnerabilities but to isolate application behavior and determine how everything works. If necessary, build an application using the same technologies and frameworks and learn about its default setup and find out what kind of mistakes are easy to make with that stack. Don't worry about vulnerabilities yet. 

After gaining a thorough understanding of the application, brainstorm potential threats that are particularly relevant due to its business purpose, design, and implementation. Use that context to then execute on test cases that realize those threats. Systematically work through every feature and page of the application, always stopping to think about new potential threats and test cases that must be exercised. Finally, use a list of vulnerabilities and best practices to test the entire application, but apply your knowledge of the application to consider which vulnerabilities apply and how they can be best tested. Go through the application systematically to test for those issues.

## Top Resources
### Web Application Hackers Handbook, 2nd Edition by Dafydd Stuttard and Marcus Pinto
This resource is a little bit dated but still really good. We like it because it's comprehensive and practical. This should be supplemented with the next resource.
### [Web Security Academy](https://portswigger.net/web-security)
Free, hands on education and labs. This is effectively the "3rd Edition" of the Web Application Hackers Handbook. Portswigger plans to add more and more exercises over time.
### [OWASP Testing Guide](https://www.owasp.org/index.php/OWASP_Testing_Project)
The Open Web Application Security Project (OWASP) produces free resources to help developers learn about application security. The OWASP Testing Guide walks through a list of vulnerabilities and talks about how to test for those issues.

## Top Tools
### [Burp Suite Community (Free) or Pro Version](https://portswigger.net/burp/communitydownload)
Burp Suite is by far the best man-in-the-middle proxy tool. There are others out there that have really good features too like OWASP ZAP and Fiddler. But, Burp Suite is purpose built to support application-layer security testing. It also can be extended with custom written plugins which often makes the difference between an average and excellent tester.

#### Notable Help Pages
* https://support.portswigger.net/customer/portal/articles/1783055-configuring-your-browser-to-work-with-burp
* https://support.portswigger.net/customer/portal/articles/1783075-installing-burp-s-ca-certificate-in-your-browser
* https://support.portswigger.net/customer/portal/articles/2326039-the-burp-methodology

#### Tips for Using Burp Suite
* Manually crawl the application to identify all the hostnames and URLs related to the application
* Add the application URLs to the Target → Scope tab
* Manually test the application for vulnerabilities. After completing manual testing for a particular feature or URL, right click on relevant requests and choose “Do an active scan”. Make sure you remain logged in in the browser to ensure it tests the application successfully. Review discovered vulnerabilities in the Target tab after clicking on a particular site.
* Use the Repeater tool when you need to manually send lots of payloads for a particular parameter and observe the application’s response. Right click on a request in the Proxy History and choose “Send to repeater”.
* Use the Proxy → Intercept feature when you want to observe modifications to a request or response in the browser.
* To intercept a particular request or response and modify it, go to Proxy → Options and define rules that intercept only the communication you are targeting
* Use Intruder to automatically send a large number of payloads for a particular parameter to the application. You can then click through the results of each request. You can even set up rules to parse out the response and show you a table of results.
* Read about Logger++ and consider how you can identify vulnerabilities through its search criteria

#### Notable Plugins
Many of these plugins can be installed using the BApp Store within Burp Suite.
* JSON Beautifier
* Hackvertor
* Logger++
* Retire.js
* CSP Auditor
* HTML5 Auditor
* Backslash Powered Scanner
* Collaborator Everywhere

