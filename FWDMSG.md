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
![ACE Toolkit App Forward MQ Message Step 9](images/2022-07-11_09-12-26.png)
![ACE Toolkit App Forward MQ Message Step 10](images/2022-07-11_09-17-51.png)
![ACE Toolkit App Forward MQ Message Step 11](images/2022-07-11_09-23-03.png)
![ACE Toolkit App Forward MQ Message Step 12](images/2022-07-11_09-25-45.png)
![ACE Toolkit App Forward MQ Message Step 13](images/2022-07-11_09-29-09.png)
![ACE Toolkit App Forward MQ Message Step 14](images/2022-07-11_09-31-43.png)
![ACE Toolkit App Forward MQ Message Step 15](images/2022-07-11_09-34-15.png)
![ACE Toolkit App Forward MQ Message Step 16](images/2022-07-11_09-36-53.png)
![ACE Toolkit App Forward MQ Message Step 17](images/2022-07-11_09-37-46.png)
![ACE Toolkit App Forward MQ Message Step 18](images/2022-07-11_09-39-14.png)
![ACE Toolkit App Forward MQ Message Step 19](images/2022-07-11_09-40-47.png)
![ACE Toolkit App Forward MQ Message Step 20](images/2022-07-11_09-41-22.png)
![ACE Toolkit App Forward MQ Message Step 21](images/2022-07-11_09-41-56.png)
![ACE Toolkit App Forward MQ Message Step 22](images/2022-07-11_09-42-24.png)
![ACE Toolkit App Forward MQ Message Step 23](images/2022-07-11_09-46-45.png)
![ACE Toolkit App Forward MQ Message Step 24](images/2022-07-11_09-48-11.png)
![ACE Toolkit App Forward MQ Message Step 25](images/2022-07-11_09-49-29.png)
![ACE Toolkit App Forward MQ Message Step 26](images/2022-07-11_09-52-30.png)
![ACE Toolkit App Forward MQ Message Step 27](images/2022-07-11_09-53-41.png)
![ACE Toolkit App Forward MQ Message Step 28](images/2022-07-11_09-54-41.png)
![ACE Toolkit App Forward MQ Message Step 29](images/2022-07-11_09-55-58.png)
![ACE Toolkit App Forward MQ Message Step 30](images/2022-07-11_09-57-00.png)
![ACE Toolkit App Forward MQ Message Step 31](images/2022-07-11_09-57-23.png)
![ACE Toolkit App Forward MQ Message Step 32](images/2022-07-11_09-58-01.png)
![ACE Toolkit App Forward MQ Message Step 33](images/2022-07-11_10-00-55.png)
![ACE Toolkit App Forward MQ Message Step 34](images/2022-07-11_10-02-44.png)
