Software-Defined Networking

Lab 4

Advanced Mininet, Open vSwitch, and SDN Controllers

University of Colorado Boulder

Department of Computer Science

> Professor Levi Perigo, Ph.D.

# Lab Summary

Understanding Mininet and popular SDN controllers is critical to
understanding SDN. The purpose of this lab is to explore some of the
advanced features of Mininet and become familiar with some of the
popular SDN controllers in industry. Knowing how to use advanced
features in Mininet and understanding specific commands and output, will
aid in your understanding of SDN. The experience gained from using the
controllers in this lab will facilitate your understanding of SDN
controllers as you expand on the foundations from this lab in the rest
of the course.

The objectives of this lab are to be used as guidelines, and additional
exploration by the student is strongly encouraged.

# Objective 1: 

# PART A: Connect Mininet to OpenDaylight (ODL)

1.  Refer the Lab 0 document to initialize OpenDaylight (ODL).

2.  Enable the ODL web interface and all the features (use the Lab 0
    document for assistance).

3.  Login to the ODL web interface.

4.  Login to Mininet.

    a.  Start a new Mininet topology that connects to a remote
        controller (ODL), uses easy to read MAC addresses, uses OpenFlow
        v1.3, and uses a network topology that is a tree with depth of 2
        and a fanout of 3.

    b.  Explain in detail what the tree topology is including the depth
        and fanout settings. **\[5 points\]**

5.  Within the GUI of ODL, does the topology show any hosts connected to
    the switches? Why or why not? If not, how would you get the hosts in
    Mininet to be displayed in the ODL topology? **\[5 points\]**

6.  Login to the Mininet VM with a duplicate session.

    a.  Within the Mininet VM, you are going to issue Open vSwitch
        commands to view statistics and flow table entries of the
        switches.

    b.  Provide a combined screenshot for the following operations:
        **\[5 points\]**

    ```{=html}
    <!-- -->
    ```
    i.  Command to show all ports and connections for the network.

    ii. Command to show all ports for Switch 2.

    ```{=html}
    <!-- -->
    ```
    c.  Write steps or provide a screenshot of the same functionality as
        in \[b (ii)\] in the GUI of ODL. **\[5 points\]**

    d.  Issue the command that shows all the current flow table flow
        entries in switch 2.

        i.  What command did you use? **\[5 points\]**

        ii. Provide a screenshot of this in the GUI of ODL**. \[5
            points\]**

        iii. What is the flow entry with the lowest priority value?
             Explain what that entry is. **\[5 points\]**

        iv. Generate traffic from hosts connected to switch 2 and
            refresh the flow table; were additional flow entries added?
            Why or why not? **\[5 points\]**

    e.  Find HTTP Flows

        i.  On Host1 run a HTTP server.

        ii. Perform a "wget" from H5 to the web server (H1).

            1.  What command did you use? **\[5 points\]**

        iii. Within ODL GUI or OVS, select a switch in the path, and
             highlight the flow entry that shows the HTTP traffic **\[10
             points\]**

    f.  Exit and clean up Mininet.

# PART B: Flow management with Cisco OpenFlow Manager (OFM)

1.  Refer the Lab 0 document to configure and initialize OFM.

2.  Explain what the grunt command does? **\[5 points\]**

3.  On the ODL VM, start the ODL controller by installing the following
    features:

> feature:install odl-restconf-all odl-openflowplugin-all
> odl-l2switch-all webconsole

4.  On Mininet, clear any existing Mininet topologies and build a new
    topology comprising of a single switch and five hosts, easy to read
    mac addresses, ODL as remote controller, running on OpenFlow 1.3
    protocol. Paste the output of the pingall command. **\[5 points\]**.

5.  Paste the screenshot of your browser displaying Cisco OFM. It should
    display the Mininet topology. \[**5 points\]**

6.  Create a flow entry on switch1 using Cisco OFM to provide the
    following functionality:

    a.  Match the packets with source MAC address of host five and
        destination MAC address of host one. If there are any matches,
        then switch1 drops the corresponding packet.

    b.  Set the priority of the flow entry as 50 and cookie value as
        0x99.

    c.  Paste the screenshot of the flow entry that's created in Cisco
        OFM. **\[10 points\]** *(Hint: Use the Flow Management tab
        inside Cisco OFM)*

7.  Explain the significance of priority value and cookie value of a
    flow entry. **\[5 points\]**

8.  Issue pingall command in Mininet. Did all the hosts ping each other?
    If yes, why? If not, why? **\[5 points\]**

9.  From the Mininet VM, paste the screenshot of the command and
    corresponding output that shows the flow table highlighting the flow
    added by OFM. **\[10 points\]**

10. Explain the "flow logic" of how the Cisco OFM application is able to
    add OpenFlow flow table entries to the switches within Mininet.
    \[**10 points**\]

# Objective 2 - Connect Mininet to ONOS

1.  Refer the Lab 0 document to initialize ONOS.

2.  Follow the instructions from the Lab 0 document to install apps and
    activate them.

3.  Then start a Mininet topology that connects to a remote controller,
    uses easy to read MAC addresses, uses OpenFlow v1.3, and uses a
    network topology that is a torus with 3 and 3, and change the IP
    address scheme from the default to 192.168.1.0/24.

    a.  Explain in detail what the torus topology is including the
        additional "3" settings. **\[5 points\]**

    b.  Issue the "pingall" command in Mininet to bring up all the
        devices.

4.  Within the GUI of ONOS:

    a.  Provide a screenshot of the topology (from the previous Mininet
        commands, including all hosts). **\[10 points\]**

    b.  Navigate around the ONOS GUI and familiarize yourself with the
        features.

        i.  Follow the "ONOS Tutorial" link on the desktop for
            additional information.

5.  Within the Mininet VM, you are going to issue Open vSwitch commands
    to view statistics and flow table entries of the switches.

    a.  Dump all OpenFlow flow tables from Switch3.

        i.  What command did you use? How many flow tables were there?
            How do you know? What is the difference between flow tables
            and flow entries **\[20 points\]**

        ii. Provide this same information by using the ONOS GUI.

> iii\. Provide a screenshot of the flow tables and flow entries from
> Switch3 from the GUI. **\[10 points\]**

6.  View the ONOS topology.

    a.  Shutdown the link from Switch1 to Host1 (from within Mininet).

        i.  What command did you use? **\[5 points\]**

        ii. Did the ONOS GUI topology change in real-time or did you
            have to refresh? Provide two examples of how this Mininet
            command could be useful for testing. **\[10 points\]**

    b.  Bring the link back up from Switch1 to Host 1.

        i.  What command did you use? **\[2 points\]**

7.  Navigate around the ONOS GUI.

    a.  Go to the main ONOS Platform menu.

        i.  Then navigate to Applications.

        ii. Explain how you could activate additional applications and
            provide a screenshot as an example. **\[10 points\]**

    b.  Intentions:

        i.  What are intentions in ONOS? **\[5 points\]**

        ii. Create a Host to Host flow between two hosts in the
            topology.

            1.  Generate traffic between these two hosts.

            2.  Provide a screenshot of the flow as well as the green
                link indicating the bandwidth on that flow in the GUI.
                **\[15 points\]**

            3.  If you are having trouble with this based on this
                topology, you can ping from a host to another host in
                Mininet and then "show related traffic" in the GUI after
                clicking on the host you initiated the ping from. Then
                you can use the "a" shortcut to show all traffic flows
                with bandwidth.

            4.  Based on the knowledge you have thus far, provide three
                functionalities/readability you can do in the ONOS
                controller that you can't do in ODL. **\[10 points\]**

            5.  With your experience thus far, do you like the ONOS or
                ODL controller better? Why? **\[5 points\]**

# Objective 3 - Connect Mininet to Ryu

1.  Refer the Lab 0 document to initialize Ryu.

2.  Enable the Ryu web interface with a basic L2 switch (use the Lab 0
    document for assistance).

3.  Login to the Ryu web interface.

4.  Login to Mininet.

    a.  Start a new Mininet topology that connects to a remote
        controller (Ryu), uses easy to read MAC addresses, and uses a
        network topology that is a tree with a fanout of three and depth
        of three.

    b.  Issue the "pingall" command in Mininet to bring up all the
        devices.

        i.  What messages do you see on the Ryu CLI debug? Indicate why
            you see these messages. **\[5 points\]**

    c.  Within the GUI of Ryu, provide a screenshot of the topology.
        **\[10 points\]**

# Objective 4 - Connect Mininet to Floodlight

1.  Refer to the Lab 0 document to initialize Floodlight.

2.  Access the Floodlight Web UI.

3.  Open a new terminal and get into the Floodlight directory. Now start
    > Mininet, and build a tree topology with a depth of 3, a fanout of
    > 3, using OpenFlow version 1.3, and port number 6653:

    a.  What command did you use? **\[5 points\]**

    b.  Paste the screenshot of the topology created on the Floodlight
        > controller dashboard. **\[5 points\]**

4.  After the topology is created on your Floodlight Web UI, proceed to
    evaluate the 'Switch Details' on any switch you desire. Post a
    screenshot of the switch details screen. **\[10 points\]**

5.  Confirm you have issued a 'pingall' operation on Mininet for the
    topology created and evaluate the flow table entries. Post a
    screenshot of the updated flow table entries. **\[10 points\]**

6.  Initiate any topology from Mininet and create a firewall rule of
    your choice. Post the screenshot of the firewall setting activated
    on the GUI. Also post screenshots of the Floodlight console logs and
    Mininet pings to prove that the firewall setting is working. **\[10
    points\]**

# Objective 5 - Import Custom Topology in Mininet 

![](vertopal_316eed5747894a3c8508809231a41cec/media/image1.png){width="5.130208880139983in"
height="2.9926213910761157in"}

**Figure 1.** Mininet custom topology

In this objective, you are required to build a custom topology for
Mininet as shown in Figure 1 above. All links marked with solid lines
need to be set to 10Mbps.

1.  Start the controller of your choice, write down the IP of the
    controller.

2.  Build the topology in MiniEdit in your Mininet VM.

    a.  Create the topology, set device names, and link speed. Set
        controller to remote and specify the IP address and port number.

    b.  Provide a screenshot of the topology. **\[10 points\]**

3.  Select "Export Level 2 Script" in the File menu, save the file as
    .sh file.

4.  In your Mininet VM run the following command:

chmod +x \[your .sh file\]

Explain what this command does. **\[2 points\]**

5.  Run the following command to start Mininet

    a.  sudo ./\[your .sh file\]

    b.  pingall

    c.  Provide a screenshot of the command and Mininet running with
        results of the pingall **\[10 points\]**

6.  Now you loaded Mininet with a custom topology using a .sh file.
    There is another way to load a custom topology, by using the
    following command:

    a.  sudo mn \--custom topology.py \--topo=mytopo
        \--controller=remote,ip=xx.xx.xx.xx

    b.  pingall

7.  Modify the .sh file into .py file that can be loaded in the above
    command. More details can be found here
    [[http://mininet.org/walkthrough/#custom-topologies]{.underline}](http://mininet.org/walkthrough/#custom-topologies)
    and here
    [[http://mininet.org/api/classmininet_1\_1topo_1\_1Topo.html]{.underline}](http://mininet.org/api/classmininet_1_1topo_1_1Topo.html).

    a.  Provide a screenshot of the command and Mininet running with
        results of the "pingall" command. **\[10 points\]**

8.  Provide original .sh file, modified .sh file, and the .py file with
    your report to get points.

# Objective 6 - Real World

1.  Use any controller you like.

2.  Create a huge topology of a multitude of switches or hosts or both
    (be careful not to crash your PC!).

    a.  Provide a screenshot of the nightmare topology from the
        controller GUI. **\[1 points\]**

> b\. Explain why this topology could possibly be realistic of a real
> world SDN network design. **\[5 points\]**

# Objective 7 -- Report questions

1.  After completing this lab, which controller would you prefer and
    why? \[**5 points**\]

2.  How can we make a controller communicate with a traditional
    router/switch not running OpenFlow for configuration/monitoring
    purposes? \[**5 points**\]

# Total Score \_\_\_\_\_\_\_\_\_\_\_\_\_ / 320
