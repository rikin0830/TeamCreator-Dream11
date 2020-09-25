# Project1
# Brief intro
A C++ code which creates the top 5 Dream-11 teams(on the basis of stats) for a cricket match.
All we can do to predict the future is to look at the past.
Even ML models are trained on training data sets(based on past) before using them on testing data sets(to predict the future).

# Requirements:
If you are a fan of cricket and know about Dream 11, with a little bit of C++ knowledge, we can get along very easily in using this code.

# Purpose of this project:
As we both know, there are many dream11 teams possible for a given match.
Using simple math and the rule of minimum 4 players from each team,we can calculate the max number of teams possible is 644688.
Note that we still didnt add constraints on total cost of team(<=100) and mininum and maximum from each category and we haven't even decided                        Captain and Vice-Captain yet.
644688 maybe a big number for us,but for cpp compiler it isn't.
So we are going to use its power and give the playing 22 as input and extract the best 5 teams possible by considering all possible constraints.

# Overview:
I built a database/csv file using previous IPL stats from iplt20.com,
In the case of a player who didn't play previous IPL I manually checked his profile and added an approxiamate analysis based entry to the database.
The csv file consists of 5 columns:
Column1 - Name of player
Column3 - Number of matches played recently 
Column2 - Avg points in those matches
Column4 - Cost of player in Dream11.
Column5 - Role of the player(0 for wk,1 for batsman,2 for all-rounder,3 for bowler)

# How to use the code?
There are 2 aspects to the code that I wrote:
1. Create best 5 teams by giving playing 22(playing 22 is generally revealed after toss)
2. Updating database after the match. (This is important because some player's stats might be bad but he is performing excellent this IPL or vice versa)

So let's talk about Point-1 first:
# How to use the code for generating best 5 teams?
I have taken standard input from INPUT.txt and standard output to OUTPUT.txt ,in sublime text,(If you don't want to use sublime then comment the stext function call in line 398 of the code)
Write "create" in the first line of the input file (INPUT.txt in my case)
Then in the next 22 lines write name of each player(without spaces)
Case-(1):In case the code doesn't find a player mentioned in the input file,
The code doesn't execute and gives the names of players who weren't found.
Case-(2):The code finds all players in the csv file and executes and prints the best 5 teams to OUTPUT.txt

SampleInput for team creation:
create
DavidWarner<br/>
JonnyBairstow
ManishPandey
PriyamGarg
VijayShankar
MitchellMarsh
AbhishekSharma
RashidKhan
BhuvneshwarKumar
SandeepSharma
Natarajan
AaronFinch
ViratKohli
AbdeVilliers
DevduttPadikkal
ShivamDube
WashingtonSundar
UmeshYadav
DaleSteyn
NavdeepSaini
YuzvendraChahal
JoshPhillipe

# How to update the database after the match?
I have taken standard input from INPUT.txt and standard output to OUTPUT.txt ,in sublime text,(If you don't want to use sublime then comment the stext function call in line 398 of the code)
Write "update" in the first line of INPUT.txt,which is followed by 22 lines containing each player and number of points earned by him in that match.
Case-(1): Due to typo,the player might not be found in the csv file. 
In that case the cod edoesn't execute at all and just reports all the players who weren't found in the csv file.
Case-(2): The code finds that all 22 players are available in the csv file,
So it updates "avg points" aka Column 2 and "number of innings" aka Column 3 for each player.

SampleInput(Based on match on 21 sept 2020)for updating database:

update
DavidWarner 11
JonnyBairstow 101
ManishPandey 49
PriyamGarg 17
VijayShankar 27
MitchellMarsh 2
AbhishekSharma 37
RashidKhan 19
BhuvneshwarKumar 4
SandeepSharma 12
Natarajan 32
AaronFinch 38
ViratKohli 34
AbdeVilliers 71
DevduttPadikkal 76 
ShivamDube 63 
WashingtonSundar 4 
UmeshYadav 16
DaleSteyn 27
NavdeepSaini 62
YuzvendraChahal 83 
JoshPhillipe 11
