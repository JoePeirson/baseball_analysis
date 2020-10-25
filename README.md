# baseball_analysis
An analysis of the 2020 mlb season. Looking at inefficiencies and assessing the best pitchers and betters over the course of the season.

# Introduction
I will detail how I collected the data, analysed the data and the conclusions I reached.

# Data Collection
I web scraped the data from the espn play by play commentaries using scrapy.

<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97102294-895db700-16a4-11eb-90c3-ee71ea4c44f7.png"> <img width="500" alt="Screenshot 2020-10-11 at 12 21 18" src="https://user-images.githubusercontent.com/72214007/97102699-03dc0600-16a8-11eb-958a-f029964d0e2c.png">
  <figcaption>Fig.1 - ESPN Webpage  /   Fig.2 - Pandas table, Data after collection</figcaption>
</p>

# Data Analysis
#### Pitcher Fatigue
I looked at how a pitchers output changes with the more pitches he throws in a single game. One would expect, that the more pitches thrown the slower and less productive he'll be. This is the hypothesis I wanted to test. 
I assumed that a pitchers quality would started to fall before 100 pitches, but quality only falls after 110 pitches. This probably shows that pitching strategy is fairly efficient, and pitchers are not being overused. The results were very similar when subsetting for just starting pitchers.
<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97102819-ed827a00-16a8-11eb-86e0-aa2e36569ae6.png">
  <figcaption>Fig.3 - Pitcher fatigue</figcaption>
</p>

#### Pitch Count
The histogram for pitch count is as expected. When the pitch count is in the batters favour, expected bases are higher, and visa versa.
But there is space for some efficiency gains in batting. For example, at a pitch count of 3-1, a batter can get a walk if he gets a ball in one of the next three balls. A batters expected bases at a 3-1 count is 0.719, but when choosing to play safe and avoid attmepting to hit a players expected bases go up to 0.752. Obviously, this strategy has to be limited due to pitchers becoming aware of the strategy.

<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103104-ccbb2400-16aa-11eb-9a9f-d19bd58fdcff.png"> <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103241-7c909180-16ab-11eb-9a3e-85d238288824.png">
  <figcaption>Fig.5 - Pitch count</figcaption>
</p>
