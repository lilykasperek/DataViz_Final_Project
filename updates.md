## March 21

I decided I wanted to do a blogdown project, and looked at different blogdown websites for inspiration. I looked at many different data sets using Kaggle. 

## March 23 Beginning of Class

I created a new project for my blogdown website, found and imported different data sets to use for different posts, created some new posts, linked my GitHub, and minimally messed around with some of the data sets I found. I am not sure how to link the new project/website to GitHub and am not sure how to push the work I did. 

```{r}
library(tidyverse)
library(ggthemes)
pol_donations <- read_csv("/Users/lilykasperek/Desktop/my-website/content/post/2022-03-22-first-post/sports-political-donations.csv")
pol_donations
```

```{r, message = FALSE, warning = FALSE, echo = FALSE}
owner_rank <- pol_donations %>% group_by(Owner) %>%
  summarise(n = n()) %>%
  arrange(desc(n)) %>%
  mutate(rank = rank(desc(n))) %>%
  filter(rank <= 25) %>%
  mutate(owner = fct_reorder(.f = Owner, .x = n))

ggplot(data = owner_rank, aes(x = n, y = owner)) +
  geom_col() +
  labs(title = "Most Frequent Donators Among All Leagues",
       y = "Count",
       x = "Owners") +
  theme_fivethirtyeight()
```

```{r}
library(tidyverse)
blockbusters <- read_csv("/Users/lilykasperek/Desktop/my-website/content/post/2022-03-22-first-post/Blockbusters_2019-1977.csv")
blockbusters

library(tidyverse)
history_of_rock <- read_csv("/Users/lilykasperek/Desktop/my-website/content/post/2022-03-22-first-post/history-of-rock-spotify.csv")
history_of_rock
```

```{r}
led <- history_of_rock %>% filter(artist == "Led Zeppelin")

ggplot(data = led, aes(x = release_date, y = popularity)) +
  geom_line() 
```

## March 23 End of Class

I created a lollipop chart for political donations and continued to mess around with different data sets. I am working on customizing the chart and adding more to it. 

## March 28 Beginning of Class 

I changed my lollipop graph. Instead I made an interactive graph with the team owners who donate the most frequently, colored by league, displaying the amount donated when you hover over the points. I am stuck on ordering the owners by the amount of donations they made. I made another interactive graph. This graph is only looking at NFL team owners and shows the top 25 highest donations made and which owner made them (some owners made multiple). The donations are colored by political parties and when you hover over the points it shows where the donations were made. For both I want to figure out how to put multiple labels on the points. I also made a static graph of blockbusters from 1977 to 2019 by release year and IMBD rating. They are colored by MPAA Rating and the films with the 5 highest IMBD Ratings are labeled as well as the films with the 5 lowest. I filtered out one missing MPAA rating. I am now working on an interactive Lollipop chart showing the popularity of nirvana songs with release dates but I can’t figure out why it won’t work. 

## March 28 After Class 

I figured out why the nirvana lollipop graph was not working and fixed it. I also added a colour scale and made it interactive. I made a table as an extension of my visualization displaying the most frequent donators and am now trying to figure out a way to display the most frequent donator's data. 

## March 30 Beginning of Class

I changed the color scale on my first two political donation visualizations.I created a simple visualization to display what party the recipients of donations made by Charles Johnson are associated with. I noticed that the same recipient had a different name in my recipients example, so I went back and noticed the same thing for others. I used ```fct_recode``` to fix this and my two visualizations. I changed the theme for many of my visualizations. I modified my blockbusters visualization so it was interactive and less visually overwhelming. I tried to rename axis ticks for the first visualization but can’t figure out what I am doing wrong. I capitalized interactive label on nirvana visualization. 

## March 30 After Class

I messed around more with the blockbusters data set created two simple visualizations that I am hoping might lead somewhere. I also created a simple visualization for the history of rock data set. I struggled this class with ideas for visualizations. 

## April 4 Beginning of Class

I rearranged the order and changed the titles of my political donations visualizations so they flow in an order that makes sense. I decided to change the variable I was coloring by and the color scale for my visualization looking at how much the most frequent donators donate. Added a label to political donation top donator visualization to show how many donations were made to each party. Made a new table to show where the owner who donates the most donates to. Made a visualization displaying how many blockbusters the major domestic distributors have produced. Added themes to my tables with library(kableExtra). Moved the position of the legend/changed the themes on a few donations visualizations. Added a definition of blockbuster - not all films are blockbusters so data set obviously does not contain all films from 1977-2019. Need help coming up with more creative questions. Tried to use geom_density_ridges but it is not working and I’m not sure why. Tried to make line plot with multiple different lines but realized the data set I created had artists with only one observation 

## April 4th After Class

Mostly worked on using theme() to change different elements of my visualizations so that they look better, and will probably continue to work on this outside of class as well. I am fairly sure I have decided on a common theme, at least for my political donations visualizations. 

## April 6th Beginning of Class 

I continued working with theme(), and now have a common font and theme in my political donation visualizations. I should be done with these visualizations except for some problems I need to fix. I added the scroll feature to one of my tables. I changed my blockbuster visualization so it is not as simple - it is now faceted. I continued common font and theme elements for my other visualizations. I changed a bar plot into a lollipop plot. I am debating if I want to keep my interactive plot or start over so I can make it more complex. Came up with new goals: fix order on political visualization, figure out how to change axis labels representing monetary values from scientific notation, figure out how to create geom_density_ridges() visualization. Need to come up with more visualizations - might change/add data sets, thinking about making a map or app for one subsection of blogdown. 

## April 6th After Class 

Fixed the order of the y axis for my political donations visualization so it is ordered from most observed donations to least. Figured out how to change labels from scientific notation to monetary values. Decided to get rid of my interactive plots because they can not really be customized. Installed library(ggpmisc) and am trying to figure out how to use it to plot tables on my visualizations. Need to make more complex visualizations, add more data sets etc. 

## April 11th Beginning of Class

I worked on trying to figure out how to add a table to a plot but could not figure it out. I should be close to done with political donations visualizations after figuring out how to add a table to plots. I tried to follow along to actually create a blogdown with the instructions you sent a while back but got confused after activating my GitHub pages. I wasn’t sure how to run code in the terminal. I started thinking about/working on my written description a little bit. I made a few small tweaks to some visualizations. I looked for new data sets because I am not sure what visualizations to make with the data sets I have now. I found an interesting data set of Forbes Billionaires List from 2021. I am debating not using the blockbusters and history of rock data sets anymore. I tried to think of questions and created some simple visualizations for a little with the new data set.  

## April 13th Before Class

I added a title, changed the font, releveled factors in the legend, and renamed one of my x labels for a new plot examining Forbes Billionaires from 2021. Found another version of this data set on Kaggle that added Residence, Citizenship, Relationship Status, Number of children, Education, whether or not the billionaire was self-made, and then another data set with the geoinformation.Had to fix the visualization showing the average age of billionaires by country. For some reason R let me change a character variable to a numeric variable the last session and it worked with the original data set but it did not work this session. With the second updated data set, age was dbl so the visualization worked. I then added labels, changed the font, and made other minor modifications to this visualization using theme(). After this, I played around with the forbes_billionaires data set and worked towards thinking of some more ideas for other visualizations. I also merged the two data sets, also did some tidying with separate. 

## April 18th Before Class

Decided to scrap the history of rock and blockbusters data sets for now. The visualizations I had were underdeveloped and I was really struggling to come up with more. I also think that the Forbes Billionaires data set fits in better with the political donations data set. My goal will be to find another data set that fits in with these two so that I can have three pages on my blog down. I moved the work I did with the other two data sets into another markdown in case I want to go back to it. I added specific questions that are answered by my visualizations. I also added the average amount spent on political donations, and a table showing the sum of how much money the top donors spent on their donations. Added a table to accompany visualization displaying the count of donations per party. Created a lollipop chart for Forbes billionaires. Added labels with outliers for average billionaire age by country. Made a lollipop chart that has points/segments above and below the average USA billionaire's net worth for billionaires in the fashion/retail industry in the United States. Just continued playing around and making minor tweaks as well. 

## April 18th After Class

This class I worked on modifying theme components of my visualizations. I made a few changes and tried to come up with some new ideas so I can finish my Forbes Billionaires section and move on to the last data set I want to use. 

## April 20th Before Class 

Fixed space between subtitle and caption and legend for the first Forbes visualization. 
Worked on making the visualizations “prettier." Changed final lollipop visualization to a bar chart since it is visualizing counts of categorical data. Made visualization showing how many are self_made and how many are not. Kept working on ideas to represent the education/some other variable of Forbes billionaires to make another visualization but after that should be done with this section for now. Tried to find another data set but couldn’t find one. Need to keep looking for last section. 

## April 20th After Class 

Today I kept working on improving the visualizations I had and made several new visualizations as well. My next step is finding another data set and working extensively with that data set. 

## April 25th Before Class

Throughout the weekend I found a new data set to use for my third and final section of my blogdown. I also finalized my theme modifications on my other visualizations and have made them pretty consistent with the spacing and text sizing. I have been working a lot on the style component of my project/visualizations. I am working on coming up with one or two more questions for the forbes billionaires data set, as well as the questions for the new data sets I found. 

## April 25th After Class

This class I worked on setting up the actual blogdown website and connecting it to Git for a good amount of time. I also started making some preliminary visualizations for the last data set I want to use in this project. 
