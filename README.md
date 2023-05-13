# Progress Report - Operations and Maintenance 
-	An overhead gantry system was installed in a distribution centre of a bakery to store products from bakery and retrieve it as per the sales orders
-	As per the request of stakeholders, I analysed machine's store/retrieve data to find out the rate of infeeding the products into the Gantry storage vs the rate of retrieving sales orders from it
-	I also analysed machine's performance to find out most common problems, uncovered some trends and analysed them even further to improve the performance

## Prerequisites:
- Volume Summary report shows how much volume in trays are stored into the machine (Infeeding) and retrieved/outfeed from machines (Outfeeding)
- Gantry system consists of two robots R101 and R102
- Downtime report shows downtime of machines independently as well as together
- The reports were targeted to audience with highly technical background (A different version was presented to stakeholders in PPT slides which can't be shared as confidentiality requirement)

### Business Task 1: Effective utilization of Machine
- Find out the utilization rate (Infeeding vs Outfeeding) of each shift
- Average downtime in hours and count of failures

**Results:** [Volume Summary](https://github.com/Vishal3698/Gantry_Perfomance_Reports_2023/blob/main/Volume%20Summary.pdf)

### Business Task 2: Performance of each robot 
- Find out the most common errors of Gantry system and drill down for each robot (R101 and R102)
- Find out any trends and see if there are any, and ways we can improve it even further

**Results:** [Downtime Report](https://github.com/Vishal3698/Gantry_Perfomance_Reports_2023/blob/main/Downtime%20Report.pdf)



## Interesting Facts:
- In order to find out which storage positions generated more erros for Business Task 2, I had to join two tables 
  - One table had error time and error description per robot (500+rows) vs the other table was from machine generated .log files with more than 3 million rows of observations (Each had timestamp and task number with task description)
  - The time when "Gripper Guide Collision" error happens, the robot was doing some task (either storage or retrieval)
  - I had to match the error timestamp with the task timestamp which could fall either a minute earlier than error generated or a minute after
  - I matched all the rows where the difference was 90 seconds
  - I had to upload the data into BigQuery and ran analysis using SQL query (took 7 seconds vs infinite time in python or excel)
 
 ### SQL Query:
 
 ![image](https://github.com/Vishal3698/Gantry_Perfomance_Reports_2023/assets/78323354/1a7b65fe-5a9f-4c9c-b960-efa2255f0282)

### Tools Used: 
- Types of Data: Structured (Excel, SQL server) & Unstructured (.log files from machines)
- Data Cleaning: Python, PowerQuery in PowerBI
- Data analysis: SQL
- Visualizations: PowerBI
