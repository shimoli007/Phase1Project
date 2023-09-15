# Phase1Project
DSF-FT06P1 Phase 1 Project 
Business Overview
Microsoft is venturing into the movie industry by establishing a new movie studio. The primary challenge is to determine what types of films are currently successful at the box office. To make informed decisions, we’ll conduct exploratory data analysis (EDA) using available movie datasets from Box Office Mojo, IMDB, Rotten Tomatoes, TheMovieDB, and The Numbers. Our goal is to provide actionable insights to assist Microsoft's new movie studio in deciding what kind of films to create.
Background of the Business
Microsoft – a global technology company – has a long history of innovation and diversification. Now, they’re looking to enter the entertainment industry by establishing their own movie studio. This move aligns with the trend of tech giants like Netflix and Amazon Prime creating original video content to engage and entertain audiences worldwide. However, Microsoft lacks expertise in movie production and distribution.
Domain of the Business
The domain of this business project is the film industry, specifically movie production and distribution. Understanding the dynamics of this industry is crucial for Microsoft to make informed decisions about which types of films to invest in. This domain encompasses aspects such as box office performance, genre popularity, critical reception, and audience preferences.
Business Case
The business case revolves around Microsoft's desire to create a successful movie studio. To achieve this, we need to answer the following questions:
·       What types of films are currently performing well at the box office?
To answer this question, we’ll analyze data from various sources, including box office revenues, IMDb ratings, and genre preferences. This analysis will help Microsoft identify genres and film characteristics that have been successful recently.
·       How can Microsoft maximize its investment in movie production?
We’ll provide recommendations on how Microsoft can optimize its budget allocation, marketing strategies, and production choices based on successful trends in the industry.
·       What audience demographics should Microsoft target?
By analyzing the data, we’ll identify target audience demographics for successful movies. This information will guide marketing efforts and distribution strategies.
Business Understanding
In order to venture into the movie industry successfully, Microsoft's new movie studio needs a clear understanding of the business domain and specific objectives to achieve its goals. Here are the details about the business they intend to enter:
Business to Venture Into:
Microsoft plans to establish a movie studio to create and distribute original video content. This venture aims to compete in the global entertainment industry by producing movies that resonate with audiences, generate significant box office revenue, and enhance Microsoft's brand presence in the entertainment sector.
Objectives
To achieve success in this venture, Microsoft's movie studio must set clear and measurable objectives. Here are the primary objectives:
To Establish a Profitable Movie Studio
The primary goal is to create a movie studio that generates a substantial profit by producing successful films. Profitability is measured through box office revenue, production cost control, and monetization of content.
To Create High-Quality Original Content
The studio aims to produce high-quality and compelling original movies that receive critical acclaim and resonate with diverse audiences. This objective is measured by IMDb ratings, Rotten Tomatoes scores, and awards won.
To Maximize Audience Engagement
The studio aims to engage and expand its audience base by catering to the preferences of various demographics. This involves identifying and targeting specific audience segments effectively.
To Optimize Investment and Resource Allocation
Efficient resource allocation is crucial. The studio aims to optimize budgets, marketing strategies, and production choices to maximize the return on investment (ROI).
Data Understanding
We’ll first load the datasets and take an initial look at the columns to check for any relationships. This will help us see if the datasets can be joined or related in any way.
To gain a deeper understanding of each dataset, we'll generate descriptive statistics for the numeric columns and check data types for all columns. This will provide insights into the distribution, count, and possible issues in the data.
"Movie Budgets" Dataset
In the "Movie Budgets" dataset:
Numeric Columns:
·       id: Has values ranging from 1 to 100, with an average of around 50. It seems like a categorization or grouping variable.
Object (String) Columns:
·       release_date: Contains the date of movie release. There are 2418 unique dates with "Dec 31, 2014" being the most frequent.
·       movie: There are 5698 unique movie titles, with "Halloween" repeated 3 times, indicating possible duplicate entries or different versions of the same title.
·       production_budget, domestic_gross, and worldwide_gross: These columns are in string format with dollar signs, which means we'll need to convert them to numeric for analysis. They contain financial information about the movie's budget and earnings.
The data types indicate that we'll need to convert the date column to a datetime format and the financial columns to numeric formats.
"TMDB Movies" Dataset
For the "TMDB Movies" dataset:
Numeric Columns:
·       Unnamed: 0: Seems like a redundant index column.
·       id: Unique identifier for each movie.
·       popularity: Represents the popularity of the movie, with an average value of around 3.13.
·       vote_average: Contains the average rating of the movie, ranging from 0 to 10.
·       vote_count: Represents the number of votes the movie received, with an average of about 194 votes.
Object (String) Columns:
·       genre_ids: Contains a list of genre IDs associated with the movie.
·       original_language: Denotes the original language of the movie, with English (en) being the most frequent.
·       original_title: Contains the original title of the movie. The title "Eden" appears 7 times, which could be due to different movies with the same name or potential duplicates.
·       release_date: Contains the date of movie release.
·       title: This column is similar to "original_title" but might contain translated or modified titles.
For further analysis, we might need to handle the genre_ids column to extract relevant genres and convert the release_date column to a datetime format.
"Rotten Tomatoes Reviews" Dataset
For the "Rotten Tomatoes Reviews" dataset:
Numeric Columns:
·       id: Unique identifier for each movie.
·       top_critic: A binary column indicating whether the critic is a top critic (1) or not (0).
Object (String) Columns:
·       review: Contains the text of the review.
·       rating: The rating given to the movie by the critic.
·       fresh: A categorical column indicating whether the review is "fresh" or "rotten".
·       critic: The name of the critic who wrote the review. Emanuel Levy seems to be the most frequent critic.
·       publisher: The name of the publication where the review was published. eFilmCritic.com is the most frequent publisher.
·       date: The date when the review was published. "January 1, 2000" is the most frequent date which could be a placeholder or default value.
The date column might need conversion to a datetime format for any time-based analysis.
“Rotten Tomatoes Movie Info" Dataset
For the "Rotten Tomatoes Movie Info" dataset:
Numeric Column:
·       id: Unique identifier for each movie.
Object (String) Columns:
·       synopsis: A brief description or summary of the movie's plot.
·       rating: The age rating of the movie (e.g., R, PG-13).
·       genre: A string that contains various genres associated with the movie.
·       director: The director of the movie.
·       writer: The writer(s) of the movie.
·       theater_date: The date the movie was released in theaters.
·       dvd_date: The date the movie was released on DVD.
·       currency: The currency used for the box office collection.
·       box_office: The box office collection of the movie.
·       runtime: The duration of the movie.
·       studio: The production studio responsible for the movie.
The theater_date and dvd_date columns will need conversion to datetime formats for time-based analysis. The box_office and runtime columns might require conversion to numeric formats after handling the currency and "minutes" strings, respectively.
"Box Office Mojo Movie Gross" Dataset
·       title: The title of the movie.
·       studio: The studio that produced the movie.
·       domestic_gross: The revenue earned from the movie in the domestic market.
·       foreign_gross: The revenue earned from the movie in foreign markets.
·       year: The year the movie was released.
Data Analysis
Next, we proceed with the actual exploratory data analysis (EDA) to uncover patterns, trends, anomalies, or relationships within the data. This can be categorized into:
Univariate EDA
This helps use analyze the distribution of certain key variables within each dataset. Potential analyses include:
Distribution of movie release dates
This analysis provides insights into the distribution of movie release dates over the years.
The bar chart reveals how many movies were released in each year, helping to identify trends and patterns in the film industry's release schedules.






 Distribution of movie ratings 
This histogram illustrates the distribution of movie ratings.
By plotting the frequency of different rating values, it offers an understanding of the typical rating range for movies in the dataset.
Distribution of movie genres 
This bar chart showcases the distribution of movie genres.
It breaks down the prevalence of various genres in the dataset, shedding light on the diversity of genres represented in the movies.



Bivariate EDA
Once we understand individual variables, we can analyze the relationships between two variables. Some potential analyses here include:
Relationship between production budget and worldwide gross
This scatter plot displays the relationship between a movie's production budget and its worldwide gross earnings.
It helps identify whether there's a correlation between higher budgets and higher earnings, providing insights into the financial aspects of movie production.






Correlation between movie ratings and box office performance
This scatter plot reveals the correlation between a movie's ratings and its box office performance, measured by worldwide gross earnings.
It helps assess whether movies with higher ratings tend to perform better at the box office, indicating the influence of critical reception on financial success.

 Comparing domestic vs. foreign gross for movies
This scatter plot compares the domestic gross (earnings within the home country) with the foreign gross (earnings in international markets) for movies.
It allows you to visualize how movies perform in domestic versus international markets and assess any trends or disparities in earnings.

Multivariate EDA
For this analysis, we'll investigate the combined impact of multiple variables on a specific outcome. Given the datasets and our objective, the following multivariate analysis options are recommended:
Genre, Ratings, and Box Office Gross:
Datasets: "TMDB Movies" and "Box Office Mojo Movie Gross" or "Movie Budgets".
Goal: Understanding how genres and ratings together influence box office performance can offer insights into which combinations are most profitable.
Visualization: A stacked bar chart that shows average gross earnings for each genre, further segmented by rating brackets (e.g., 0-2, 2-4, ... 8-10).
Production Budget, Ratings, and Worldwide Gross:
Datasets: "Movie Budgets" and "TMDB Movies".
Goal: By analyzing the interplay between production budget, movie ratings, and worldwide gross, we can assess the profitability of movies at various budget levels and ratings.
Visualization: A scatter plot with production budget on the x-axis, worldwide gross on the y-axis, and points colored by rating.
Director, Ratings, and Box Office Gross:
Datasets: "TMDB Movies" and "Rotten Tomatoes Movie Info".
Goal: Certain directors might consistently produce highly-rated movies that also perform well at the box office. Identifying these directors can be valuable for future projects and potential partnerships.
Visualization: A scatter plot with directors on the x-axis, average gross on the y-axis, and points sized by average rating.
Recommendations
Invest in Drama and Comedy
In our analysis, we found that Drama and Comedy are the most prevalent genres. Their frequent production suggests that these genres are in demand and resonate with a broad audience. Investing in these genres might appeal to a broader audience, given their popularity. Even better, they’re often produced on lower budgets compared to high-octane action or VFX-heavy sci-fi movies
High-Budget Movies Require Caution
While there's a positive correlation between production budget and worldwide gross, there are exceptions. High-budget movies that don't resonate with audiences can lead to significant losses. It's essential to strike a balance between budget and potential audience appeal.
Leverage International Markets
Many movies have shown a higher gross in foreign markets compared to domestic. Consider tailoring some productions for international appeal or collaborating with international studios.
Collaborate With Successful Studios
Some studios consistently produce high-grossing movies. Exploring partnerships or collaborations with these studios might be beneficial.
Next Steps
Expand Genre Analysis
Our genre analysis was based on data from Rotten Tomatoes. Combining genre data from other sources like TMDB can provide a more comprehensive view.
Streaming and Digital Revenues
In the current age, box office collections are just one revenue stream. Analyzing data related to streaming rights, digital downloads, and Blu-ray/DVD sales can provide a complete picture of a movie's profitability.
Feedback Collection
Understanding the target audience's demographics can guide marketing efforts and distribution strategies. Collect data on age, gender, location, and preferences to fine-tune movie production and marketing strategies. Additionally, collecting and analyzing feedback from viewers can provide insights into what worked and what didn't for a particular movie. This feedback can guide future productions.

