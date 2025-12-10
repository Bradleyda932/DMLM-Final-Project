# Data Mining and Linear Modeling: Final Project

## **Video Game Data: A Statistical Analysis & Prediction**

---

### Bradley Antholz

---

## **Project Overview**

This project explores video game sales data from 1980 to 2016/2017 with the goal of identifying patterns between companies, genres, and platforms, and determining what makes a video game successful. The project includes data cleaning, variable creation, predictive modeling (Random Forest and Logistic Regression), and visualization.

---

## **The Dataset**

**Source:** [Video Game Sales (Kaggle)](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

This dataset contains global, North American, European, and Japanese sales numbers, along with game Name, Publisher, Platform, Genre, and Year.

The project focuses on:

* Creating interpretable variables for analysis
* Grouping companies by size
* Predicting game success using statistical models

### **Cleaning Process**

* Removed regional sales columns and kept **Global_Sales**, as it was the most consistent.
* Lost the **Year** variable due to an accidental `select()` call; restoring it would have required extensive backtracking, so it was omitted.
* Created several new variables (detailed below) to enhance analysis.
* Combined duplicate publisher names and renamed unclear platform abbreviations (e.g., "TG16" → "TurboGrafx-16").

---

## **The Process**

This section outlines everything done after the initial cleaning phase.

### **Created Variables**

The following variables were created to support analysis:

* **type_of_game** and **type_of_game_BV**: Distinguish between standalone titles (e.g., *Pokémon Blue*) and series titles (e.g., *Madden*).
* **Sales_Bracket**: Makes global sales numbers easier to interpret.
* **Publisher_Size**: Categorizes companies as Small, Medium, or Big using:

  * Small: ≤ 5 games
  * Medium: ≤ 100 games
  * Big: > 100 games
* **Game_Count**: Number of games associated with each publisher.
* **successful_game_BV**: Binary variable defining game success:

  * ≤ $1 million global sales → 0
  * (>) $1 million global sales → 1

These variables support predictive modeling and pattern identification.

---

## **Code Walkthrough**

The project is split into three R files. Run each in the order below.

### **1. fp_cleaning (df1)**

Responsible for all cleaning steps. Comments explain each transformation. Ends with an `lapply()` check to ensure variables look correct.

### **2. fp_prediction (df2)**

Contains the main statistical work:

* Creates new binary variables
* Performs Random Forest and Logistic Regression
* Generates ROC curves and evaluates thresholds
* Produces predicted success probabilities

### **3. fp_visuals (df3)**

Generates visualizations, including:

* Series vs standalone comparisons
* Highest-selling genres
* Publisher clustering analysis

These charts help summarize findings for presentation.

---
