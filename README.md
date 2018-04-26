# HelloDBP
A simple application for Software AG's Digital Business Platform (DBP). This project includes the design time source files and projects, plus a build file to install.

## Prerequisites
1. A machine with the following products installed:
    - Integration Server with CloudStreams, JDBC Adapter, Terracotta DB Adapter, Dynamic Business Orchestrator, Task Engine ...
    - Designer with plugins...
    - Universal Messaging
    - Apama
    - MwS
    - MashZone NextGen
    - API Gateway
    - API Portal
    - Event Data Store
  
## Quick Start
1. Start Command Central and Platform Manager (sometimes two of them) via Windows Services or startup.bat/sh
1. Go to [Command Central UI](https://localhost:8091/cce/web/#environment:ALL/t/0) and start servers in this order:
    1. Terracotta DB, Universal Messaging
    1. Integration Server, MwS, MashZone NextGen
    1. API Gateway (should auto-launch Event Data Store)
    1. API Portal
1. Install Cloudstreams Connector for IS
    1. Go to [CloudStreams Cumulocity Download Page](http://techcommunity.softwareag.com/ecosystem/communities/public/webmethods/products/cloudstreams/downloads/Cumulocity/index.html)
    1. Click Download and Save file to disk
    1. Move the downloaded WmCumulocityProvider.zip file to Integration Server replicate/inbound folder (C:\SoftwareAG\IntegrationServer\instances\default\replicate\inbound)
    1. Open [IS Administrator](http://localhost:5555)
    1. Go to Packages > Management > Install Inbound Packages and Install WmCumulocityProvider.
    1. Restart IS to reload CloudStreams with Cumulocity provider.
1. Install HelloDBP IS package
    1. Download the lastest HelloDBP package from [IS](IS) folder.
    1. Go to Packages > Management > Install Inbound Packages and Install HelloDBP.zip.
    1. Open Designer Service Development perspective and use File > Sync Document Types > All Out-of-Sync... to sync the two DES types to the common repository.
1. Provide URL and Credentials for Cumulocity tenant
    1. Go to [IS CloudStreams](http://localhost:5555/WmCloudStreams/) page
    1. Click on Cumulocity provider, disable the CumulocityConnection, Edit, and change the URL, User and Password.
    #. Re-enable the CumulocityConnection.
1. Enable the Event Persistence Connection
    1. Go to [IS JDBC Adapter](http://localhost:5555/WmRoot/adapter-index.dsp?url=%2FWmART%2FListResources.dsp%3FadapterTypeName%3DJDBCAdapter%26dspName%3D.LISTRESOURCES&adapter=JDBCAdapter&text=webMethods+Adapter+for+JDBC&help=true) page
    1. Edit the EventStoreConnection
    1. In the "Other Properties" field, ensure the proper path to the suite folder.
    1. Enable the EventStoreConnection
1. Create the Things dataset in Terracotta DB
    1. One way to do this is via the [Terracotta DB Adapter in IS](http://localhost:5555/WmRoot/adapter-index.dsp?url=%2FWmART%2FListResources.dsp%3FadapterTypeName%3Dcom.wm.adapter.wmtcdb.TCDBAdapter%26dspName%3D.LISTRESOURCES&adapter=com.wm.adapter.wmtcdb.TCDBAdapter&text=webMethods+Adapter+for+Terracotta+DB&help=true)
1. Clone this Git Repository using Designer Git perspective
    1. In Designer, click the "Open Perspective" button or menu and choose Git.
    1. Click on Clone Git Repository link.
    1. In the URI, paste the link to this repository (from the green "Clone or download" button).
    1. Click "Next" twice and then check the box "Import all existing Eclipse projects after clone finishes"
    1. Click "Finish".
    1. You must re-build the HelloApama project using Project > Clean... action in Designer.
1. Deploy the HelloDBO process
    1. Open the Dynamic Process Development perspective in Designer
    1. Open the HelloDBO - 1 process.
    1. Click on "Upload for Dynamic Process" button.
    1. When asked to deploy the "Analyze Alert" task, say Yes.
    1. Provide MwS sysadmin credentials.
    1. After a minute, navigate to [Business Console](http://localhost:8585/business.console#/), you should see the HelloDBO and Analyze Alert types now.
1. Import MashZone assets
    1. Go to folder MashZoneNG > prestocli > bin
    1. padmin importAlias -u <User> -w <Password> -f "<local git path>\HelloDBP\MashZone\Aliases.zip"
    1. padmin importDashboard -u <User> -w <Password> -f "<local git path>\HelloDBP\MashZone\Dashboard.zip"
    


