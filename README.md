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
1. Go to [Command Central UI](https://localhost:8091/cce/web/#environment:ALL/t/0)
    1. Command Central, Platform Manager 
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
1. Install HelloDBP IS package
    1. Download the lastest HelloDBP package from [Resources](Resources) folder.


