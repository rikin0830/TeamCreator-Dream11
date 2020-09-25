# Project1
# Brief intro
A C++ code which creates the top 5 Dream-11 teams(on the basis of stats) for a cricket match.<br/>
All we can do to predict the future is to look at the past.<br/>
Even ML models are trained on training data sets(based on past) before using them on testing data sets(to predict the future).<br/>

# Requirements:
If you are a fan of cricket and know about Dream 11, with a little bit of C++ knowledge, we can get along very easily in using this code.<br/>

# Purpose of this project:
As we both know, there are many dream11 teams possible for a given match.<br/>
Using simple math and the rule of minimum 4 players from each team,we can calculate the max number of teams possible is 644688.<br/>
Note that we still didnt add constraints on total cost of team(<=100) and mininum and maximum from each category and we haven't even decided                        Captain and Vice-Captain yet.<br/>
644688 maybe a big number for us,but for cpp compiler it isn't.<br/>
So we are going to use its power and give the playing 22 as input and extract the best 5 teams possible by considering all possible constraints.<br/>

# Overview:
I built a database/csv file using previous IPL stats from iplt20.com,<br/>
In the case of a player who didn't play previous IPL I manually checked his profile and added an approxiamate analysis based entry to the database.<br/>
The csv file consists of 5 columns:<br/>
Column1 - Name of player<br/>
Column3 - Number of matches played recently <br/>
Column2 - Avg points in those matches<br/>
Column4 - Cost of player in Dream11.<br/>
Column5 - Role of the player(0 for wk,1 for batsman,2 for all-rounder,3 for bowler)<br/>

# How to use the code?
There are 2 aspects to the code that I wrote:<br/>
1. Create best 5 teams by giving playing 22(playing 22 is generally revealed after toss)<br/>
2. Updating database after the match. (This is important because some player's stats might be bad but he is performing excellent this IPL or vice versa)<br/>

So let's talk about Point-1 first:<br/>
# How to use the code for generating best 5 teams?
I have taken standard input from INPUT.txt and standard output to OUTPUT.txt ,in sublime text,(If you don't want to use sublime then comment the stext function call in line 398 of the code)<br/>
Write "create" in the first line of the input file (INPUT.txt in my case)<br/>
Then in the next 22 lines write name of each player(without spaces)<br/>
Case-(1):In case the code doesn't find a player mentioned in the input file,<br/>
The code doesn't execute and gives the names of players who weren't found.<br/>
Case-(2):The code finds all players in the csv file and executes and prints the best 5 teams to OUTPUT.txt<br/>

SampleInput -1 :<br/>
----------------------
create<br/>
DavidWarner<br/>
JonnyBairstow<br/>
ManishPandey<br/>
PriyamGarg<br/>
VijayShankar<br/>
MitchellMarsh<br/>
AbhishekSharma<br/>
RashidKhan<br/>
BhuvneshwarKumar<br/>
SandeepSharma<br/>
Natarajan<br/>
AaronFinch<br/>
ViratKohli<br/>
AbdeVilliers<br/>
DevduttPadikkal<br/>
ShivamDube<br/>
WashingtonSundar<br/>
UmeshYadav<br/>
DaleSteyn<br/>
NavdeepSaini<br/>
YuzvendraChahal<br/>
JoshPhillipe<br/>

Sample Output -1: </br>
--------------------------------------------

The best 5 teams are::</br>
</br>
Estimated points for team-1 = 566.82</br>
DavidWarner(C) </br>
JonnyBairstow </br>
ManishPandey </br>
RashidKhan </br>
AaronFinch </br>
AbdeVilliers </br>
DevduttPadikkal(VC)</br> 
ShivamDube </br>
DaleSteyn </br>
YuzvendraChahal</br> 
JoshPhillipe </br>
-------------------------------------</br>
Estimated points for team-2 = 566.22</br>
DavidWarner(C) </br>
JonnyBairstow </br>
ManishPandey </br>
RashidKhan </br>
AaronFinch </br>
AbdeVilliers </br>
DevduttPadikkal(VC)</br> 
WashingtonSundar </br>
DaleSteyn </br>
YuzvendraChahal</br> 
JoshPhillipe </br>
-------------------------------------</br>
Estimated points for team-3 = 565.607</br>
DavidWarner(C) </br>
JonnyBairstow </br>
ManishPandey </br>
SandeepSharma </br>
AaronFinch </br>
ViratKohli </br>
AbdeVilliers </br>
DevduttPadikkal(VC)</br> 
ShivamDube </br>
DaleSteyn </br>
YuzvendraChahal</br> 
-------------------------------------</br>
Estimated points for team-4 = 565.007</br>
DavidWarner(C) </br>
JonnyBairstow </br>
ManishPandey </br>
SandeepSharma </br>
AaronFinch </br>
ViratKohli </br>
AbdeVilliers </br>
DevduttPadikkal(VC)</br> 
WashingtonSundar </br>
DaleSteyn </br>
YuzvendraChahal</br> 
-------------------------------------</br>
Estimated points for team-5 = 563.229</br>
DavidWarner(C) </br>
JonnyBairstow </br>
ManishPandey </br>
PriyamGarg </br>
RashidKhan </br>
AaronFinch </br>
AbdeVilliers </br>
DevduttPadikkal(VC)</br> 
ShivamDube </br>
DaleSteyn </br>
YuzvendraChahal</br> 
-------------------------------------</br>

SampleInput -2 :<br/>
----------------------
create<br/>
DavidWarner<br/>
JonnyBairstow<br/>
ManishPandey<br/>
PriyamGarg<br/>
VijayShankar<br/>
MitchellMarsh<br/>
AbhishekSharma<br/>
RashidKhan<br/>
BhuvneshwarKumar<br/>
SandeepSma<br/>
Natarajan<br/>
AaronFinch<br/>
Viratohli<br/>
AbdeVillier<br/>
DevduttPadikkal<br/>
ShivamDube<br/>
WashingtonSundar<br/>
UmeshYadav<br/>
DaleSteyn<br/>
NavdeepSaini<br/>
YuzvendraChahal<br/>
JoshPhillipe<br/>

SampleOutput-2 : <br/>
-----------------------
The following player/players were not found in the csv:<br/>
SandeepSma<br/>
Viratohli<br/>
AbdeVillier<br/>

Note that now I have deliberately introduced some typos in the sample input.<br/>
But the code finds them out.Even in the next part(database update) the code first checks whether all players mentioned are in the csv or not and gives an error like this(SampleOutput-2) if any player is not available in the csv.<br/>
# How to update the database after the match?
I have taken standard input from INPUT.txt and standard output to OUTPUT.txt ,in sublime text,(If you don't want to use sublime then comment the stext function call in line 398 of the code)<br/>
Write "update" in the first line of INPUT.txt,which is followed by 22 lines containing each player and number of points earned by him in that match.<br/>
Case-(1): Due to typo,the player might not be found in the csv file. <br/>
In that case the cod edoesn't execute at all and just reports all the players who weren't found in the csv file.<br/>
Case-(2): The code finds that all 22 players are available in the csv file,<br/>
So it updates "avg points" aka Column 2 and "number of innings" aka Column 3 for each player.<br/>

SampleInput(Based on match on 21 sept 2020)for updating database:<br/>

update<br/>
DavidWarner 11<br/>
JonnyBairstow 101<br/>
ManishPandey 49<br/>
PriyamGarg 17<br/>
VijayShankar 27<br/>
MitchellMarsh 2<br/>
AbhishekSharma 37<br/>
RashidKhan 19<br/>
BhuvneshwarKumar 4<br/>
SandeepSharma 12<br/>
Natarajan 32<br/>
AaronFinch 38<br/>
ViratKohli 34<br/>
AbdeVilliers 71<br/>
DevduttPadikkal 76 <br/>
ShivamDube 63 <br/>
WashingtonSundar 4 <br/>
UmeshYadav 16<br/>
DaleSteyn 27<br/>
NavdeepSaini 62<br/>
YuzvendraChahal 83 <br/>
JoshPhillipe 11<br/>

SampleOutput:<br/>
Update Complete <br/>
