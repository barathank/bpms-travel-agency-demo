JBoss BPM Suite Travel Agency Demo
==================================
This is an online employee travel booking process project. It contains multiple web services for looking up data for the process
and rules to calculate pricing. Furthermore, there are several tasks that can be activated to evaluate pricing and to review the
final booking data before completing the booking.

Welcome to the JBoss BPM Travel Agency!

There are three options available to you for using this demo; local, OpenShift and containerized.


Option 1 - Install on your machine
----------------------------------
1. [Download and unzip.](https://github.com/jbossdemocentral/bpms-travel-agency-demo/archive/master.zip)

2. Add products to installs directory. For example download and add BPMS installer jar into the installs directory.

3. Run 'init.sh' or 'init.bat' file. 'init.bat' must be run with Administrative privileges.

4. Start JBoss BPMS Server by running 'standalone.sh' or 'standalone.bat' in the <path-to-project>/target/jboss-eap-6.4/bin directory.

5. Login to [http://localhost:8080/business-central](http://localhost:8080/business-central)

    ```
     - login for admin and other roles (u:erics / p:bpmsuite1!)
    ```


Option 2 - Install with one click in xPaaS (bpmPaaS)
----------------------------------------------------
After clicking button, ensure `Gear` size is set to `medium`:
  
[![Click to install OpenShift](http://launch-shifter.rhcloud.com/launch/light/Install bpmPaaS.svg)](https://openshift.redhat.com/app/console/application_type/custom?&cartridges[]=https://raw.githubusercontent.com/jbossdemocentral/cartridge-bpmPaaS-travel-agency-demo/master/metadata/manifest.yml&name=travelagency&gear_profile=medium&initial_git_url=)

Once installed you can use the JBoss BPM Suite logins: 

   * u:erics   p: bpmsuite  (admin)

   * u: alan   p: bpmsuite  (analyst)

   * u: daniel p: bpmsuite (developer)

   * u: ursla  p: bpmsuite (user)

   * u: mary   p: bpmsuite (manager)

Current hosting of bpmPaaS is on JBoss BPM Suite 6.0.2 in OpenShift Online.


Option 3 - Generate containerized installation
----------------------------------------------
The following steps can be used to configure and run the demo in a container

1. [Download and unzip.](https://github.com/jbossdemocentral/bpms-travel-agency-demo/archive/master.zip)

2. Add product installer to installs directory. For example download and add BPMS installer jar into the installs directory.

3. Copy contents of support/docker directory to the project root.

4. Build demo image

	```
	docker build -t jbossdemocentral/bpms-travel-agency-demo .
	```
5. Start demo container

	```
	docker run -it -p 8080:8080 -p 9990:9990 jbossdemocentral/bpms-travel-agency-demo
	```
6. Login to http://&lt;DOCKER_HOST&gt;:8080/business-central
  
    ```
     - login for admin and other roles (u:erics / p:bpmsuite1!)
    ```
    
*Note*: Replace localhost with DOCKER_HOST when it appears in other locations within the documentation

Additional information can be found in the jbossdemocentral docker [developer repository](https://github.com/jbossdemocentral/docker-developer)


Booking a trip to Edinburgh (just one scenario)
-----------------------------------------------
1. Build & deploy project.

2. Start process with following data in start form (either from JBoss BPM Suite dashboard or using external client
	 UI deployed at [http://localhost:8080/external-client-ui-form-1.0](http://localhost:8080/external-client-ui-form-1.0)):

  ```
  Name: [your-name]

  Email Adress: [any-email]

  Number of Travellers: 2  

  From Destination: London

  To Destination: Edinburgh

  Preferred Date of Departure: 2014-12-20

  Preferred Data of Arrival: 2014-12-29

  Other Details / Notes: [any-text]
  ```

3. Login to [http://localhost:8080/business-central](http://localhost:8080/business-central)

  ```
  - login for admin role (u:erics / p:bpmsuite1!)
  ```

4. Two web services will be run and a sub-process to calculate the cost before deciding it is not needed that this booking be
	 reviewed on pricing, so you will find a task 'Employee Booking' for you to process.

5. Navigate to the "Tasks" tab -> "Task List" and click on it. 

6. Expand the right-side pane window.   Click on the "Work" tab and click on "claim" to claim the task.

7. Fill in the form provided for the task, it allows review of all the booking data submitted, generated by services and 
   calculated by the rules. You can request a review to send it back for a pricing review or check the completed box to 
   finish the task and process (isBookingConfirmed). All tasks have automated reassignment, meaning if not completed within 1 minute
   they will be put back into the group.

8. Enter credit card details (beginning with 1234...) for compensation to be triggered., Expiry details of the 
   card (e.g. 12/12) and your full name.

9. Check the logs and you will see that the process has been compensated.

10. To trigger different path for successful booking of Flights, just change the 'Credit Card details' to use any 
    card number that does not begin with 1234....

11. For details on demoing the compensation aspects of the Travel Agency demo project, 
    see [docs/compensation-howto/README-COMPENSATION.md](docs/compensation-howto/README-COMPENSATION.md)


Supporting Articles
-------------------
- [7 Steps to Your First Process with JBoss BPM Suite Starter Kit](http://www.schabell.org/2015/08/7-steps-first-process-jboss-bpmsuite-starter-kit.html)

- [A Micro Services Migration Story with JBoss BPM Travel Agency](http://www.schabell.org/2015/05/micro-services-migration-story-with-jboss-bpm-travel-agency.html)

- [Online Free PEX Webinar - A Guide to Modern BPM Tools](http://www.schabell.org/2015/04/online-free-pex-webinar-guide-to-modern-bpm-tools.html)

- [Quickest Way into the Clouds with JBoss BPM Travel Agency](http://www.schabell.org/2015/02/into-clouds-with-jboss-bpm-travel-agency.html)

- [Webinar - How to Excite the Travel Industry with a BPM Story](http://www.schabell.org/2015/02/webinar-how-to-excite-travel-industry.html)

- [Slides from webinar - How to excite the travel industry with a BPM story](http://www.schabell.org/2015/02/slides-webinar-jboss-bpm-travel-agency.html)

- [How to fly with the JBoss BPM Travel Agency (video 4 of 4)](http://www.schabell.org/2015/02/how-to-fly-with-jboss-bpm-travel-agency-part4.html)

- [How to fly with the JBoss BPM Travel Agency (video 3 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part3.html)

- [How to fly with the JBoss BPM Travel Agency (video 2 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part2.html)

- [How to fly with the JBoss BPM Travel Agency (video 1 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency.html)

- [Jump Start Your Rules, Events, Planning and BPM Today](http://www.schabell.org/2014/12/jump-start-rules-events-planning-bpm-today.html)

- [3 Reasons You Need The New JBoss Travel Agency](http://www.schabell.org/2014/12/3-reasons-you-need-new-jboss-travel-agency.html)

- [How To Excite the Travel Industry With a BPM Story](http://www.schabell.org/2014/10/how-to-excite-travel-agencies-with-bpm-story.html)


Released versions
-----------------
See the tagged releases for the following versions of the product:

- v1.5 - JBoss BPM Suite 6.2, JBoss EAP 6.4.4 and travel agency installed.

- v1.4 - JBoss BPM Suite 6.1 with travel agency installed.

- v1.3 - JBoss BPM Travel Agency with automated task reassignment.

- v1.2 - JBoss BPM Travel Agency with one-click install on bpmPaaS.

- v1.1 - JBoss BPM Suite 6.0.3 with optional docker installation.

- v1.0 - JBoss BPM Suite 6.0.3 and updated travel agency demo with compensation features.

- v0.2 - moved to JBoss Demo Central, updated windows init.bat support.

- v0.1 - JBoss BPM Suite 6.0.3 and travel agency demo installed.


[![Video part 1](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/video-part-1.png?raw=true)](http://vimeo.com/ericschabell/bpms-travel-agency-part-1)

[![Video part 2](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/video-part-2.png?raw=true)](http://vimeo.com/ericschabell/bpms-travel-agency-part-2)

[![Video part 3](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/video-part-3.png?raw=true)](http://vimeo.com/ericschabell/bpms-travel-agency-part-3)

[![Video part 3](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/video-part-4.png?raw=true)](http://vimeo.com/ericschabell/bpms-travel-agency-part-4)

![Cloud Sign](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/cloud-sign.jpg?raw=true)

![Digital Sign](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/announce-sign.jpg?raw=true)

![Agency Process](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/agency-process.png?raw=true)

![Calculate Process](https://github.com/jbossdemocentral/bpms-travel-agency-demo/blob/master/docs/demo-images/calculate-process.png?raw=true)

![Compensation](https://raw.githubusercontent.com/jbossdemocentral/bpms-travel-agency-demo/master/docs/demo-images/compensation-process.png?raw=true)

![Special Trips UI Form](https://raw.githubusercontent.com/jbossdemocentral/bpms-travel-agency-demo/master/docs/demo-images/SpecialTripsUIform.png)

![Started Process](https://raw.githubusercontent.com/jbossdemocentral/bpms-travel-agency-demo/master/docs/demo-images/started-process.png)

