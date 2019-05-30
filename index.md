# Factors Affecting High Performance Computing – Case Study and Result Comparison Using a Self Created Benchmark Tool
I had recently purchased the iPhone X and was showing it off to my friends. Sumeet and Bander told me that it wasn’t as great as I made it sound and that the S9 plus and the OnePlus 6T were better phones.
Our argument was based purely on the performance of the phones because we believed that there was no basis to compare the designs as each had their pros and cons.
We were thinking about how we could compare the phones when we came across a ‘Benchmarking’ paper in our High-Performance Computing class. Upon digging deeper into it, we found out there were many tools that could be used for the same.
After careful consideration (of user ratings) we decided on using AnTuTu, Geekbench and PerformanceTest Mobile.
•	GeekBench V4.3.2 (Android) vs GeekBench 4 (iOS)
•	AnTuTu V7.1.9 (Android) vs AnTuTu 7.2.1 (iOS)
•	PerformanceTest Mobile V1.2.0 (Android, iOS)
We observed various results, some weird, and some that gave us insight into why maybe a certain phone was performing better than the other. We didn’t stop here. Instead we moved on to researching why certain anomalies were present in the results, and we found some striking things.
Screenshots of Benchmarks:

The GeekBench scores showed that the iPhone performed considerably better than the other two phones.

![GeekBench Scores](/images/1.jpg)
![GeekBench Graph](/images/Graph1.jpg)
![GeekBench Graph2](/images/Graph3.jpg)

We moved forward and ran the AnTuTu scores. SURPRISE, OnePlus 6T was waaaaaaay ahead in terms of its score!

![AnTuTu Scores](/images/2.jpg)
![AnTuTu Graph](/images/Graph3.jpg)

Also, while we were running these scores on the phones, we thought about something else. The calculations were taking a lot of time, so we decided to run the same thing on my Laptop. I was assuming that my laptop’s score would destroy the scores of all the phones, but to our amazement, it did not:

![Phones VS Laptop](/images/3.jpg)
![PvL Graph](/images/Graph4.jpg)
![PvL Graph2](/images/Graph5.jpg)

GameBench was also used to measure game performance (frames per second) while playing PUBG. There wasn’t a considerable difference in the performance (thus we’re not showing the screenshots) with all 3 phones running the game smoothly at around 30 fps. Initially we thought this was problematic but turns out games like PUBG have fps locked at 30 fps.

![GameBench iPhone](/images/4.jpg)

We measured the power consumption score (lower is better) while playing games as well (in terms of how many hours the phone could run a game compared to its battery capacity). We ran my favorite PUBG to test this out. The iPhone gave us a result of 19.82 mAh/min of game (2716mAh battery, 137 minutes from 100%-0% battery), whereas the S9+ gave us a result of 19.77 mAh/min of game (3500mAh battery, 177 minutes from 100%-0% battery) and the OnePlus6T gave us a result of 21.27 mAh/min of game (3700mAh battery, 174 minutes from 100%-0% battery). Upon discussion in class, we realized that playing a game isn’t a fair way to test out the score because rendered frames will not always be constant, so we did the test again with a video. I used a personal video, set it to repeat, and played it with the default media players on each phone. 

![Batt Graph](/images/Graph6.jpg)
![Batt Graph](/images/Graph7.jpg)

We saw different results this time, the iPhone gave us a result of 12.93 mAh/min of video (2716mAh battery, 311 minutes from 100%-0% battery), whereas the S9+ gave us a result of 16.21 mAh/min of video (3500mAh battery, 216 minutes from 100%-0% battery) and the OnePlus6T gave us a result of 16.44 mAh/min of video (3700mAh battery, 225 minutes from 100%-0% battery). Frame rendering did affect our results.
We continued digging deeper and found that it isn’t just the processor, or the RAM, that the Benchmark scores depend on. There are also multiple other factors, like chip size, heat dissipation, power consumption, programming language used, etc. More on them later, but we went deep into what were the differences, be it in terms of hardware, or in terms of software. We also came across a tactic that was used by a certain company to boost its scores (look at the surprising part above). Basically, they boost their processor performance once they detect that that benchmark test was being run.
The question was that why was it that even though all three phones had comparable processors and the iPhone had the least amount of RAM, the iPhone still outperformed the other 2 phones. We found out the following factors:
1.	The iPhone processors are almost 2x the size of non-apple chips. More silicon is used to create these which, even though it increases the price, also speeds up computations as more cache can be present due to increased size.
2.	The iPhone read/write speed was found to be the highest using PassMark PerformanceTest. 
1213/536 for the iPhone vs 798/208 for the S9+ vs 735/203 for the OnePlus 6T. The iPhone has NVMe based storage solution with custom controllers.
3.	Apple creates custom components for its devices whereas the components created for Android devices are created for a large scale of manufacturers.
4.	The memory management in iPhone is better in one aspect. The ARC, or automatic reference counting, in iPhone has the advantage over the GC, or Garbage Collector, in android, that the Garbage Collector pauses applications to clean up memory whereas ARC decides whether something remains in the memory or not based on its referencing.
5.	Apple software is optimized for iPhones whereas Android softwares are created for a variety of manufacturer phones.
Now, we had a very big collection of results, and we wanted to see how these were calculated in the first place.
The simplest thing we came across was doing float and integer calculations multiple times and calculating the times required for the same. Some did string sorting while some did data compression. An advanced thing to do was to render images and 3D mazes or maybe solve complex vectors.
We wanted to begin with the simple thing first and started with integer calculations, then moved to float, and then just for the fun of it, we decided to move onto Hashing algorithms.
Our tool creates SHA-1 and MD5 hashes of a string ‘The big brown fox jumps over lalalala’ and calculates the time taken to do so. This is done 20,000 times so as to obtain comprehensible results. We also added the brute force PIN cracking method which is in the worst case can run from 00,000 to 99,999. The downside to this was that we were only able to create it for Android phones because none of us had any knowledge of iOS app development.

![Our Tool](/images/5.jpg)

We created the tool in such a way so as to present a score, lower is better.
These were our results when running our benchmark tool on the S9+ and OnePlus 6T. As you can see that even though the scoring systems differ, the S9+ performs better than the OnePlus 6T. The GeekBench scores are 1.5X better for the S9+, whereas our score is 2X better. We feel that if we can add more constraints to the score, we can make the score even better.
This project led us to discover a lot of things with respect to architectures, memory management, optimizations, etc. We wish to move forward with it and improve the benchmark tool, adding more single core computations, and maybe applying methods that could help us determine the power of the GPUs in the devices.
