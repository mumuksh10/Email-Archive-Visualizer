# Email-Archive-Visualizer
Developed a software which analyzes an email archive and visualizes the data using D3 JavaScript Library. Analyzed and Visualized data for approximately 60,000 emails from Sakai Developer emails archive. **You can analyze any email archive by changing the base url in gmane.py file**

How to use -:

- The first step is to spider the email archive repository.The base URL is hard-coded in the gmane.py and is hard-coded to the Sakai developer list.  You can spider another repository by changing that base url. Make sure to delete the content.sqlite file if you switch the base url.  The gmane.py file operates as a spider in that it runs slowly and retrieves one mail message per second so as to avoid getting throttled by the email archieves server. It stores all of its data in a database and can be interrupted and re-started as often as needed. It may take many minutes to hours to pull all the data down depending on how much data there is is so you may need to restart several times if the data is large.


- The second process is running the program gmodel.py. gmodel.py reads the rough/raw data from content.sqlite and produces a cleaned-up and well-modeled version of the data in the file index.sqlite.  The file index.sqlite will be much smaller (often 10X smaller) than content.sqlite because it also compresses the header and body text. Each time gmodel.py runs - it completely wipes out and re-builds index.sqlite, allowing you to adjust its parameters and edit the mapping tables in content.sqlite to tweak the data cleaning process.


- You can re-run the gmodel.py over and over as you look at the data, and add mappings to make the data cleaner and cleaner. When you are done, you will have a nicely indexed version of the email in index.sqlite. This is the file to use to do data analysis. With this file, data analysis will be really quick. The first, simplest data analysis is to do a "who does the most" and "which organzation does the most"?  This is done using gbasic.py


- There is a simple vizualization of the word frequence in the subject lines in the file gword.py. This produces the file gword.js which you can visualize using the file gword.htm. (Sakai Developer email archive example -:

<img width="901" alt="Screenshot 2023-01-19 at 2 57 42 AM" src="https://user-images.githubusercontent.com/90265721/213298729-55fccc7d-6c8d-48ee-9685-7a071e62d498.png">


- A second visualization is in gline.py. It visualizes email participation by organizations over time. Its output is written to gline.js which is visualized using gline.htm. (Sakai Developer email archive example -:

<img width="1268" alt="Screenshot 2023-01-19 at 3 00 54 AM" src="https://user-images.githubusercontent.com/90265721/213299263-1c77e4ae-d258-48c0-8660-4708f356adad.png">
