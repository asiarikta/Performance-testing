
Introduction




This document explains how to run a performance test with JMeter against a Booking.

Installations
Java

  https://www.oracle.com/java/technologies/downloads/
JMeter

https://jmeter.apache.org/download_jmeter.cgi
Click =>Binaries
=>apache-jmeter-5.6.3.zip

We use BlazeMeter,Lighthouse to generate JMX files

https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en,

https://chromewebstore.google.com/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk

Prerequisites
As of JMeter 5.6, Java 8+ and above are supported.
we suggest multicore cpus with 4 or more cores.
Memory 16GB RAM is a good value.
Elements of a minimal test plan
Thread Group

The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

HTTP Request Default (Configuration Element)

HTTP Request (Sampler)

Summary Report (Listener)

Test Plan
Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the jMeter version you are using)

Name: Users

Number of Threads (users): 1 to 30

Ramp-Up Period (in seconds): 3

Loop Count: 3

i. The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

ii. All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

iii. Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

iv. The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

Test execution (from the Terminal)
keep your jmx file in bin
JMeter should be initialized in non-GUI mode.
Make a report folder in the bin folder.
Run Command in jmeter\bin folder
Command

 file generate command
 
![Capture](https://github.com/user-attachments/assets/03b5989a-9e6f-45ec-978a-2951f7765a2b)

![Capture2](https://github.com/user-attachments/assets/c3add445-1145-47f3-967c-db437e144dfe)


jmeter -n -t Booking.jmx -l report\Booking.jtl
jmeter -n -t Ecommerce.jmx -l report\Ecommerce.jtl
Report Generate command
![pic 3](https://github.com/user-attachments/assets/4002846c-c3d8-403c-ad86-0cd4d3c7bfc2)


![pic2](https://github.com/user-attachments/assets/cc674a2e-5f8a-491f-86fc-71fbdd34a2ab)

jmeter -g report\Booking.jtl -o report\Booking.html
jmeter -g report\Ecommerce.jtl -o report\Ecommerce.ht
