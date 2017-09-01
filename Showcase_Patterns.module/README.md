# BusinessWorks Showcase_Patterns
These projects contain a number of Enterprise Integration Patterns as defined by Gregor Hohpe and Bobby Woolf at http://www.enterpriseintegrationpatterns.com/ 

### Project Pre-Reqs
* BusinessWorks 6.4
* MySQL configured as described below (Other databases can be used. It is left to the user to adjust the JDBC Shared Resource and ensure all the required objects are available)
* SMTP Account- The SMTP Shared Resource must be configured for an account the user has access to
* FTL Instance- Currently configured for local instance but can be changed as needed

## Integration Styles Projects
### File Transfer
#### File_Transfer.bwp
This process implements the basic File Transfer Integration Style defined in http://www.enterpriseintegrationpatterns.com/patterns/messaging/FileTransferIntegration.html. It monitors a directory for new files, copies the file to a new directory and then deletes the original file.

### Shared Database
The shared database pattern defined in http://www.enterpriseintegrationpatterns.com/patterns/messaging/SharedDataBaseIntegration.html is implemented in two parts - one for Application A and another for Application B. It uses one of the MySQL Tables to create new customers (from Application A), and Application B reads the Customer table.
Ensure the Database is setup and the shared Resource for MySQL is updated appropriately
#### Shared_Database_Application_Writer.bwp
This is the implementation of Application A
#### Shared_Database_Application_Reader.bwp
This is the implementation of Application B

### Remote Procedure Invocation
RPI/RPC as defined in http://www.enterpriseintegrationpatterns.com/patterns/messaging/EncapsulatedSynchronousIntegration.html is not really used these days with integration via API's being the much preferred route and so we have not implemented this Integration Style in this showcase.

### Messaging
The Messaging Pattern defined in http://www.enterpriseintegrationpatterns.com/patterns/messaging/Messaging.html is implemented in two parts - again one for Application A which sends messages, and Application B which receives the messages.
It utilises TIBCO FTL as the messaging layer and so please ensure that the FTL shared resource is correctly modified for your environment. We have also included a json configuration file which can be uploaded to your FTL Realm server to pre-configure FTL for this showcase. This can be found within this directory.
#### Messaging_Application_Sender.bwp
This process sends a single message via TIBCO FTL.
#### Messaging_Application_Receiver.bwp
This process receives any messages from TIBCO FTL.