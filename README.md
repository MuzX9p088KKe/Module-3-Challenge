# Election Analysis

## Overview of Election Audit

We were tasked to write a Python script to audit election results in a congressional district in Colorado. While this task is usually done in Excel, a Python script could be more versatile and be used for other congressional or senatorial districts.

The election results are transcribed from mail-in ballots, punch cards, and electronic direct recording into a csv file.

The scope of this audit is to use that csv file which contains all the unique vote entries for this election and to produce an easy-to-read output. After running the Python script, the following information should be delivered:


* Total number of votes cast
* The voter turnout for each county
* The percentage of votes from each county out of the total count
* The county with the highest turnout
* A complete list of candidates who received votes
* Total number of votes each candidate received
* Percentage of votes each candidate won
* The winner of the election based on popular vote

In addition to the script itself, we were also required to provide a written analysis of the election audit including all the results and an overview of our methods. This was required in order to help clarify our methods for the election commission and demonstrate what could be done with this tool in the future and with the data we presented.



## Election Audit Results

The very first step of the audit was to import the data to be used in the script and then to create an output text file to be populated with the results.

![Import_Export_PyPoll](https://user-images.githubusercontent.com/76575162/118425241-64578280-b68e-11eb-9265-edf8ed3f9601.png)

Next we established variables to hold key values before running through the data and turning it into an easily usable list of dictionaries. We then prompted the script to open the database.

![Variables_PyPoll](https://user-images.githubusercontent.com/76575162/118425301-85b86e80-b68e-11eb-8830-da8cd958cf7a.png)
![Openfile_PyPoll](https://user-images.githubusercontent.com/76575162/118425352-a7b1f100-b68e-11eb-9d89-bba0aae98824.png)


This was the ground work to get us started on the audit and find the following information


* ### How many votes were cast in this congressional election?

	In order to count all the votes, a simple "for" loop was created to run through all the data in the csv file and to add a vote to the total_votes variable for each new row in the file.
	
![total_vote_count](https://user-images.githubusercontent.com/76575162/118425438-d4660880-b68e-11eb-99f5-fca72dc33620.png)

This resulted in a total vote count of 369,711 which we output to the text file by printing an f-string as follows:

	
![write_total_vote_count](https://user-images.githubusercontent.com/76575162/118425538-fe1f2f80-b68e-11eb-947c-eba3d44247c3.png)




* ### Breakdown of the number of votes and the percentage of total votes for each county in the precinct.

	Still in the same "for" loop, we had the script check if the county associated with each individual vote was already present in the list or add it to the list if it was not before initializing the county's vote tally at 0.
	Next, each occurrence of the county in the data would add one vote to its vote tally. 
	
![county_votes_tally](https://user-images.githubusercontent.com/76575162/118425597-1ee78500-b68f-11eb-8243-f590d19728bb.png)

	
In order to output this information to a text file along with calculating each county's percentage share of the total vote count, we used the following f-string: 

![write_county_votes](https://user-images.githubusercontent.com/76575162/118425929-d7adc400-b68f-11eb-872b-607bb55fd882.png)

	  
This showed that the results for each county were:

		- Jefferson: 10.5% (38,855)
		- Denver: 82.8% (306,055)
		- Arapahoe: 6.7% (24,801)

* ### Which county had the largest number of votes?

	As seen in the above breakdown, Denver was the county with the most votes with a total of 306,055 or 82.8% of the total votes. 
	
	In order to automatically determine the largest county turnout we used a "for" loop to retrieve the county votes data and calculating the  before adding an "if" statement to determine which county had the highest turnout. We then used an f-string to output it to the text file.
	
	![write_county_turnout](https://user-images.githubusercontent.com/76575162/118425986-fe6bfa80-b68f-11eb-9daa-789152648626.png)


* ### Breakdown of the number of votes and the percentage of the total votes each candidate received.

	After focusing on counties, we moved on to the individual candidates and the votes they received. Just like for the counties, we had the script check if the candidate associated with each individual vote was already present in the list or add it to the list if it was not before initializing the candidate's vote tally at 0.
	Next, each occurrence of the candidate in the data would add one vote to its vote tally.
	
	![candidate_vote_count](https://user-images.githubusercontent.com/76575162/118426082-24919a80-b690-11eb-8b8b-4e470c662117.png)

	
	In order to output this information to a text file along with calculating each candidate's percentage share of the total vote count, we used the following f-string:
	
	![candidate_summary](https://user-images.githubusercontent.com/76575162/118426132-468b1d00-b690-11eb-9300-91db78972190.png)

	
	This showed that the results for each candidate were:
	- Charles Casper Stockham: 23.0% (85,213)
	- Diana DeGette: 73.8% (272,892)
	- Raymon Anthony Doane: 3.1% (11,606)   

* ### Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

	As seen in the above breakdown, Diana DeGette was the winning candidate with a total of 272,892 votes or 73.8% of the total votes. 

	In order to automatically determine the winning candidate we used a "for" loop to retrieve the county votes data and calculating the  before adding an "if" statement to determine which county had the highest turnout. We then used an f-string to output it to the text file.
	
	![winning_candidate_summary](https://user-images.githubusercontent.com/76575162/118426254-82be7d80-b690-11eb-9087-75fcb9259722.png)




## Election Audit Summary


As demonstrated while going over our method, this script is pretty easy to use and even creates a text file to output a summary of the data from our analysis. The file in question can be found [HERE](https://github.com/MuzX9p088KKe/Module-3-Challenge/blob/main/Analysis/election_results.txt) or in the "Analysis" folder and is named election_results

It would be extremely easy to re-write this script by modifying the file it will open in order to analyze the vote data of another district. All that would be needed is to create a folder with a similar structure containing the script along with an "Analysis" subfolder and a "Resources" subfolder containing the dataset of interest.

Another fairly easy change would be to rewrite the way the script produces the output and turn it into an announcement such as "Candidate X has won this election by a total of Y votes out of a total of Z votes across the district" or something of the sort.

If the data as other things to track on top of the county or candidate name, say hypothetically a specific polling location, it would also be possible to keep count of how many votes came out of that location, how many votes for each candidates came out of it and so on.

This script is pretty straightforward and easy to modify and use. Its versatility would make it a great asset for any similar election audit.

