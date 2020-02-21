# Web Application Security Engineer Public Training Resources
This project is focused on providing resources to equip developers or new application security hires for self study and to grow their basic application-layer security testing skills. It is used as a complement to Security PS's 1 on 1 internal, proprietary training. This resource is intended to be minimal but high value. If you are interested in working for Security PS and live in the Kansas City area, please visit [www.securityps.com](https://www.securityps.com) and click "Contact Us" to inquire about a job.

## Building a Foundation For Security Testing
The foundation of a great application security engineer is his or her ability to observe, dissect, and analyze an application. The engineer must understand how an application works. Dynamic scanning and static analysis tools can hunt for vulnerabilities. But, they can't think or make connections between observations. If you, instead, start by gaining a thorough understanding of an application's architecture and construction, severe vulnerabilities will seem to fall in your lap. Ask your self, what happens when you initially visit the application? What do you see in an HTTP proxy in terms of cookies, headers, and request parameters? What steps are involved in logging in, using the forgot password process, and registering? Which cookies and headers does the application use and for what purpose? How much of what you are observing is part of the default framework or template used to develop the application, and how much of it did a developer intentionally design and implement? Try skipping process steps, modifying session cookies, altering URL and POST parameters - Not to find vulnerabilities but to isolate application behavior and determine how everything works. If necessary, build an application using the same technologies and frameworks and learn about its default setup and find out what kind of mistakes are easy to make with that stack. Don't worry about vulnerabilities yet. 

After gaining a thorough understanding of the application, brainstorm potential threats that are particularly relevant due to its business purpose, design, and implementation. Use that context to then execute on test cases that realize those threats. Systematically work through every feature and page of the application, always stopping to think about new potential threats and test cases that must be exercised. Finally, use a list of vulnerabilities and best practices to test the entire application, but apply your knowledge of the application to consider which vulnerabilities apply and how they can be best tested. Go through the application systematically to test for those issues.

## Staring With Software Development
If you haven't written many web applications, these resources will get you started on your journey. Before trying to learn hacking, build lots of web applications. Build traditional web applications and single page applications. Build applications that use a REST API and applications that have an MVC architecture. Build Android applications or iOS applications. Add authentication, user roles, authorization controls, multi-step processes, functionality that accepts a file upload and and process the file, and more. Write lots and lots of code. If you understand how applications are built, you will be tremendously better at finding vulnerabilities later.

After you build an application, proxy the traffic with Burp Suite Community Edition (see below). Ask yourself questions like:
* How does HTTP work?
* When I log in, how does it keep track of who I am?
* What headers am I seeing?
* What cookies does it use?
* What are the cookies for?
* What happens if I change or take away a header or cookie in Burp Suite?
* What parameters are sent either in the URL or POST body?
* What happens if I change those parameters to point at different database IDs or put in invalid characters?

Investigate how the application works from the perspective of the proxy? Alter the HTTP request in ways that you can't in the browser and see what happens. Look at the HTTP response and see what comes back from the server that maybe you didn't realize was there. Get comfortable using a proxy and looking at HTTP requests and responses.

### Getting Started with HTMl, CSS, JavaScript, and SQL
While these are basic resources, they are also classic resources.
* https://www.w3schools.com/html/default.asp
* https://www.w3schools.com/css/default.asp
* https://www.w3schools.com/js/default.asp
* https://www.w3schools.com/sql/default.asp

### Getting Started with C#, ASP.NET, and ASP.NET MVC
* https://dotnet.microsoft.com/learn/videos
  * C# 101
  * .NET Core 101
  * ASP.NET Core 101
  * Nuget 101
  * Intro to Visual Studio
  * Entity Framework Core 101

## Getting Started with Application Security Testing
### Web Application Hackers Handbook, 2nd Edition by Dafydd Stuttard and Marcus Pinto
This resource is a little bit dated but still really good. We like it because it's comprehensive and practical. This should be supplemented with the next resource.
### [Web Security Academy](https://portswigger.net/web-security)
Free, hands on education and labs. This is effectively the "3rd Edition" of the Web Application Hackers Handbook. Portswigger plans to add more and more exercises over time.
### [The Burp Methodology](https://portswigger.net/support/the-burp-methodology)
This resouce provides step by step guidance for finding different classes of vulnerabilities with Portswigger's Burp Suite tool (see the tools section below for more information).
#### Related Resource
* https://portswigger.net/burp/documentation/desktop/penetration-testing

### [OWASP Testing Guide](https://www.owasp.org/index.php/OWASP_Testing_Project)
The Open Web Application Security Project (OWASP) produces free resources to help developers learn about application security. The OWASP Testing Guide walks through a list of vulnerabilities and talks about how to test for those issues.

## Top Tools
### [Burp Suite Community (Free) or Pro Version](https://portswigger.net/burp/communitydownload)
Burp Suite is by far the best man-in-the-middle proxy tool. There are others out there that have really good features too like OWASP ZAP and Fiddler. But, Burp Suite is purpose built to support application-layer security testing. It also can be extended with custom written plugins which often makes the difference between an average and excellent tester.

#### Notable Help Pages
* https://support.portswigger.net/customer/portal/articles/1783055-configuring-your-browser-to-work-with-burp
* https://support.portswigger.net/customer/portal/articles/1783075-installing-burp-s-ca-certificate-in-your-browser
* https://support.portswigger.net/customer/portal/articles/2326039-the-burp-methodology

#### How To Proxy an Application on Localhost (or 127.0.0.1) on Windows
When you run an application locally and attempt to proxy traffic through Burp Suite on Windows, the browser bypasses the proxy and you can't see any of the requests or responses. This happens when you type in something like http://127.0.0.1/ or http://localhost/ in the location bar of a browser. One way to make sure you can see that traffic is to add a host entry, and then type that hostname in to the browser's address bar instead. To create a host entry, open notepad as an administrator by finding it in the start menu, right clicking, and selecting "Run as Administrator". Once Notepad is open, choose File -> Open and type in "c:\windows\system32\drivers\etc\hosts". Add the entry "127.0.0.1 application.local" to the bottom of the hosts file and save the file. An example of the updated host file is shown below.
```
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost
127.0.0.1 application.local
```
Now, when you visit a web application that you host locally, type in http://application.local instead of http://127.0.0.1. The traffic will now flow through the browser correctly as long as you have enabled the proxy in the browser using the help pages above.

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