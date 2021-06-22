

# [Project 1 - Bike-Share Case Study](http://htmlpreview.github.io/?https://github.com/dswhite11/DW_portfolio/blob/c81faca8b4e40771da8f49ee5e10e88496daba2c/cycling_project/cycling_notebook.html)

I created this report from an R Notebook as the capstone project to Google's Data Analytics Certificate course, hosted on Coursera. The purpose of the project was to analyze the data of a bike-share company in Chicago, and provide recommendations to the company's marketing team for their new ad campaign.

The report is extremely detailed and shows nearly all the steps I took in the analysis process. It begins with uploading and manipulating the data in PostgreSQL and Excel, then moves to cleaning and reorganizing the data, and ends with visualizations created in RStudio and Tableau.

### Summary

- Used SQL to combined datasets and explore data
- Calculated ride times in SQL, and cleaned data of negative ride times
- Using SQL, calculated mean ride times, weekend and weekday ride counts, mean weekend and weekday ride counts by month
- Used R and **Lubridate** library to converted ride times (HH:MM:SS) to decimals
- Used SQL to clean the latitude and longitude data
- Plotted mean ride times, weekend/weekday ride counts, mean weekend/weekday ride counts using **ggplot2** library
- Created map visualizations in Tableau

### Applications used

- PostgreSQL
- Postico
- Excel
- RStudio
- Tableau

### Languages used

- SQL
- R

### Preview

![Animated gif](/images/cyclistics_anim_screenshot.gif)

Visualizations created:

<div>
  <a href="/portfolio/images/mean_daily_ride_count.png"><img src="/portfolio/images/mean_daily_ride_count.png" height=200 width=200></a>
  <a href="/portfolio/images/mean_ride_time_per_month.png"><img src="/portfolio/images/mean_ride_time_per_month.png" height=200 width=200></a>
  <a href="/portfolio/images/mean_ride_time_weekend_weekday.png"><img src="/portfolio/images/mean_ride_time_weekend_weekday.png" height=200 width=200></a>
  <a href="/portfolio/images/ride_geographical_distribution.png"><img src="/portfolio/images/ride_geographical_distribution.png" height=200 width=200></a>
</div>
   

---

# [Project 2 - Movie Correlation Project in Python](/movies_project/Movie Correlation Project.md)

### Summary

### Applications used

- Jupyter Notebooks

### Languages used

- Python

### Preview

---

# [Project 3 - Reading Log Visualization](https://public.tableau.com/profile/david.white5299#!/vizhome/Books2020_16052071128230/Daves2020ReadingLog)

This project is a visualization of all the books I read in 2020. It is interactive, and allows the user to read my review of each book by selecting an icon on the chart at the top. Selecting an icon will also highlight the book's page count in the bar graph.

I used a web-scraping program based in R to scrape the GoodReads.com website for page numbers for all of the books. 

### Summary

- Stored data in Google Sheets
- Used Tableau to create visualization
- Used web-scraping tool in R to gather data

### Applications used

- Tableau
- Google Sheets
- RStudio

### Languages used

- R

### Preview

![Animated gif](/images/readinglog_tableau_gif.gif)

---

# [Project 4 - Lakers Game Analysis](http://htmlpreview.github.io/?https://github.com/dswhite11/portfolio/blob/d89e5016de149971961424d6e08a6c361dae2344/laker_project/lakers_markdown_intro.html)

A fun project using the built-in Lakers data from the Lubridate package. I practiced filtering and plotting with ggplot2 to analyze each Laker's performance in the first game of the season, against the Portland Trailblazers. The notebook goes through every step of my thinking process, so if it seems tedious and wordy, that's why.

### Summary

- Data comes from the **Lubridate** library in R
- Filtered the data using **dplyr** library
- Used **ggplot2** to create visualization

### Applications used

- RStudio

### Languages used

- R

### Preview 

![Preview](/images/lakers_screenshot.png)
