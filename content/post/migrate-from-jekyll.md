+++
title = "Graph 1: Scatterplot"
date = "2015-10-10T13:07:31+02:00"
tags = ["jekyll", "migration", "hugo"]
+++

## Step One: Extracting the Data
In order to set up a scatterplot, you must first extracte the data. We do that by writing: 

<!--more-->

    query<-"SELECT playerID,sum(HR) AS career_HR ,sum(SO) AS career_SO
    FROM Batting
    GROUP BY playerID
    HAVING sum(HR)>=400"
    result<-sqldf(query)


We place the code into result by writing result<-sqldf(query). We do this so that we have a common place to store the code, and for continuity through Step 2. 

    
## Step 2: Visualize the Data
Next, we will use the data we extracted in step one to visualize the data through a scatter plot. In order to do this, We had to install the ggplot2 package. Other packages installed include sqldf and Lahman. Notice that you can change the color of the scatterplot as well as the size of the points. You can also change the x and y axis. We do this by writing 

<!--more-->

        ggplot()+
          geom_point(data=result,aes(x=career_SO,y=career_HR), size=3, color="blue")+
          ggtitle("Career Strikeouts vs Homeruns for Great Hitters")+
          xlab("Career Strikeouts")+
          ylab("Career Homeruns")


## Step 3: Run the Data
This step is simple. All you must do is highlight the above information, and select run. Your scatterplot will appear. If you wish to make changes, simply go back to the above code, make changes, and run the code again. 

``` {r}
ggplot()+
  geom_point(data=result,aes(x=career_SO,y=career_HR), size=3, color="blue")+
  ggtitle("Career Strikeouts vs Homeruns for Great Hitters")+
  xlab("Career Strikeouts")+
  ylab("Career Homeruns")

```

"img/Rplot.png"



