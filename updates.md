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