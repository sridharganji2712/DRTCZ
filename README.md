DRTCZ: A Spatially Isolated Real-Time Scheduling Framework for Efficient Fog Task Offloading

DRTCZ is an extended scheduling and task offloading mechanism for iFogSim designed to enhance real-time performance and scalability in fog computing environments. It introduces a spatially partitioned architecture in which fog devices are divided into two execution zones:

Real-Time Computing (RTC) Zone – A dedicated high-performance node subset for latency-critical tasks.
Non-Real-Time Computing (NRTC) Zone – A separate region handling background and delay-tolerant tasks.
This separation eliminates queuing interference, minimizes deadline misses, and allows both workloads to progress independently. The RTC zone can also expand or shrink dynamically depending on the number of real-time tasks present.

Key Highlights
Spatial isolation between RT and NRT workloads
Dual-buffer queueing with independent scheduling
Adaptive RTC zone resizing based on real-time load
Reduced latency and improved throughput compared to RR/MLFQ
Robust under node failures, heavy NRT backlog, and bandwidth constraints
Fully compatible with iFogSim and CloudSim architecture

Repository Structure
The repository extends the default iFogSim structure by adding a new package:
org.fog.drtcz/
    DRTCZController.java
    DRTCZPlacement.java
    DRTCZExample.java
    DRTCZUtils.java

These classes introduce the zone-based scheduling logic, device classification, and experimental setup for testing the DRTCZ methodology.

Environment Setup
This section explains how to prepare a complete working environment for running DRTCZ.

1. Install Java (JDK)
iFogSim requires Java 8.
Steps:
Download Java SE Development Kit 8 (JDK 1.8):
https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html
Install the JDK and ensure java -version returns version 1.8.
If multiple Java versions are installed, configure JAVA_HOME:

For Windows:

Control Panel → System → Advanced System Settings → Environment Variables
JAVA_HOME = C:\Program Files\Java\jdk1.8.0_xx
Add to PATH: %JAVA_HOME%\bin

2. Install Eclipse IDE

Download Eclipse IDE for Java Developers:
https://www.eclipse.org/downloads/

Install and launch it.
Choose a workspace directory, such as:
C:\Users\<username>\eclipse-workspace\

3. Import iFogSim into Eclipse

Open Eclipse
Select File → Import
Choose Existing Projects into Workspace
Browse to the iFogSim folder
Ensure the following projects appear:
iFogSim
cloudsim
Click Finish.

After import, ensure there are no compilation errors.
If errors exist, check whether the JRE System Library is set to Java 8:

Right Click Project → Build Path → Configure Build Path → Libraries
Remove JRE 11/17 if present.
Add JRE System Library → Installed JREs → Add Java 8.

4. Add Required Libraries Manually (if needed)
iFogSim uses the following jars (usually bundled inside the lib/ folder):
gson.jar
commons-math3.jar
jfreechart.jar
jcommon.jar

If missing, download them and place inside iFogSim/lib/.
Add them to build path:
Right click iFogSim → Build Path → Add External Archives
How to Integrate DRTCZ into iFogSim
Copy the folder org/fog/drtcz/ into:

iFogSim/src/org/fog/


Ensure the following classes are available:
DRTCZController (modified Controller)
DRTCZPlacement (zone-based module placement)
DRTCZExample (example topology runner)
Utility classes (task classification, node scoring, queues)

Replace or adjust the default Controller and ModulePlacement as instructed in comments.
Build the project.


Running the DRTCZ Simulation

Open DRTCZExample.java in the org.fog.drtcz package.
Set the simulation parameters:
Number of fog nodes
RTC/NRTC ratio
Task generation settings
Network bandwidth
Run the file as:
Right Click → Run As → Java Application


The simulation outputs will appear in the Eclipse Console, including:

Task completion timelines
Latency metrics
Energy consumption
Throughput
Deadline miss rates

All results are generated during the simulation run .
