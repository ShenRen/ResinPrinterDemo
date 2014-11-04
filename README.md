ResinPrinterDemo
================

This is software for a raspberry pi to drive a resin printer.

Background - Why
Creation Workshop is an awesome tool, but is unable to run on a raspberry pi.  That's okay though!  The standalone host is a slimmed down version of the Creation Workshop software.  This software accepts the files exports from CreationWorkshop and uses those to drive the resin printing process.

But the raspberry pi has only one video output!!
You will connect to your pi via a webpage.  (This is similiar to how you configure your router.)   The raspberry pi will display the image to the projector.

Directions:

Download latest release here:
<release>

On your raspberry pi, run:
sudo apt-get install librxtx-java
java -Djava.library.path=/usr/lib/jni -cp /usr/share/java/RXTXcomm.jar -jar CwHost.jar


Find the ip of your raspberry pi

Open a browser go to the following webpage:
<needs webclient> static content

Or 
Open a browser, postman, etc...
GET
http://raspberrypi:8080/cwhost/machine/motorsoff
http://raspberrypi:8080/cwhost/machine/morotson
http://raspberrypi:8080/cwhost/machine/status
http://raspberrypi:8080/cwhost/machine/movez/-10
http://raspberrypi:8080/cwhost/machine/movez/-1
http://raspberrypi:8080/cwhost/machine/movez/-.025
http://raspberrypi:8080/cwhost/files/list
http://raspberrypi:8080/application.wadl
POST -form-data - file
http://raspberrypi:8080/cwhost/files/upload


Developers
This project was developed using the following: Eclipse ide, Maven to manage, Jersey for easy rest api, rxtx for serial, static html file for web client/interface.  
To run in eclipse:
Clone the project from github
Import into eclipse as a maven project

Run this command on the terminal
sudo apt-get install librxtx-java

Configure your environment
In eclipse, right-click project, left-click "Maven install"
In eclipse, right-click project, left-click "Maven build" and the "Run Configurations" window will appear.  In the "Run Configurations" window, type "exec:java" in the textbox labeled "Goals:".  Left-click on the tab "JRE" and enter "-Djava.library.path=/usr/lib/jni -cp /usr/share/java/RXTXcomm.jar" (no quotes) in the textbox labeled "VM arguments".  Left-click the "Apply" button, then left-click the "Run" button.  The project will run (see example startup output)!

Export a runnable jar
In eclipse, right-click the project, then left-click "Export".  The "Export" window will appear.  Expand the folder labeled "Java", select "Runnable JAR file", then click the button "Next >".  Under the box labeled "Launch Configurations", select the configuration that you used in the "Maven Build" process (the one you did in the "Configure your environment" section above), type in your export destination (for example "/home/ergobot/Documents/CwHost.jar"), click the radio button labeled "Package required libraries into generated JAR", click the button labeled "Finish". 


Running the jar
To run the jar, you will need the properties.config file in the same directory as the jar.  After you have the properties.config file in the same directory as the CwHost.jar file, go to the directory in a terminal, type the following:

java -Djava.library.path=/usr/lib/jni -cp /usr/share/java/RXTXcomm.jar -jar CwHost.jar

Congrats!

