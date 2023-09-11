# Google-Data-Analytics-Capstone: Cyclistic-Bike-Share-Analysis
author: "Zainab Zanna Ahmad"
date: "2023-11-9"

---
# Introduction

Hypothetically, I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. 

Therefore,my team and I were tasked with understanding how casual riders and annual members use Cyclistic bikes differently. From these insights, the marketing team will design a new marketing strategy to convert casual riders into annual members. 

---

# Background

In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that
are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to
do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why
casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are
interested in analyzing the Cyclistic historical bike trip data to identify trends.

---

## Business task
Find out how annual members and casual riders use Cyclistic bikes
differently.
My answer will help the company design marketing strategies at converting casual riders into annual riders.

---
## Preparing the data
The data was gotten from **Motivate International Inc**.It was retrieved here: https://divvy-tripdata.s3.amazonaws.com/index.html

---
## Data organization
The data was organized in CSV files by months, and for this project, the most recent **12 months** data from February 2022 to January 2023 was used. Each of the data files consists of 13 columns.

---
## Data credibility and bias
The data is **reliable** as it was gotten from a reliable source.The data is **original**, directly collected by Motivate International Inc. It is **comprehensive** as it includes the necessary information to carry out this project.It is also **current**, and **cited**. There is **no any bias** issue with the data.

---
## Licensing, privacy, Secuirity and accessiblity
The data has **permit** to be used. Here is the license agreement: https://ride.divvybikes.com/data-license-agreement 
Personal **identifiable** data has been removed. The data **protects** the **privacy** of its subjects and is easily **accessible**.

---
## Integrity and problems with the data
The data contains some **discrepancies**,like blank values, inconsistent number of id characters and so on. But it was cleaned to make sure its **integrity** is intact.

---
## Choice of tools and reason
**R** was used to **merge**, **clean**, **analyze** and **visualize** the findings, because the data is **large** and R makes it **easier** to work with large data set.

---
### Loading the necessary libraries

```{r message=FALSE}
library(tidyverse)
library(dplyr)
library(janitor)
library(skimr)
library(readr)
library(lubridate)
library(ggplot2)
library(data.table)
library(parsedate)
```
# Data collection

I used excel to check the data through out the 12 files to make sure the column numbers and names are the same. I further load the data into R.

### Loading the data of the 12 individual months into discrete data frames

```{r message=FALSE}
feb <- read_csv("divvy-tripdata-202202.csv")
march <- read_csv("divvy-tripdata-202203.csv")
april <- read_csv("divvy-tripdata-202204.csv")
may <- read_csv("divvy-tripdata-202205.csv")
june <- read_csv("divvy-tripdata-202206.csv")
july <- read_csv("divvy-tripdata-202207.csv")
aug <- read_csv("divvy-tripdata-202208.csv")
sep <- read_csv("divvy-tripdata-202209.csv")
oct <- read_csv("divvy-tripdata-202210.csv")
nov <- read_csv("divvy-tripdata-202211.csv")
dec <- read_csv("divvy-tripdata-202212.csv")
jan <- read_csv("divvy-tripdata-202301.csv")
```
Here, the individual data set of 12 months were loaded into R in different data frames, so that it could all be merged into a single file

# Data combining

Merging the 12 months data into a data frame
```{r}
all_trips <- rbind(feb, march, april, may, june, july, aug, sep, oct, nov, dec, jan)
```
The data has been merged into a single file called all_trips

# Data exploration

```{r}
skim(all_trips)
```


