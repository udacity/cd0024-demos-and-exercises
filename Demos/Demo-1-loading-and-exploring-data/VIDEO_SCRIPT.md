# Demo Video Script: Loading and Inspecting Data with Pandas and Polars

**Target Length:** ~10 minutes | **Speaking Pace:** ~130–150 words/min (~1,300 words)

---

## [0:00–0:30] INTRO

Hey everyone, welcome to this demo on loading and inspecting data. The first step in any data analysis project is understanding what you're working with, and that's exactly what we're going to cover here.

We'll explore a dataset using two of the most popular Python libraries for data manipulation: pandas and Polars. By the end of this demo, we'll have loaded our data, peeked inside it, and will have a solid sense of what we're working with.

Let's jump right in.

---

## [0:30–2:30] LOADING DATA WITH PANDAS



First we're going to import our libraries, namely pandas and Path from pathlib (because we don't need the entire pathlib library, we import only one single part of it, namely Path). We're using Path for file paths because it's a best practice—it ensures that our folders paths (which might use forward or backward slashes) work across all operating systems, that is Windows, Mac, and Linux, so the code stays portable no matter what system we're on.

We're going to set the display option with `pd.set_option('display.float_format', '{:.2f}'.format)`. With this setting we get only 2 decimals in all tables. A amall detail, but it makes the output much easier to read when we're presenting results.

We're working with a file called `synthetic_data.csv`. This is a dataset with observations on individuals and their healh—things like activity levels, age groups, weekly workouts, daily steps, heart rate, and more. The data was synthetically generated using random numbers for illustrative purposes, but it's designed to closely match what you'd see in real-world health data.

We're going to load the data with `df = pd.read_csv(data_path)`, and save it as a variable called df, you can give this any name you prefer, but it in the Python community it has become a convention to call our data 'df' which is short for dataframe, but you can also give it a more descriptive name if you work with multiple datasets. 

Let's look a little closer at what this line does. We are first calling the pandas library which we named pd, and then access the content of that library using the dot accessor, you can think of the dot as your key card to open the door to the library. After that, all the methods of that library are available to you, and we will use read_csv fir our purpose. The documentation of pandas will tell you exactly which methods are available and what input they expect so it is always a good habit to review this to ensure we are using a method correctly. read_csv expects as an argument inside of the paranthesis, the path to the dataset we want to read and we will pass along the path we created in the line above.


---

## [2:30–4:00] INSPECTING WITH PANDAS: HEAD, INFO, DESCRIBE

Now that the data is loaded, we're going to see what's inside. First we'll call `df.head()`, which shows the first five rows of the DataFrame. Right away we can see the structure—the column names across the top and the first 5 observations for each column. We're doing this to get a quick first impression and to spot any obvious issues incorrect values or unexpected formats.

Next we're going to call `df.info()`. This is like reading the blueprint of the dataset. It tells us how many rows we havehow many columns and the data types for each column, which are floats, integers, and objects, and whether there are any missing values. Here, every column has 700 non-null values, so we have no gaps. We're running this because it's essential before analysis: if we assumed a column was numeric when it's actually text, we'd run into errors later.

Then we're going to run `df.describe()` to get a statistical summary. This gives us a snapshot of all the numeric columns—count, mean, standard deviation, min, max, and the quartiles. In just a few seconds we can see that people in this dataset average about 8,560 steps per day, or that resting heart rate ranges from roughly 56 to 84. These numbers help us understand the scale and spread of the data and spot potential outliers.

Finally we're going to show `df.dtypes`, which gives a quick column-by-column view of the data types without all the extra information from info. Sometimes that's all we need.

---

## [4:00–4:30] TRANSITION: WHY POLARS?

We have now seen to load and inspect date with pandas. But there's another library we want to explore, namely Polars. Polars is a modern DataFrame library that's become incredibly popular because it's built for speed—it often outperforms pandas on large datasets. The syntax is very similar or identical for the basic commands, which is by design, because it was meant to allow for an easy transition from pandas.  We're now going to repeat everything we just did, this time using Polars, so you can see that these techniques are universal even when the code looks a little different.

---

## [4:30–7:00] LOADING & INSPECTING WITH POLARS

We're going to start by importing polars as `pl` and using the same Path for our CSV file. Then we're going to load the data with `pl.read_csv()` and store the result in `df_pl`, you can give this any name you prefer, but we will use this name to distinguish it from the dataframe we created earlier with pandas. Notice what we just did here, we used again the dot accessor to get access to the methods of the library we are using, and because polars was designed for an easy transition, many methods were given the same name as in pandas. So while what are doing here looks very simlar to what we did earlier with pandas, keep in mind that under the hood you are using a different library with a method that has the same name but runs different code with a slightly different outcome. 

Next we're going to call `df_pl.head()` to preview the data, again, a method that has the same name is its pandas equivalent. Just like in pandas, this shows the first five rows. But polars also displays the shape right at the top—five rows, nine columns—and shows the data types directly in the column headers, which is already pretty informative.

Next we'll here's where Polars differs from pandas. Polars doesn't have a single `info()` method. So we're going to use a few separate attributes to get the same information. `df_pl.shape` gives us the number of rows and columns as a tuple. `df_pl.schema` shows the column names along with their data types. And `df_pl.estimated_size('mb')` tells us approximately how much memory the DataFrame is using. It's a bit more explicit, but we end up with the same picture: 700 rows, 9 columns, about 0.05 megabytes.

Then we're going to call `df_pl.describe()` for the statistical summary. We get the same kind of output—count, null count, mean, standard deviation, min, max, and the percentiles. One thing we want to point out is that Polars includes string columns in the output too, showing values like "Lightly Active" for the minimum or "Very Active" for the maximum. Different presentation, same goal: understanding the distribution of the data.

Finally, for data types, Polars gives us another option, namely `df_pl.dtypes`, which returns a simple list of the data types in column order—String, String, Int64, Float64, and so on. It's compact and useful when we just need the types, and not the column manes (which is what schema gives us). Use dtypes when we want a quick list, and schema when we need to see which type goes with which column.

---

--

## [8:30–10:00] WRAP-UP

We've now built a solid foundation for loading and inspecting data. We loaded a CSV into a Python, previewed the data, checked the structure, got statistical summaries.

In the data analysis that follows these steps, you'll build on these foundational steps and expand upon them. But it all starts here, with understanding what you have before you try to analyze it.

I hope you found this video informative on your journey towards analyzing data in Python.
---

