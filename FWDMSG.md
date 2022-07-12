# Develop an Integration using ACE Toolkit to interact with MQ and Event Streams.

This article explains the steps needed to create an Integration Flow developed with *ACE Toolkit* that uses the *MQ Nodes* to interact with a **MQ Queue Manager** and the *Kafka Nodes* to interact with an **Event Streams cluster** using the latest version of the **ACE Integration Server Certified Container (ACEcc)** as part of the *IBM Cloud Pak for Integration (CP4I)*.

## Low Code / No Code Development with ACE Toolkit.

1. Open the Toolkit in your workstation and create a new REST API project as shown below.

![ACE Toolkit App Forward MQ Message Step 1](images/2022-07-11_08-49-05.png)

2. Give a name to your project, i.e. *FWDMSG* and then click *Finish*.

![ACE Toolkit App Forward MQ Message Step 2](images/2022-07-11_08-52-31.png)

3. In the project tree click *New* and select *Message Flow* from the pop up menu.

![ACE Toolkit App Forward MQ Message Step 3](images/2022-07-11_08-54-46.png)

4. Give a new to your flow, i.e. *MQ2MQES* and then click *Finish*.

![ACE Toolkit App Forward MQ Message Step 4](images/2022-07-11_08-56-21.png)

5. Double click the *Message Flow Editor* tab to maximize it and create your flow.

![ACE Toolkit App Forward MQ Message Step 5](images/2022-07-11_09-04-33.png)

6. Drag and drop the *Nodes* from the palette to implemeng the "logic". In this case we will use the following nodes:
  * MQ Inout Node,
  * Flow Order Node,
  * Mapping Node,
  * MQ Output Node, and
  * Kafka Producer Node.

    And you will proceed to wire them. The flow should look like the one below. Once you are done double click the tab again in order to access the properties for each node. 

![ACE Toolkit App Forward MQ Message Step 6](images/2022-07-11_09-07-33.png)

7. As part of the flow we will do some message transformation from JSON to CSV. In order to take advantage of the Mapping Node we need to define the corresponding *Message Model*. To do so, click on the *New* menu in the project tree and then select *Message Model* from the pop up menu.

![ACE Toolkit App Forward MQ Message Step 7](images/2022-07-11_09-10-11.png)

8. Explore the different options. If you are using Mac you will notice *COBOL* is grayed out. For the same reason we will use CSV for this exercise, so select *CSV text* and click *Next*.

![ACE Toolkit App Forward MQ Message Step 8](images/2022-07-11_09-11-09.png)

9. In the next window select *Create DFDL schema using wizard* and then click *Next*.

![ACE Toolkit App Forward MQ Message Step 9](images/2022-07-11_09-12-26.png)

10. In the next window enter a name for the DFDL schema, i.e. *MYDATAMODEL* and then select *Next*.

![ACE Toolkit App Forward MQ Message Step 10](images/2022-07-11_09-17-51.png)

11. In the next windown enter the nunmber of field for the CSV, in this case *7* and then click *Finish*.

![ACE Toolkit App Forward MQ Message Step 11](images/2022-07-11_09-23-03.png)

12. As a result a new tab is open with the CSV schema. *Save* your progress, expand the *Record* and modify the *fields* to provide more meaningful names. You can use the following values as reference. Once you are done close the tab.

Field Name | Value
---------|-------
ID | *String*
FNAME | *String*
LNAME | *String*
EMAIL | *String*
PHONE | *String*
COMPANY | *String*
COMMENTS | *String*

![ACE Toolkit App Forward MQ Message Step 12](images/2022-07-11_09-25-45.png)

13. Now we can start configuring the nodes. Click the *MQ Input Node* to put it in focus, navigate to the *Properties* area and select the *Basic* menu to enter the name of the queue based on the configuration done in the MQ Lab, for simplicity the name is *CP4I.DEMO.API.Q*.

![ACE Toolkit App Forward MQ Message Step 13](images/2022-07-11_09-29-09.png)

14. Proceed to the *MQ Connection* section and enter the MQ configuration information. Including the information we used in the previous lab.

Property | Value
---------|-------
Connection | ***MQ client connection properties***
Destination queue manager name | ***QMGRDEMO***
Queue manager host name | ***qmgr-demo-ibm-mq***
Listener port number | ***1414***
Channel name | ***ACE.TO.MQ***

![ACE Toolkit App Forward MQ Message Step 14](images/2022-07-11_09-31-43.png)

15. As a final step we need to tell the node what format to expect, so navigate to the *Input Message Parsing* section and select *JSON*.

![ACE Toolkit App Forward MQ Message Step 15](images/2022-07-11_09-34-15.png)

16. The input node will parse the message automatically, but if we want to use the graphical mapper we need to have a json schema. To do so, we will import an existing json schema into the project. Right click the white space in the project tree and from contextual menu select *Import*.

![ACE Toolkit App Forward MQ Message Step 23](images/2022-07-11_09-46-45.png)
 
17. In the *Import* wizard type *file*, then select *File System* and click *Next*.

![ACE Toolkit App Forward MQ Message Step 16](images/2022-07-11_09-36-53.png)

18. In the next window select *Browse* and navigate to the folder where you have the json schema.

![ACE Toolkit App Forward MQ Message Step 17](images/2022-07-11_09-37-46.png)

19. The *Folder* will appear on the left side and the content on the right. Scroll down until you find the *contact.json* file then click *Browse* to define the folder where the file will be imported to.

![ACE Toolkit App Forward MQ Message Step 18](images/2022-07-11_09-39-14.png)

20. In the pop up windos select the *App* we created at the beginning of the Lab. In this case *FWDMSG*, and then click *OK*.

![ACE Toolkit App Forward MQ Message Step 19](images/2022-07-11_09-40-47.png)

21. The information is complete, you can click *Finish*.

![ACE Toolkit App Forward MQ Message Step 20](images/2022-07-11_09-41-22.png)

22. Note the project tree now has a section with the JSON schema. Double click the *Mapping Node* to create the corresponding map.

![ACE Toolkit App Forward MQ Message Step 24](images/2022-07-11_09-48-11.png)

23. We do not need to make any change in the next window, simply click *Next*.

![ACE Toolkit App Forward MQ Message Step 22](images/2022-07-11_09-42-24.png)

24. Here we will specific the data format used to process the message as well as the output message format. Expand *FWDMSG* (or whateever name you used); do the same with the *JSON Types* folder and select the *contact.json* schema we imported from the previous step. In the output section expand *FWDMSG* as well, but this time select *DFDL and XML Schemas* and then select *CONTACT* which is the CSV format we defined in previous steps. Then click *Next*.

![ACE Toolkit App Forward MQ Message Step 25](images/2022-07-11_09-49-29.png)

25. The next page confirms the output format, in this case *DFDL*. You can click *Finish*.

![ACE Toolkit App Forward MQ Message Step 26](images/2022-07-11_09-52-30.png)

26. The mapping editor will open. Expand the *JSON* and *CONTACT* records to get them in full view.

![ACE Toolkit App Forward MQ Message Step 27](images/2022-07-11_09-53-41.png)

27. Connect the *Data* level at the left with the  *record* on the right.

![ACE Toolkit App Forward MQ Message Step 28](images/2022-07-11_09-54-41.png)

28. A *Local Map* is created automatically. Click on in to open it and configure the mapping.

![ACE Toolkit App Forward MQ Message Step 29](images/2022-07-11_09-55-58.png)


![ACE Toolkit App Forward MQ Message Step 30](images/2022-07-11_09-57-00.png)
![ACE Toolkit App Forward MQ Message Step 31](images/2022-07-11_09-57-23.png)
![ACE Toolkit App Forward MQ Message Step 32](images/2022-07-11_09-58-01.png)
![ACE Toolkit App Forward MQ Message Step 33](images/2022-07-11_10-00-55.png)
![ACE Toolkit App Forward MQ Message Step 34](images/2022-07-11_10-02-44.png)
