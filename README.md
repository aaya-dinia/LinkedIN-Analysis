**If you are a LinkedIn user, have you ever wondered about the segments of people in your network?**<br />
**As a user on LinkedIn I was curious about the statistics of people in my network which led me to try to anlyse my LinkedIn network using python**.<br /><br />
First we need data, you can request and download your data directly from LinkedIn :<br /><br />
 ![image](https://user-images.githubusercontent.com/113764800/193473694-cfd70b27-996f-4665-bcf5-a8c8033ac2e8.png)<br />
 ![image](https://user-images.githubusercontent.com/113764800/193472630-ba1e19d7-2e30-44bb-91d7-170b6be64e8a.png)<br /><br />
 Specifically, I imported the connections data. we will now import and check the data :<br /><br />
 ![image](https://user-images.githubusercontent.com/113764800/193472905-4c188146-f42a-42ff-8229-6fb60bf37082.png)<br /><br />
 "Connected On" indicates the date I connect to that person, I will convert that column into a date-time and visualize it with Plotly<br /><br />
 ![image](https://user-images.githubusercontent.com/113764800/193472976-be692478-c91a-4d9c-abd4-a04ebf4ead9d.png)<br /><br />
**Let's visualise our Number of Connections :**<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473239-8e50a00c-f3b0-4704-8292-9539b1b3b77c.png)<br /><br />
**Which organizations do the people in my network work at?**<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473322-7b712e9c-d6c9-4b50-a4e6-bc06ae4fdca9.png)<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473352-c7570213-3fd6-4925-ae3d-dce0dd39c0cd.png)<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473382-d9bc198a-cd6a-46aa-b58f-e8c1db93fb65.png)<br /><br />
With a treemap, it is easier to compare the proportion of one company related to the others! It looks like the majority of my network are from my School "Ecole des Sciences de l'Information [ESI]". The second-largest percentage is from Capgemini, Confideniel and Orange.<br /><br />
**How about the Top Common Positions ?**<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473427-84c6a733-58bb-4528-8352-f34357b599f8.png)<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473491-4addbb83-736a-4ae8-8ed7-ea3d04548864.png)<br /><br />
It is great that the top common positions in my network are my target groups for networking "data scientist".<br />
Some people might have titles start with "data scientist" but also have more words in their titles. Find out all the positions with words start with "Data scientist"<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473530-579a1fc4-16d0-4b81-a234-58373226da3a.png)<br /><br />
**Let's visualise the Top Common Positions but this time with Wordcloud;)**<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473564-2b151b7e-2a8f-4df3-8402-baee6cef5b0a.png)<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193473668-04498a5a-fdeb-4a56-9fc4-72e697136d5f.png)












