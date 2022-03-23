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