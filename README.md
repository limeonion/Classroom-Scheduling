# <p align="center"></br>Hadoop for Class Scheduling</br></p>

------

![Img_4](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/11.png)

Goal
------
Learn Parallel Processing of Big Data using Hadoop MapReduce and Build Analysis and Visualization Dashboard(s) using Tableau</br>

**Note: The data processed in this project consists of files having more than 700,000 rows**

Context & Problem Statement
-------------------------------------------
Class room scheduling for courses is complex problem. It is all the more difficult in a department where the enrollments are increasing and number of courses and class sizes are increasing. You are given the data for courses and class rooms from 1931 to 2017. Data analysis you perform will be driven by problems you want to solve and questions you want answered. Users for this “data product” are (i) course schedulers (ii) teachers teaching a course (iii) university planners and (iv) university development department for fund raising related activities.

Understand the domain and design a list of relevant questions. You are required to design and implement MR algorithms to extract useful intelligence to answer the questions. This intelligence will be offered as answers to questions through a web interface (dashboard). The answers to these questions could be through visualization, textual output or numerical information. The dashboard will feature ability for the user to interact by choosing from a set of questions and also by configuring the parameters for the questions and the visualizations. Sample questions to get you started are given below one for each type of user: (i) List all the class rooms of capacity greater than 200 for Mondays and Wednesdays between 5 and 6.20PM for Spring 2016 (ii) List a class room with capacity greater than 200 for May 9, 2016, 7-11pm (iii) track the trend in growth of seats per semester per building in the last 10 years in an interactive visualizations and (iv) compare enrollment increase over last 10 years to the building space increase in a visualization.

More specifically we want to analyze the data and provide a presentation of the charts (in the form of the dashboards) explaining the usage of the spaces (classrooms). How it has changed, what is trending, who is using the classrooms. Are the rooms being efficiently used?  Why was  CSE 4/587 scheduled in a 150 capacity NSC 215 when there was a classroom with modern facilities available at Knox 109 and Knox 110?

Steps for Hadoop Setup
---------------------------------
You can either run Hadoop MR jobs in HDFS which require you to run the HDFS every time or you can also do it locally by **adding Hadoop jars in Eclipse**
 
1. Follow Tutorials from the mentioned links (make sure to set the **JAVA_HOME** and **HADOOP_HOME**  path in your **bash_profile**)
	> - https://getblueshift.com/setting-up-hadoop-2-4-and-pig-0-12-on-osx-locally/
	> -  http://www.mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/
	> -  http://www.tutorialspoint.com/hadoop/hadoop_enviornment_setup.htm

2. Edit **bash_profile**<br />
	$ nano .bash_profile<br />
	```
	export JAVA_HOME = $(/usr/libexec/java_home -v 1.7)
	export HADOOP_HOME = /localpath/hadoop-2.6.4
	PATH = "$HADOOP_HOME/bin:${PATH}"
	export PATH
	```
	$ source .bash_profile
 

3. Download the Jar from the below link and copy paste it in the **Plugin Folder** of Eclipse
	https://github.com/winghc/hadoop2x-eclipse-plugin/blob/master/release/hadoop-eclipse-kepler-plugin-2.4.1.jar

4. Goto Project Build path and add Hadoop jars as shown below
![Img_1](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/1.png)

5. Configure program parameters in run configuration
![Img_2](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/2.png)

	*Alternatively if you are running Hadoop on HDFS than you may want to give the HDFS path for the Arguments as shown below
> hdfs://localhost:9000/user/amitdatt/input/ hdfs://localhost:9000/user/amitdatt/output/

6.  Define the location of a Hadoop infrastructure for running MapReduce applications
![Img_3](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/3.png)

Questions that we solved
------------------------------------
**Question 1: UB Course Demand**</br>

> Every semester UB offers great courses to its students and provide the best world class faculty to teach those courses. However, we have observed that some of the courses are always in high demand either due to increasing technology demand of that field or due to extra ordinary teaching faculty. 

> UB student affairs want to globalize some of its courses which are highly demanding among students but we are not able to shortlist the courses. Can you utilize the “UB Course Scheduling data” to gather an insight on which courses have always been the first choice for the students?

**Solution:**
> **Source code:**</br>
> https://github.com/limeonion/Classroom-Scheduling/blob/master/Problem_2/Question_1_UB_Course_Demand/UBCourseDemand.java

![Img_6](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/6.png)

---- 
**Question 2: Most Popular Department Every Year**</br>
> We see that UB consists of many departments. However, which among these is the most popular? How do we decide which one is the most popular? Answering this question can give us an idea as to which department needs more classrooms and more time slots. 

> Since the popularity might change every year we also need to observe trends over the past few years. Therefore, our question would be, find the most popular department by number of enrollments every year.

**Solution:**
> **Source code:**</br>
> https://github.com/limeonion/Classroom-Scheduling/blob/master/Problem_2/Question_2_Popular_Department/PopularDepartment.java

![Img_7](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/7.png)

---- 
**Question 3: Find wasted space in every building over the years**</br>
> UB is broken into buildings and each building has a lab or a lecture hall. A lot of this space is usually wasted. 

> Find out which buildings have been historically wasting space and which buildings have been efficient. So that we can allot more classes in the inefficient buildings

**Solution:**
> **Source code:**</br>
> https://github.com/limeonion/Classroom-Scheduling/blob/master/Problem_2/Question_3_Building_Utilization/BuildingUtilization.java

![Img_8](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/8.png)

---- 
**Question 4: Lecture Time Analysis**</br>
> Class scheduling is very complex problem and its all the more difficult in a department where the enrollments are increasing. We have observed that some of the classes are small as compared to the number of students enrolled and vice versa. This not only make it difficult for the professor to deliver his/her lecture efficiently but also creates a bad image of us among international students.

> Being a World Class University we do not want our students to fight for a seat during the class. Can you utilize the “UB Course Scheduling data” to provide an insight on what time of the day have remained most occupied with lectures during the years and what is the most suitable time to reschedule these courses, so that we can allocate them class of proper size?

**Solution:**
> **Source code:**</br>
> https://github.com/limeonion/Classroom-Scheduling/blob/master/Problem_2/Question_4_LectureTime_Analysis/LectureTimeAnalysis.java


![Img_9](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/9.png)

---- 
**Question 5: Find the most popular exam slots in every building**</br>
> Exam season is stressful for everyone. For the students and especially for the staff. They have to ensure classes are allotted and everyone finds their place. From the 6 years’ exam data that we have we aim to find the most popular exam slots in every building. By this data we can find out what time slot most exams are held. We can further analyze this data and make decisions to move some of the exams at this time slot to another. We can also make decisions to move them to other halls to.

**Solution:**
> **Source code:**</br>
> https://github.com/limeonion/Classroom-Scheduling/blob/master/Problem_2/Question_5_Popular_Exam_Slots/PopularExamSlots.java

![Img_10](https://github.com/limeonion/Classroom-Scheduling/blob/master/Resources/10.png)


