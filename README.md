# Data Mining and Linear Modeling: Final Project
## ***Video Game Data: A statistical Analysis & Prediction***
---
### Bradley Antholz
---
## *Project Overview*
> This section will be a timeline of everything from finding the data to cleaning it and beyond.
---
### *The Dataset*
> [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

 * This dataset is from Kaggle, and thank you to Professor Follett for helping me find it. In short, it is a dataset of video games ranging from 1980 to 2016/2017 of North American, European, Japanese and total Global Sales. Included are their Publisher, Platform, Genre, and of course, Name. 
* The overall goal of this project was to create patterns between companies and sales and see what makes a successful game, well, successful. This process will be explained in detail later on. 


##### Cleaning Process
  * I removed all sales columns except global sales, because I didn't feel they were needed, as global sales was the only consistent one (the others had 0's).
  * I did not intend to remove year, however during the process ChatGPT used select(), which did that very thing. I tried to go back and fix it, but it turned out to be either very difficult or impossible, so I gave up.
  * Despite that, I created several variables as well, which will be further explained later on.
  * Last, I combined several entries or renamed them, as doing so made the data more consistent and easy to read. For example, I don't know about you, but I have no idea what Platform "TG16" was, so I renamed it (after looking up what it was) to "TurboGrafx-16". Along with this, I combined a few companies who had multiple branches who put out video games, such as Sony, who has listed: Sony Computer Entertainment, Sony Computer Entertainment Europe, Sony Online Entertainment, among others.

## *The Process*
> This section will be about everything I did with the dataset after the initial cleaning phase, but up to data visualizations.
* I created the following variables: type_of_game, Sales_Bracket, type_of_game_BV, successful_game_BV, Game_Count, Publisher_Size. Here is a detailed explanation of each one, and why they exist:
  * **type_of_game and type_of_game_BV**: Created to distinguish between if a game was a solo title (think Pokemon Blue) or part of a larger series (think Madden).
  * **Sales_Bracket, Publisher Size**: These were created mostly just for me and the audience, as the values of sales numbers are hard to understand, and it can be hard to know what publishers are "big" and who are not. Pub_Size is used for statistical analysis later on.
  * **Game_Count** was created to establish Pub_Size, as we needed a threshold for what constitutes as a big or small company. To do this, the cutoffs were: Small: 5 games; Medium: 100; Big: 100+. Here is where our goals come in, we want to preform deep statistical analysis with all 3 categories of Pub_Size in order to achieve what I'm after.
  * Last, **successful_game_BV**. This was the backbone of the entire operation, as I tested every variable against it. To establish it, though, the cutoff was at or below $1 Million in global sales = 0, above = 1.

### *Code Walkthrough*

> I made 3 R files, one for cleaning, one for prediction and one for visualization. they will be referred to by their proper names in the following paragraphs.

##### fp_cleaning (df1)

* This dataset is all about cleaning, with comments in the code explaining what everything means. The file is called fp_cleaning.R, and the corresponding dataset is df1. At the end of the file, I like to use lapply to make sure everything looks right. The main purpose of this dataset is to setup the other datasets and make analysis easier.
  *  All that is needed to run the code is highlight every line and hit run.

### fp_prediction (df2)

* Here is the meat and potatoes of this project. This file is about establishing parameters for prediction, setting binary variables, and preforming regression analysis. WIth df1 ready to go, at the top of this file we create df2 from df1, then modify df2 how we want. We are using a random forest and logistic regression (GLM) for prediction, using Global_Sales as our BV.




