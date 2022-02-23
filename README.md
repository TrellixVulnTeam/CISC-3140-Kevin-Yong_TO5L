# CISC-3140-Kevin-Yong
CISC3140 Kevin Yong for Spring 2022 Semester

AUTHOR: Kevin Yong
Description: Lab 1


Step 1:git submodule add -f https://gist.github.com/d66a59b6db4e59c16efd4c42ad411f8e.git data_lab1

Copies Professor Chuang's repo to my local machine. This repo contains a file called data.csv

Description of helloworld.awk:
Prints Total, car_ID, year, make, model, ranking, on the first row.
Copies car_ID, year, make, model from data.csv to report.csv
The data under Ranking will NOT be filled with the script.
Creates a column called total that adds the results from column 8 to the last column of the file.
The program will sort report.csv based on the total, in descending order.

Known bugs with awk script:
Data from data.csv that contain a space is read into two different columns.
For example, if Car-make is "Hello world", "Hello" is read into column n and "world" is read into column n+1.
Temp fix: The model name will be replaced with "Model". Now, ranking will sort properly except for the column that
contains the Make: Civic coupe (the only string that contains an empty space inbetween).

-----------------------------------
After running the script with: 
awk -f helloworld.awk data.csv  > report.csv

To sort the rankings by numeric order:
paste -d' ' <(cut -d' ' -f1-5 report.csv )  <(cut -d' ' -f6- report.csv |sort -n) >sortedreport.csv

Typing this in the terminal will cut out columns 1 to 5 of report.csv and print it.
Then it will take out column 6 (the Ranking column) of report.csv and sort it in numerical order then
print to sortedreport.csv
This way, the sorting of the ranking will NOT undo the reverse numeric sorting of the Total.

Known bugs: The string "Ranking" would get sorted along the with numbers and would not remain on top.
Temp fix: Attached "--Ranking" in the same column as Model.
-----------------------

Now, to create a new script that will search for unique name (by adding total string value we can get an unique ID)
For each make with a unique name, print top three. Total is already sorted, so the program just needs to
print the first three cars that matched the name. (Using a counter=0, when counter=3 move on next unique name. Use next;)

 touch topCarMakes.awk

Looks at column 1. Takes carmake and set as string(To use for comparison later)
Prints ranking, car_id, year, car make, car model, total score to new File.
Counter++; // This counter will move on to next car make on 3.

Now "skip" all car makes with the unique ID and restart until there is no more data in the .CSV.


