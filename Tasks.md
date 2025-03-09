# WS UK Industry 4.0: Back to Basics task

Tasks described below have been used during Industry 4.0's B2B training and have been completed by competitors.
Please feel free to use a joined simulated environment of CODESYS + FactoryIO to complete this task.
For any further information, feel free to contact me through [my LinkedIn profile](www.linkedin.com/in/mregulski).

## 💻 Task I: PLC Programming

Program PLC logic for Sorting station to match following requirements:

| No.  | Description |
|------|------------|
| 1.0  | Once started, station shall remain inactive, until a Start button on a man control panel is pressed. |
| 1.1  | If at any moment an Emergency Stop button is pressed, system shall come to a stop. |
| 1.2  | Upon releasing an Emergency Stop, station shall indicate a need for "reset", before the process can be started again. "Reset" means removal of any outstanding parts on exit conveyor and vision sensor locator and return to initial position of all actuators. It should be initiated by pressing a Reset button. |
| 1.3  | A short documentation shall be supplied, where part coding detected by Vision sensor is explained, together with chosen location for such part (remover 1-3). |
| 1.4  | Program shall perform according to the documentation provided. |
| 1.5  | Counters for each remover shall be adding up each removed item. |
| 1.6  | Upon station reset, all counters shall be set to 0. |
| 1.7  | Upon pressing Stop button, a system shall come to a stop. Process can be resumed by pressing a Start button, indicated to a user by flashing a Start light with 1Hz frequency. |
| 1.8  | To minimize energy costs, sorter belts shall not be set to run continuously. Belts should only be initiated when sorter arm is being used to dispatch a part. |
| 1.9  | Both factory IO project and Codesys project shall be saved under Desktop in a folder "B2B_Day1". |

Use PLC simulator of your choice to complete this task. FactoryIO offers a selection of connectors to various programming environments.

> Name of variables, how they are assigned, and program structure are completely up to you.

## 💻 Task II: Node-RED Dashboard

Extend PLC logic for Sorting station and create an online dashboard to match following requirements:​

| No.  | Description |
|------|------------|
| 2.0  | Online dashboard shall include a group called "Conveyor status" with live state of all conveyor belts (5 in total). |
| 2.1  | Display last reading of vision sensor on a dashboard. |
| 2.2  | Dashboard shall include a group called "Dispatch" with live counter values for each of the remover stations. |
| 2.3  | Send a notification every time system is stopped using emergency stop button. |
| 2.4  | Editor: demonstrate a use of flow or global variables within your solution. |
| 2.5  | Include a static element within the dashboard that includes notes from task 1 – explaining which part number is for which part. |
| 2.6  | Export Node-RED flow, and save it as "B2B_Dashboard_Day2". |
| 2.7  | Factory IO project, Codesys project, and Node-RED flow shall be saved under Desktop in a folder "B2B_Day2". |

> Layout of your dashboard and any additional visual effects can be added, but will not be marked.

## 💻 Task III: Databases

Extend Node-RED dashboard for Sorting station with use of databases:

| No.  | Description |
|------|------------|
| 3.0 | Create a new database called "sorting_station" and add user "nodered" with sufficient rights to ```INSERT```, ```UPDATE```, ```SELECT``` and ```DELETE```. |
| 3.1 | Create two tables within "sorting_station" db: "counters" and "vision_camera". |
| 3.2 | Table "counters" should consist of two columns: "ID" and "value". Assign column "ID" and ```TINYINT``` and primary key, and "value" as ```SMALLINT```. |
| 3.3 | Limit number of rows in "counters" to 3. |
| 3.4 | Table "vision_camera" should consist of three columns: "ID", "timestamp" and "value". Assign column "ID" as ```SMALLINT``` and primary key, "value" as ```TINYINT``` and "timestamp" as ```TIME```. |
| 3.5 | Establish connection between Node-RED and newly created db, using created credentials. |
| 3.6 | Create a Node-RED flow to cyclically update "counters" records for all three counters. Cycle time should be equal to 10 sec. |
| 3.7 | Create a Node-RED flow to cyclically update "vision_camera" records for every scanned item. Include timestamp when scan has been performed. |
| 3.8 | Using "ui-table" node, display a live counter of parts scanned by vision camera. Columns should include: part identifier used in FactoryIO, description, and total value. |
| 3.9 | Resetting simulation in FactoryIO (see previous task) should not clear counters in database. |
| 3.10 | Include a single button for each db table in your Node-RED dashboard to clear records. |

> Use a database of your choice to complete this task. During training session, a MariaDB server and HeidiSQL have been used.
