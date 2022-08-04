# Computing-descriptives-for-Continuous-variables-
#COMPUTING DESCRIPTIVES ###
### Loading the libraries ###
pacman::p_load(pacman, rio, tidyverse)

### loading and preparing the dataset (Google search data)
data <- import("StateData.xlsx") %>% as_tibble() %>% 
  select(state_code,region, psychRegions, instagram:modernDance) %>%
  mutate(psychRegions = as.factor(psychRegions)) %>% print()

### Summary for the entire tables 
data %>% summary()
### Another way 
summary(data)

### Summary for only one variable 
### Remember facebook is a catergorical variable
data %>% select(facebook) %>% summary()
### Another way 
summary(data$facebook) # this gives an output in a flat form

## Quartiles 
### Using the Tukey's five number summary 
fivenum(data$facebook) 
### This provides the minimum, lower-hinge, median, upper-hinge, maximum, also no labels 

### Boxplot stats thats shows the hinges, number of observations, confidence intervals for median 
### and outliers 
boxplot(data$entrepreneur, notch = TRUE, col = "red", horizontal = TRUE) # we see all of them here
boxplot.stats(data$entrepreneur) # you see everything here 

### Another one 
boxplot(data$facebook, notch = TRUE, col = "green", horizontal = TRUE)
boxplot.stats(data$facebook)

### Another way is to use the psych package 
p_load(psych) # Loading the psych package 
p_help(psych, web = FALSE) #Gettin information from psych

### Describing the data 
describe(data$facebook) # This provides descriptive statistics useful for psychmetrics

### Describing the  entire data 
describe(data)







