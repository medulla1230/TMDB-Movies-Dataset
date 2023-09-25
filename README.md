# TMDB-Movies-Dataset

### Introduction

This project is part of the projects in the Data Analyst NanoDegree Program from Udacity.

The data set contains information about 10,000 movies collected from The Movie Database (TMDb), including user ratings and revenue. 
The objective of this project is to explore the TMDB movie dataset and answer questions like the genres that have been popular year by year, the properties associated with 
movies that have the highest revenues and the count for the most popular genres across the years.

### Data Wrangling

In this section, we will load in the data and inspect it to check for cleanliness, and then trim and clean the dataset for analysis.

There are 10866 rows and 21 columns. 
Some of the columns that have rows with missing values include imdb_id(10 missing values),cast, homepage, director, tagline, keywords, overview, genres, production_companies

### Taking note of dataset issues

For the movie data, the following columns have null and missing values and a lot of them.
- imdb_id(unique identifier of the movie in the IMDB database)
- cast(The list of actors involved in the movies)
- homepage(The website of the movie. More than two-thirds of this data is missing)
- director(The name of the person directing the movie)
- tagline(the catchphrase used for the movie)
- keywords(special words used to identify the movie)
- overview(a brief description of what the movie is about)
- genres(The movies category)
- production_companies(The name of the companies that collaborated to produce the movie. Almost 10% of this data is missing).

There are a lot of potential reasons for these missing values. Was the data ever tracked? Was it lost in history? Is the research effort to make this data whole worth it? So we will take note of where the dataset isn't perfect and start uncovering some insights
The first part of the data cleaning involves removing the duplicate rows as well as columns that will not be helpful in providing insights such as cast, tagline, overview, keywords, imdb_id, id

### Exploratory Data Analysis
Here we will answer a few questions that will help us understand our data better
- How has runtime changed over the years?
  
According to Google, a movie is considered as a video that has a runtime of at least 80 minutes. So in this section, We will filter out movies that have less than 80 minutes of runtime and then look at how runtime has changed over the years.
Most movies have an average runtime of 100 minutes or more, which is about 1.7hours and the longest movie runtimeis 900 minutes, an equivalent of 15 hours.

![image](https://github.com/Irene-arch/TMDB-Movies-Dataset/assets/56026296/99df6127-26c9-488a-b7cc-02a3879b567b)

Over the years, the average runtime of movies has been around 100 minutes and has not really changed much.

- Longest movie in the Dataset?
- Shortest Movie in the Dataset?
- Which genres are most popular from year to year?
- Which were the top movie genres overall?
- Which properties are associated with movies that have high revenues?

Since we already know that the revenue and budget columns have no null values, We will check for the number of zero values that exist as these will affect the accuracy of our findings

- What is the correlation betwen the attributes in the dataset?

 A new column profit will be added to the dataset by getting the difference between revenue and budget.

 ```python
movies['profit'] = movies['revenue_adj'] - movies['budget_adj']
plt.figure(figsize=(15, 7.5))
c_relation = movies.corr()
sns.heatmap(c_relation, cmap='coolwarm', annot=True)
c_relation
```

![image](https://github.com/Irene-arch/TMDB-Movies-Dataset/assets/56026296/acccf434-3260-44f6-a833-731a14500860)

### Conclusions
- The average runtime of majority of the movies is between 90 and 110 minutes.
- The genres with the most popularity are adventure and animation while history and music are the least liked genres.
- The movie runtimes have not changed much over the years and are largely around 110 minutes.
- Genres that resulted in the most revenue are action and drama.
- The longest movie in the dataset is called The Story of Film: An Odyssey and has a runtime of 900 minutes.
- The shortest movies in the dataset are Mythica: The Necromancer, Ronaldo, Anarchy Parlor, Quatre Ã©toiles, Jean-Philippe, Mission Kashmir and have a length of 61 minutes each.
- From the heatmap, we can see that many attributes have a high positive correlation with one another which also shows how co-dependent they are. Popularity has a high positive correllation with vote counts and profits which implies that the higher the vote count, the more popular a movie becomes and that also results in more profit.

### Limitations
I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue
