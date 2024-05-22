

# Insurance claim Data
# Customer Analytics

### Dashboard Link: https://drive.google.com/file/d/1k9Lpc8iBeIfX7q9sU3NLrMUiv7IR9CV7/view?usp=drive_link
## Problem Statement 1

This dashboard provides a visual examination of the clients and the car involved in the collision, highlighting data insights. 
It helps the company understand the age group, marital status and occupation of their most patronized customers as well as their most frequently 
used cars and the reasons for the accident  

Since Total number of accidents/customers is 12000,
(5612 Female drivers) and (6226 Male drivers)
Thus, male drivers has the highest number of accidents


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that DOB, claim dates and accident dates have their details in a single column, so therefore the dates where separated into different columns as Year, Month and Weekday.
- Step 5 : The data type of Gender column was changed to Text from string so as to convert 0 and 1 to male and female.
- Step 6 : The data type of Police notification column was changed to Text from string so as to convert 0 and 1 to Yes and No.
- Step 7 :The data type of Holiday weeks column was changed to Text from string so as to convert 0 and 1 to Yes and No.
- Step 8 :The data type of Drinking and driving column was changed to Text from string so as to convert 0 and 1 to Yes and No.
- Step 9 : The data type of Passenger column was changed to Text from string so as to add the delimiter (passenger) to it.
- Step 10 : The data type of Claim column was changed to Text from string so as to add the delimiter (Claims) to it.
 
- Step 11 : Calculated column was created in which, customers were grouped into various age groups.

for creating new column following DAX expression was written;
       
        Age group = IF([Age]<=19,"Teenager",IF([Age]<=35,"Young Adult",IF([Age]<=50,"Adult",IF([Age]<=65,"Seniors","Elderly"))))
        
Snap of new calculated column,

![age group](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/d0e0232d-2102-484e-9dda-29996b5e04c4)


- Step 12 : New measure was created to find the total number of customers.

Following DAX expression was written for the same,
        
        Total Customer = COUNTA(Sheet2[Vehicle color])
        
A card visual was used to represent count of customers.
![TT customers](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/eece6737-97bf-4ea0-9b1c-2b2ed7ea4cf9)



 - Step 13 : New measure was created to find the total number of female customers and the male customers.
 
 Following DAX expression was written as
 
         Female = CALCULATE([Total Customer],Sheet2[Gender] ="Female")
         Male = CALCULATE([Total Customer],Sheet2[Gender] ="Male")
 A card visual was used to represent this
 
![male sn](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/3a98debf-4693-4898-8cba-d51ca947ca64)

 ![female sn](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/311fd4a2-1f6b-44ac-a00f-dde2a2ef44b7)


 - Step 14: New measure was created to calculate the age of customer at accident date
 
 Following DAX expression was written to find customer age,
 
         age@accident = DATEDIFF(Sheet2[DOB],Sheet2[Accident Date],YEAR)
Snap of new calculated column,
![age](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/45b3b21f-92a4-464b-bc8f-2463657b3f6f)

 
 # Report Snapshot 1 (Power BI DESKTOP): Customer Analytics

  ![customer analytics](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/0a894215-9796-499a-9056-9517a66282fe)

# Insights

This dashboard provides a visual examination of the clients and the car involved in the collision, highlighting data insights. 

The key performance indicator was developed by acquiring the whole quantity of clients that we have in the spreadsheet, as well as the total number of male and female clients.

The first graphic depicts the overall accident by vehicle type using a clustered column chart, with SUVs having the greatest number of accidents.

The second graph shows total accidents by age group, with teens having the largest number of accidents. 

The third graph shows overall accidents by gender, with males having the largest number of accidents. 

The fourth visual depicts Total Accident by Marital Status and Gender, with married men having the greatest number of accidents. 

The fifth visual depicts the trend of total vehicle accidents in each state by age group, with teens in the Northern Territory having the greatest number of accidents.


 # Report Snapshot 2 (Power BI DESKTOP): Incident Analytics
 ## Problem Statement 2

This dashboard displays a visual examination of accidents, highlighting data insights. 
The key performance indicator was developed by gathering the total number of drivers who were under the influence of alcohol and those who were not, as well as the gender of the drunk drivers. 
- Step 15: New measure was created to calculate the number of male druck drivers
 
 Following DAX expression was written to find the number of the male drunck drivers,
 
      Male Drunk Drivers = CALCULATE([Drunk Drivers],Sheet2[Gender]="Male")
         
 - Step 16: New measure was created to calculate the number of female druck drivers
 
 Following DAX expression was written to find the number of the female drunck drivers,
 
       Female Drunk Drivers = CALCULATE([Drunk Drivers],Sheet2[Gender]="Female")
 
 ![incident analytics](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/bf3e1cd3-abaf-487b-ab8f-d9d8e9a4df50)
 
# Insights
 
The first graphic shows the Total Accident by Accident Reason, with speeding being the greatest number. 

The second graph depicts the Total Accident Per Year, with 2015 having the greatest number of accidents. 

The third graph displays the total number of accidents by collision type, with nose to tail having the largest number. 

The fourth graph illustrates the total accident by weather and collision types, with nose-to-tail on wet pavement having the greatest number. 

# Report Snapshot 3 (Power BI DESKTOP): Claim Analytics
 ## Problem Statement 3
This dashboard gives a visual overview of the client's claims and insurance policy, highlighting key insights. 

![claim analytics 1](https://github.com/rmotr-curriculum/freecodecamp-intro-to-pandas/assets/157006710/4616d04b-e595-45c5-88f0-099177bd40ef)

# Insights

The first graph displays the overall accident by month, and July has the largest number of events. 

The second graph depicts the overall accident by weekday, with Tuesday having the largest number of events.

The third graph displays the overall sum repair amount and sum insured amount by claim month, with the largest number of claims in October. 

The fourth graph depicts the total accident by police notification, revealing that 86% of customers did not inform the police. 

The fifth graph depicts the total accident by prior claim, with three being the greatest number of times the customer requested before the repair payment was granted to them.

The sixth graphic shows the total amount insured and the repair cost by vehicle type. 



 






