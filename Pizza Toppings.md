# SAS-Pizza Toppings

### Project Overview
A gourmet pizza restaurant is considering adding new toppings to its menu. Each month they survey 10 customers about their preferences for three different toppings. The restaurant wants data on several different toppings. So they don’t always ask about the same three toppings. Customers rate each topping on a scale of 1(would never order) to 5 (would order often). The restaurant wants to compute average ratings for all toppings, so the ratings variables need to be numeric. 

### Data Source
From "Pizza(3).csv" file.

### Tools
- Excel
- SAS
- 
### Data Cleaning/Preparation
1. Obtain the data.
2. Scrub the data: handle with repetitive valus, missing valus and incorrect values.
3. Format the data.

### Exploratory Data Analysis
Key questions, such as:
1. what are the average ratings for all toppings?

### Data Analysis
If use Import, some of the variables will be strings rather than numeric so need to use DATA step.
Code:
data pizza;
    infile 'E:\Users\bxw190014\Desktop\sas Hw1\Pizza(3).csv' firstobs=2 DSD Missover; 
    input SurveyNum Arugula PineNut Squash Shrimp Eggplant;  
run;
proc print data = pizza;
run;

/*calculate avg ratings using proc means*/
proc means data=Pizza mean;
var Arugula PineNut Squash Shrimp Eggplant; 
output out=AvgRatings mean=;
run;
/*rename variables and create final dataset*/
data AvgRatings;
set AvgRatings;

/*Reshape the data*/
array Toppings[5] Arugula PineNut Squash Shrimp Eggplant;
do i = 1 to dim(Toppings);
	Topping = vname(Toppings[i]);
	AvgRating = Toppings[i];
	output;
end;
drop i Arugula PineNut Squash Shrimp Eggplant _type_ _freq_;
run;

### Results/Findings


### Recommendations

### Limitations

### References
