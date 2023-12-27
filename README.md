# EDA-netflix-movies
# 1) Case Introduction
This is one of my project that I work with my team. We are doing data analysis for our client from entertainment industry. I got task to do an exploratory data analysis (EDA) on the dataset that the client given to us. I need to extract some insights  from the dataset as initial hypothesis that can be used for further analysis.

# 2) Business Problem
The dataset contains Netflix data. From the client explanation, they suspect that the average movie length is decreasing. As proof, they've given us the average movie durations from 2011 to 2020, which are 103, 101, 99, 100, 100, 95, 95, 96, 93, and 90 minutes, respectively.
The client wants to know what is behind these decreasing duration trends. So I need to find out why the netflix average movie length is decreasing with the EDA technique. I will bring you through all the analysis process that I have done for this project.

# 3) Proving the Decreasement of Movie Length
At first, the client only share the summary data about average movie length that I have mentioned in the ‘Business Problem’ section.

As the adage say, "A picture is worth a thousand words", I want to create the visualization of the Movie Length from 2011 to 2020 so I can understand the message behind it easier. To create the visualization, I did these steps:
## 1. Create Dictionary
To examine netflix average movie duration’s data, it would be smart to start working with pandas. However, before I can do that, I need to create a DataFrame from scratch. I will begin by crafting a dictionary.
## 2. Create DataFrame
Next step, in order to transform the dictionary, movie_dict, into a pandas DataFrame, first, I need to import the pandas library. It's also important to examine the DataFrame to confirm it was constructed properly.
## 3. Create Data Visualization
The  pandas DataFrame has been created. Now, let's return to the main objective: investigate the client’s claim that the durations of movies are decreasing over time with data visualization.

Considering that the data is continuous, a line plot seems to be an appropriate choice, with the movie’s ‘Release Years’ displayed on the x-axis and the ‘Movie’s Average Durations’ (in minutes) on the y-axis. This will enable us to easily identify any trends in movie lengths. I use matplotlib.pyplot package to visualize the data, because it was one of the most widely used packages for this purpose.

![graph 1_netflix movie durations 2011-2020](https://github.com/PatriatdinRB/netflixmovies/assets/153470430/45fd659a-070e-441f-9f4b-90c1e89fec4d)

From the data visualization above, overall, it’s true that movie durations have been decreasing over the last decade! However, it is quite difficult to conduct further analysis if I only depend on the summary data from the client. There are several questions about this trend that I can't answer at the moment, including:
- How does this trend appear over a more extended time frame?
- Is there any factor that drives this trend such as movie’s genre?

# 4) Loading the Data from CSV File
After I send the data visualization and the questions, then the client gave me the original dataset in CSV format,   named "netflix_data.csv".  Let's construct another DataFrame, this time encompassing all the data. Considering the size of the dataset, printing the entire DataFrame may not be practical, so I’ll examine it by printing just the first ten rows.

# 5) Filtering the data
Great! The data is there. Now I can start analyzing movie durations with further analysis.
There are several column that tell netflix movie information. A quick scan on the DataFrame, there is a column labeled ‘type’ and the dataset also includes TV shows. Also, the 'duration' column has different units depending on the ‘type’ column. Maybe the ‘duration’ column units were: minutes (for movie) and seasons (for TV Show).
I need to filter the data by keeping the rows where the ‘type’ column is ‘Movie’. And also to be more efficient, I’ll create a new DataFrame named ‘netflix_movies’ that contains only 'title', 'country', 'genre', 'release_year', and 'duration'.

# 6) Creating a scatter plot
I have imported the raw data, filtering the data, and trimmed the DataFrame to include only the needed columns. Next step, I need to visualize the data again to observe trends over a more extended period.
This time around, I’m dealing with individual movies data instead of aggregate data. A line plot won't be suitable for current data set, so I choose a scatter plot instead. I'll continue with the year of release on the x-axis and movie duration on the y-axis.

![graph 2 (scatter plot)_netflix movie durations](https://github.com/PatriatdinRB/netflixmovies/assets/153470430/14d0ece0-d504-4c16-ae5b-97d92a67aebb)

# 7) Dig Deeper
Here comes the interesting thing. Through this visualization, I can gain more insights compared to the initial plot.

Some of the insights were:
- It’s quite clear there are more movies released after 2000 compared to before 2000,
- In 2000 - 2020 period, especially in the last ten years, the shorter movie duration (less than 60 minutes) trends starting to appear,
- What factors are behind this trend? Let’s find out.
  
Next step, I want to know more about the movies which the duration are less than 60 minutes. So I need to filter the DataFrame to include only movies with a duration less than 60 minutes and examine their genres. This could potentially give me insights into what's decreasing the average duration.

# 8) Marking non-feature films
Interesting! I found another trend. The movies that less than 60 minutes mostly are grouped to a few genres such as "Children", "Stand-Up", and "Documentaries". It is make sense, as these types of movies are typically have less duration compared to Hollywood blockbuster movies.

To make it more attractive, instead of remove these rows from the data set, I would mark them with a different colour, so I can explore the impact of these genres on the data set.

I choose loops to generate a list of colors based on the 'genre' column, then I would pass this list to the plotting function in a later step to color all non-typical genres differently!

# 9) Plotting with color
With the ‘colors’ list, now I will be able to visually assess whether these genres could be the reason behind the movie duration decreasement trend.
This time, I’m also enhance the plot with additional axis labels and a fresh theme using plt.style.use().

![graph 3 (scatter plot)_netflix movie durations (color marked)](https://github.com/PatriatdinRB/netflixmovies/assets/153470430/18cbe94e-3d02-4c55-88e8-0d2448d6783c)


# 10) EDA Conclusion
Finally, I have done the EDA Analysis.  As I hypothesized, non-typical genres like children's movies and documentaries are clustered towards the lower half of the plot. It means these genres has an impact on  Netflix Movie duration decreasement trend in 2000-2020 period. However, we can't draw definitive conclusions until we conduct further analysis.

EDA Conclusion:
- Movies genres have potentially significant impact to Netflix Movie duration decreasement trend in 2000-2020 period.
- Further analysis is needed to draw definitive conclusions.

