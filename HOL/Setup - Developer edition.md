# Microservices architecture - developer edition setup


## Requirements

1.  Microsoft Azure subscription must be pay-as-you-go or MSDN.

    a.  Trial subscriptions will not work.

2.  A virtual machine configured with (see Before the hands-on lab):

    b.  Visual Studio 2017 Community edition, or later

    c.  Azure Development workload enabled in Visual Studio 2017 (enabled by default on the VM)

    d.  Service Fabric SDK 2.7 or later for Visual Studio 2017

    e.  Google Chrome browser (Swagger commands do not work in IE)

    f.  PowerShell 3.0 or higher (v5.1 already installed on VM)


## Before the hands-on lab

Duration: 45 minutes

Synopsis: In this exercise, you will set up your environment for use in the rest of the hands-on lab. You should follow all the steps provided in the Before the hands-on lab section to prepare your environment before attending the hands-on lab.

IMPORTANT: Most Azure resources require unique names. Throughout these steps, you will see the word "SUFFIX" as part of resource names. You should replace this with your Microsoft alias, initials, or other value to ensure the resource is uniquely named.

#### Task 1: Provision Service Fabric Cluster

In this task, you will provision the Service Fabric Cluster in Azure.

1.  In the Azure Portal, select +New, then type "Service Fabric" into the Search the Marketplace box. Select Service Fabric Cluster from the results. 

    ![In the Azure Portal, in the left pane, New is selected. In the Marketplace pane, Everything is selected. In the Everything pane, Service Fabric is typed in the search field, and under Results, Service Fabric Cluster is circled.](images/Setup-developer-edition/image5.png "Azure Portal")

2.  On the Service Fabric Cluster blade, select Create.

3.  On the Basics blade of the Create Service Fabric cluster screen, enter the following:

    a.  Cluster name: Enter contosoeventssf-SUFFIX, replacing SUFFIX with your alias, initials, or another value to make the name unique (indicated by a green check in the text box).

    b.  Operating system: Leave set to WindowsServer 2016-Datacenter

    c.  User name: Enter holuser

    d.  Password: Enter Password.1!!

    e.  Subscription: Select the subscription you are using for this lab

    f.  Resource Group: Select Create new, and enter hands-on-labs for the resource group name. You can add -SUFFIX, if needed to make resource group name unique. This is the resource group you will use for all resources you create for this hands-on lab.

    g.  Location: Select the region to use.

    h.  Select OK. 
    
    ![On the Basics blade, all fields are set to the previously defined settings.](images/Setup-developer-edition/image6.png "Basics blade")

4.  On the Cluster configuration blade, set the following:

    a.  Node type count: Select 1

    b.  Node type 1 (Primary): Select to configure required settings. On the Node type configuration blade enter:

    -  Node type name: Enter Web

    -  Durability tier: Leave Bronze selected

    -  Virtual machine size: Select a VM size of D1\_V2 Standard, and select Select on the Choose a size blade. ![On the Cluster configuration blade, under Virtual Machine Size, D1\_V2 Standard is circled.](images/Setup-developer-edition/image7.png "Cluster configuration blade")

    -  Single node cluster: Leave unchecked

    -  Initial VM scale set capacity: Leave set to 5

    -  Custom endpoints: Enter 8082. This will allow the Web API to be accessible through the cluster.

    -  Enable reverse proxy: Leave unchecked

    -  Configure advanced settings: Leave unchecked

    -  Select OK on the Node type configuration blade.

    c.  Select OK on the Cluster configuration blade. 
    
    ![The Create Service Fabric cluster blade, Cluster configuration blade, and Node type configuration blade all display with the previously defined settings.](images/Setup-developer-edition/image8.png "Three blades")

5.  On the Security blade, you can provide security settings for your cluster. This configuration is completed up front, cannot be changed later. Set the following:

    a.  Configuration Type: select "Basic"

    b.  Key vault: Select to configure required settings. On the Key vault configuration blade click "Create a new vault".

    c.  On the "Create key vault" configuration blade enter:

    -  Name: hands-on-lab-SUFFIX

    -  Resource Group: hands-on-lab2-SUFFIX

    -  Location: Use the same location as the first resource group you created.

    ![Create a new vault in selected in the Key vault blade, and the values specified above are entered into the Create key vault blade.](images/Setup-developer-edition/image9.png "Key vault and Create key vault blades")

    d.  Click "Create" on the Create key vault configuration blade. Wait for the key vault deployment to complete.

    e.  When the key vault deployment completes you will return to the Security configuration blade. You will see a warning that the key vault is not enabled for deployment. Follow these steps to resolve the warning:

    -  Click "Edit access policies for hands-on-lab-SUFFIX"

    -  n the Access policies configuration blade, click the link "Click to show advanced access policies"

    -  Check the "Enable access to Azure Virtual Machines for deployment" checkbox.

    -  Click "Save". When the key vault update completes, close the Access policies blade.

    ![Basic Configuration Type is selected on the Security blade, and Edit access policies for hands-on-lab-SUFFIX is selected. Enable access to Azure Virutal Machines for deployment is checked in the Access policies blade on the right.](images/Setup-developer-edition/image10.png "Security and Access policies blades")

    f.  Enter "hands-on-lab-sol" as the certificate name. Then click Ok on the Security configuration blade.

    ![Basic Configuration Type is selected on the Security blade, and Certificate name is set to hands-on-lab-SUFFIX. ](images/Setup-developer-edition/image11.png "Security blade")

6.  On the Summary blade, review the summary, and select Create to begin provisioning the new cluster. 

    ![The Summary blade displays with the message that Validation has passed.](images/Setup-developer-edition/image12.png "Summary blade")

7.  It can take up to 30 minutes or more to provision your Service Fabric Cluster. You can move on to the next task while you wait.

> **Note**: If you experience errors related to lack of available cores, you may have to delete some other compute resources, or request additional cores be added to your subscription, and then try this again.

#### Task 2: Provision a lab virtual machine (VM)

In this task, you will provision a virtual machine (VM) in Azure. The VM image used will have Visual Studio Community 2017 installed.

1.  Launch a web browser, and navigate to the [Azure Portal](https://portal.azure.com/).

2.  Select +New, then type "Visual Studio" into the search bar. Select Visual Studio Community 2017 (latest release) on Windows Server 2016 (x64) from the results. 

    ![In the left pane of the Azure portal, New is circled. In the Marketplace blade, Everything is selected. In the Everything blade, the search field contains Visual Studio. Under Results, Visual Studio Community 2017 on Windows Server 2016 (x64) is circled.](images/Setup-developer-edition/image13.png "Azure portal")

3.  On the blade that comes up, ensure the deployment model is set to Resource Manager and select Create.

    ![Resource Manager displays in the the Select a deployment model field.](images/Setup-developer-edition/image14.png "Select a deployment model field")

4.  Set the following configuration on the Basics tab.

    a.  Name: Enter LabVM

    b.  VM disk type: Select SSD

    c.  User name: Enter holuser

    d.  Password: Enter Password.1!!

    e.  Subscription: Select the subscription group you are using for this lab

    f.  Resource group: Select Use existing, and select the hands-on-labs resource group created previously.

    g.  Location: Select the region you are using for resources in this lab.

    h.  Select OK to move to the next step. 
    
    ![The Basics blade displays with the fields set to the previously stated settings.](images/Setup-developer-edition/image15.png "Basics blade")

5.  On the Choose a size blade, ensure the Supported disk type is set to SSD, and select View all. This machine won't be doing much heavy lifting, so selecting D2S\_V3 Standard is a good baseline option. 

    ![On the Choose a size blade, the Supported disk type, SSD, is circled. The D2S\_V3 Standard option is circled, as is the View all button.](images/Setup-developer-edition/image16.png "Choose a size blade")

6.  Select Select to move on to the Settings blade.

7.  Accept all the default values on the Settings blade, and select OK.

8.  Select Create on the Create blade to provision the virtual machine. 

    ![The Create blade displays with the Standard D2s v3 offer details.](images/Setup-developer-edition/image17.png "Create blade")

9.  It may take 10+ minutes for the virtual machine to complete provisioning.

#### Task 3: Connect to your lab VM

In this step, you will open an RDP connection to your Lab VM, and disable Internet Explorer Enhanced Security Configuration.

1.  Connect to the Lab VM. (If you are already connected to your Lab VM, skip to Step 9.)

2.  From the left side menu in the Azure portal, select Resource groups, then enter your resource group name into the filter box, and select it from the list. 

    ![In the Azure Portal, Resource groups pane, hands-on is typed in the search field, and under Name, hands-on-labs is circled.](images/Setup-developer-edition/image18.png "Azure Portal, Resource groups pane")

3.  Next, select your lab virtual machine, LabVM, from the list. 

    ![In the Name list, the LabVM Virtual Machine is circled.](images/Setup-developer-edition/image19.png "Name list")

4.  On your Lab VM blade, select Connect from the top menu. 

    ![The Connect button is circled on the lab VM blade top menu.](images/Setup-developer-edition/image20.png "Lab VM blade top menu")

5.  Download and open the RDP file.

6.  Select Connect on the Remote Desktop Connection dialog. 

    ![In the Remote Desktop Connection Dialog Box, the Connect button is circled.](images/Setup-developer-edition/image21.png "Remote Desktop Connection Dialog Box")

7.  Enter the following credentials (or the non-default credentials if you changed them):

    a.  User name: holuser

    b.  Password: Password.1!!

    ![The Windows Security Credentials page displays](images/Setup-developer-edition/image22.png "Windows Security Credentials page")

8.  Select Yes to connect, if prompted that the identity of the remote computer cannot be verified. 

    ![In the Remote Desktop Connection dialog box, a warning states that the identity of the remote computer cannot be verified, and asks if you want to continue anyway. At the bottom, the Yes button is circled.](images/Setup-developer-edition/image23.png "Remote Desktop Connection dialog box")

9.  Once logged in, launch the Server Manager. This should start automatically, but you can access it via the Start menu if it does not start. 

    ![The Server Manager tile is circled in the Start Menu.](images/Setup-developer-edition/image24.png "Start Menu")

10. Select Local Server, the select On next to IE Enhanced Security Configuration. 

    ![In Server manager, in the left pane, Local Server is selected. In the right, Properties pane, IE Enhanced Security Configuration is circled, and a callout arrow points to On.](images/Setup-developer-edition/image25.png "Server manager")

11. In the Internet Explorer Enhanced Security Configuration dialog, select Off under Administrators, then select OK. 

    ![In the the Internet Explorer Enhanced Security Configuration dialog box, under Administrators, the Off button is selected and circled. ](images/Setup-developer-edition/image26.png "Internet Explorer Enhanced Security Configuration dialog box")

12. Close the Server Manager.

#### Task 4: Install Chrome on LabVM

In this task, you will install the Google Chrome browser on your Lab VM.

1.  On your Lab VM, open a web browser, and navigate to <https://www.google.com/chrome/browser/desktop/index.html>, and select Download Chrome. 
    
    ![Screenshot of the Download Chrome button.](images/Setup-developer-edition/image27.png "Download Chrome button")

2.  Select Accept and Install on the terms of service screen. 

    ![The Download Chrome for Windows window displays.](images/Setup-developer-edition/image28.png "Download Chrome for Windows ")

3.  Select Run on the Application Run -- Security Warning dialog. 

    ![The Run button is circled in the Application Run -- Security Warning dialog box.](images/Setup-developer-edition/image29.png "Application Run ??? Security Warning dialog box")

4.  Select Run again, on the Open File -- Security Warning dialog. 

    ![In the Open File -- Security Warning dialog box, a message asks if you want to run the file. At the bottom, the Run button is circled.](images/Setup-developer-edition/image30.png "Open File ??? Security Warning dialog box")

5.  Once the Chrome installation completes, a Chrome browser window should open. For ease, you can use the instructions in that window to make Chrome your default browser.

#### Task 5: Install Service Fabric SDK for Visual Studio

In this task, you will install the latest Service Fabric SDK for Visual Studio 2017 on your Lab VM.

1.  On your Lab VM, open a browser, and navigate to <https://docs.microsoft.com/azure/service-fabric/service-fabric-get-started>.

2.  Scroll down on the page to the Install the SDK and tools section, and select Install the Microsoft Azure Service Fabric SDK under the To use Visual Studio 2017 heading. 

    ![In the Install the SDK and tools section, the link to Install the Microsoft Azure Service Fabric SDK is circled.](images/Setup-developer-edition/image31.png "Install the SDK and tools section")

3.  Run the downloaded executable, and select Install in the Web Platform Installer screen. 

    ![The Web Platform Installer window displays the information for Microsoft Azure Service Fabric SDK - 2.8.232.](images/Setup-developer-edition/image32.png "Web Platform Installer window")

4.  On the Prerequisites screen, select I Accept. ![The Web Platform Installer Prerequisites window lists the file name and file size to be downloaded. At the bottom, the I Accept button to download additional software and review the license is circled.](images/Setup-developer-edition/image33.png "Web Platform Installer Prerequisites window")

5.  Select Finish when the install completes. 

    ![The Web Platform Installer Finish window shows that the installation was successful, and lists the products that were installed.](images/Setup-developer-edition/image34.png "Web Platform Installer Finish window")

6.  Select Exit on the Web Platform installer to close it.

7.  Restart the VM to complete the installation, and start the local Service Fabric cluster service.

#### Task 6: Validate Service Fabric ports

Occasionally, when you create a new Service Fabric Cluster using the portal, the ports that you requested are not created. This will become evident when you try to deploy and run the Web App, because the required ports will not be accessible through the cluster.

In this task, you will validate that the ports are open and if not, fix the issue.

1.  In the Azure portal, navigate to the Resource Group you created previously, and where you created the cluster. If your Service Fabric cluster is still deploying, do not proceed to the next step until the deployment is completed.

2.  Select the load balancer from the list of resources in the resource group. 

    ![In the Azure Portal Resource Group pane, in the list of resources, the LB-contosoeventssf-kb-Web load balancer is circled.](images/Setup-developer-edition/image35.png "Resource group list")

3.  Under the Settings category in the left-hand menu, select Health Probes.

    ![In the Settings section, Health probes is circled.](images/Setup-developer-edition/image36.png "Settings section")

4.  Verify if a probe exists for port 8082, and that it is "Used By" a load balancing rule. If both of these are true, you can skip the remainder of this task. Otherwise, proceed to the next step to create the probe and load-balancing rule.

    ![In the list of health probes, three health probes display. For AppPortProbe1, its Port (8082), and Used by value (AppPortLBRule1) are circled.](images/Setup-developer-edition/image37.png "Health probes list")

5.  Select +Add on the Health Probes blade.

    ![Screenshot of an Add button.](images/Setup-developer-edition/image38.png "Add button")

6.  On the Add health probe blade, enter the following:

    a.  Name: Enter WebApiPortProbe

    b.  Protocol: Select TCP

    c.  Port: Enter 8082

    d.  Interval: Leave the default value

    e.  Unhealthy threshold: Leave the default value

    f.  Select OK to create the probe. 
    
    ![Fields on the Add health probe blade are set to the previously listed settings.](images/Setup-developer-edition/image39.png "Add health probe blade")

7.  Once the Health probe is added (this can take a few minutes to update), you will create a rule associated with this probe. Under the Settings block in the left-hand menu, select Load balancing rules. 

    ![In the Settings section, Load balancing rules are circled.](images/Setup-developer-edition/image40.png "Settings section")

8.  Select +Add on the Load balancing rules blade.

    ![Screenshot of an Add button.](images/Setup-developer-edition/image38.png "Add button")

9.  On the Add Load balancing rules blade, enter the following:

    g.  Name: Enter LBWebApiPortRule

    h.  IP Version: Leave IPv4 selected

    i.  Frontend IP address: Leave the default value selected

    j.  Protocol: Leave as TCP

    k.  Port: Set to 8082

    l.  Backend port: Set to 8082

    m.  Backend pool: Leave the default value selected

    n.  Health Probe: Select the WebApiPortProbe you created previously

    o.  Leave the default values for the remaining fields, and Select OK. 
    
    ![Fields on the Add load balancing rule blade are set to the previously defined settings.](images/Setup-developer-edition/image41.png "Add load balancing rule blade")

10. If you get an error notification such as "Failure to create probe", ignore this, but just go check that the probe indeed exists. It should. You now have a cluster ready to deploy to, and expose 8082 as the Web API endpoint / port.

