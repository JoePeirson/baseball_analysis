# baseball_analysis
An analysis of the 2020 mlb season. Looking at inefficiencies and assessing the best pitchers and betters over the course of the season.

# Introduction
I will detail how I collected the data, analysed the data and the conclusions I reached.

# Data Collection
I web scraped the data from the espn play by play commentaries using scrapy from the 2020 mlb season minus the world series.

<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97102294-895db700-16a4-11eb-90c3-ee71ea4c44f7.png"> <img width="500" alt="Screenshot 2020-10-11 at 12 21 18" src="https://user-images.githubusercontent.com/72214007/97102699-03dc0600-16a8-11eb-958a-f029964d0e2c.png">
  <figcaption>Fig.1 - ESPN Webpage  /   Fig.2 - Pandas table, Data after collection</figcaption>
</p>

# Data Analysis
### Metrics - Expected Bases
I have created my own metric called expected bases. Expected bases calculates each players return (or output) from facing a pitcher.

For example, if a player scores a single, a walk or any other play that results in him getting to first base, this equals one expected base. If a player scores a double, this equals two and so on. If a player is struck out or caught, or cannot make a play, this will be zero.

I sum up a players total expected bases and divide it by the number of trips to plate, and this gives me and expected bases for each hitter, and expected bases given up for each pitcher.

This is similar to OPS, but combines slugging and OBP a bit more accurutely rather than adding them together.

Expected bases will be how I measure the success of various teams, players and strategies

##### Expected Bases = (1B + 2B * 2 + 3B * 3 + HR * 4)/Plate Appearances

### Pitcher Fatigue
I looked at how a pitchers output changes with the more pitches he throws in a single game. One would expect, that the more pitches thrown the slower and less productive he'll be. This is the hypothesis I wanted to test. 
I assumed that a pitchers quality would started to fall before 100 pitches, but quality only falls after 110 pitches. This probably shows that pitching strategy is fairly efficient, and pitchers are not being overused. The results were very similar when subsetting for just starting pitchers.
<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97102819-ed827a00-16a8-11eb-86e0-aa2e36569ae6.png">
  <figcaption>Fig.3 - Pitcher fatigue</figcaption>
</p>

### Pitch Count
The histogram for pitch count is as expected. When the pitch count is in the batters favour, expected bases are higher, and visa versa.

But there is space for some efficiency gains in batting. For example, at a pitch count of 3-1, a batter can get a walk if he gets a ball in one of the next three balls. A batters expected bases at a 3-1 count is 0.719, but when choosing to play safe and avoid attmepting to hit a players expected bases go up to 0.752. Obviously, this strategy has to be limited due to pitchers becoming aware of the strategy.

<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103104-ccbb2400-16aa-11eb-9a9f-d19bd58fdcff.png"> <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103241-7c909180-16ab-11eb-9a3e-85d238288824.png">
  <figcaption>Fig.4 - Pitch count  /   Fig.5 - Inefficiency</figcaption>
</p>

### Pitch Velocity
When pitching 97mph and faster the efficiency of a pitcher starts to improves rapidly when measured against expected bases. This holds true when subsetting just for fast balls thrown.

<p float="left">
  <img width="400" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103526-4d7b1f80-16ad-11eb-808c-47539de44cd9.png"> 
  <figcaption>Fig.6 - Pitch Velocity</figcaption>
</p>

### Pitch Variety Strategy
Pitchers who throw five different pitches regulary (each pitch more than 15% of pitches) don't seem to be too successful. The data shows that it is best to throw between 2-3 pitch types and throw them regulary.

<p float="left">
  <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103874-a51a8a80-16af-11eb-8036-3fc2f3113469.png"> <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103892-c1b6c280-16af-11eb-9895-fe7a0fe10fd2.png"> <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97103903-d7c48300-16af-11eb-8906-b662193cc930.png"> 
  <figcaption>Fig.7 - Pitch Variety Efficiency</figcaption>
</p>
When a pitcher has three main pitches, all of which he throws over 25% of the time, the majority of his pitch types are much more successful versus the average.
When a pitcher has five main pitches, all of which he throws over 15% of the time, the majority of his pitch types are much less successful versus the average.

<p float="left">
  <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97104127-b5336980-16b1-11eb-9432-82356ce0ec4d.png"> 
  <figcaption>Fig.8 - Pitch success with good and bad variety</figcaption>
</p>

### Best Pitchers and Batters


<p float="left">
  <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97104390-d4cb9180-16b3-11eb-9c2e-e1527daecf83.png"> <img width="300" alt="Screenshot 2020-10-11 at 12 11 59" src="https://user-images.githubusercontent.com/72214007/97104405-ec0a7f00-16b3-11eb-80fe-e92395be8686.png"> 
  <figcaption>Fig.9 - Best pitchers/batters (count is every plate appearance)</figcaption>
</p>
