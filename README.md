**If you are a LinkedIn user, have you ever wondered about the segments of people in your network?**<br />
**As a user on LinkedIn I was curious about the statistics of people in my network which led me to try to anlyse my LinkedIn network using python**.<br /><br />
# Data
First we need data, you can request and download your data directly from LinkedIn :<br /><br />
![image](https://user-images.githubusercontent.com/113764800/193478229-ae598457-b147-4bdf-9af1-104df7c2d36c.png)
 ![image](https://user-images.githubusercontent.com/113764800/193472630-ba1e19d7-2e30-44bb-91d7-170b6be64e8a.png)<br /><br />
 Specifically, I imported the connections data. we will now import and check the data :<br /><br />
 ```
 import pandas as pd 
import numpy as np 
import plotly.express as px
```
```
connections_df = pd.read_csv('sample_data/Connections.csv')
connections_df.info()
```
![image](https://user-images.githubusercontent.com/113764800/193474850-4a81a68f-fc92-442a-8581-5647e164280a.png)<br />

 "Connected On" indicates the date I connect to that person, I will convert that column into a date-time and visualize it with Plotly :<br />
 ```
connections_df ["Connected On"] = pd.to_datetime(connections_df ["Connected On"])
connections_df ["Connected On"]
```
![image](https://user-images.githubusercontent.com/113764800/193475317-b8ea4be2-d64b-4ad4-a618-de3f42911690.png)

## **Number of Connections**<br />
Let's visualise our Number of Connections :
 ```
connections_line = px.line(connections_df.groupby(by='Connected On').count().reset_index(), 
                           x="Connected On", 
                           y="First Name", 
                           labels={'First Name': 'Number'},
                           title='My Connections')
 connections_line.show()
```
![image](https://user-images.githubusercontent.com/113764800/193475408-1502de70-6498-4389-821d-a7e3df32d87a.png)<br /><br />
## **Which organizations do the people in my network work at?**<br />
 ```
company_groupby = connections_df.groupby(by='Company').count().reset_index().sort_values(by='First Name', ascending=False).reset_index(drop=True)
company_groupby
```
![image](https://user-images.githubusercontent.com/113764800/193475438-9f1ac33a-3424-4c4c-b645-bf9fcb77893c.png)<br /><br />
### Visualisations with a bar graph<br />
```
company_groupby = connections_df.groupby(by='Company').count().reset_index().sort_values(by='First Name', ascending=False).reset_index(drop=True)

fig2 = px.bar(company_groupby[:15],
      x='Company',
      y='First Name',
      labels={'First Name': 'Number'})

fig2
```
![image](https://user-images.githubusercontent.com/113764800/193475462-b7580274-0041-46f6-903c-fb1def9eb032.png)<br /><br />
### Visualisations with a treemap<br />
```
fig4 = px.treemap(company_groupby[:50], path=['Company', 'Position'],
          values='First Name',
          labels={'First Name': 'Number'})
fig4
```
![image](https://user-images.githubusercontent.com/113764800/193475491-6d3408fc-cdc9-4689-b6a0-d2151dd4cbe2.png)<br /><br />
With a treemap, it is easier to compare the proportion of one company related to the others! It looks like the majority of my network are from my School "Ecole des Sciences de l'Information [ESI]". The second-largest percentage is from Capgemini, Confideniel and Orange.<br /><br />
## **How about the Top Common Positions ?**<br />
```
# lower the words because people tend to write the same titles with different cases
connections_df['Position'] = connections_df['Position'].str.lower()

# Extract the position with frequency greater than 0.5%
connections_df['Position'].value_counts()[connections_df['Position'].str.lower().value_counts()/len(connections_df) * 100 > 0.5]
```
![image](https://user-images.githubusercontent.com/113764800/193475551-6d48ddae-2c17-4d5b-a4e9-91e1f339b38a.png)<br /><br />
```
fig6 = px.bar(connections_df.groupby(by='Position').count().sort_values(by='First Name', ascending=False)[:10].reset_index(),
       x='Position',
       y='First Name',
       labels={'First Name': 'Number'},
        title= 'Positions in my LinkedIn Network'
      )
fig6.show()
```
![image](https://user-images.githubusercontent.com/113764800/193475605-b409164c-7236-47b7-b48a-91468b61a15f.png)<br /><br />
It is great that the top common positions in my network are my target groups for networking "data scientist".<br />
Some people might have titles start with "data scientist" but also have more words in their titles. Find out all the positions with words start with "Data scientist <br/>
```
position = connections_df.Position.str.lower()
position.str.startswith('data scientist').sum()
```
![image](https://user-images.githubusercontent.com/113764800/193475691-e6e7b95c-10b9-4e74-948c-6298d1835ed1.png)<br /><br />

### **Let's visualise the Top Common Positions but this time with Wordcloud;)**<br />
```
positions = ' '.join(connections_df[~connections_df.Position.str.lower().isnull()].Position.unique())

from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator
import matplotlib.pyplot as plt
%matplotlib inline


def make_wordcloud(new_text):
    ''''function to make wordcloud'''
   
    wordcloud = WordCloud(width = 800, height = 800, 
                min_font_size = 10,
                background_color='black', 
                colormap='Set2', 
                collocations=False).generate(new_text) 
    
    fig7 = plt.figure(figsize = (8, 8), facecolor = None) 
    plt.imshow(wordcloud, interpolation='bilinear') 
    plt.axis("off") 
    plt.tight_layout(pad = 0) 

    plt.show() 
 wordcloud = make_wordcloud(positions)
 ```
![image](https://user-images.githubusercontent.com/113764800/193473668-04498a5a-fdeb-4a56-9fc4-72e697136d5f.png)












