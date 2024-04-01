
# Project Title

Final project for the Building AI course - Performance Training Optimizator

## Summary

The idea of this project is to identify what would be the most effective training routine that would improve an athlete´s performance for a specific course/track.
We will use the following data: hours of resistance training per week, hours of strenght training per week, hours of rest per week, carbohydrate ingestion per week (g/kg) and protein ingestion per week (g/kg).
We will analyse the data and identify which factors generate the most effective performance improvement in milliseconds.


## Background

Understanding how to improve an athlete´s performance is a complex thing. It doesn´t matter if it´s a professional athlete or an amateur athlete, there are many variations of trainings, diets, and everybody is just trying to perform at the best level possible. In this scenario, it´s common to make mistakes that end up reducing performance, especially if not supported by professionals. How to balance the amount and type of training? How to balance rest? How to balance the diet? Even if each organism reacts differently, would there be a general guideline that could be followed and which is backed up with data? Would it be possible to identify what factors to prioritize to reach optimum performance and what results to expect?
As an amateur athlete, I have many times trained myself not knowing exactly what to expect. Hopefully this project will be an opportunity to understand better what training and performance success look like.


## How is it used?

The process is somehow simple, the idea is getting weekly data from a single athlete or even several athletes for a specific course/track, and using linear regression to identify how each variable/input affects the overall performance. In the end of the process we should have an idea of what inputs (which are training variables) to prioritize for reaching the best performance, and even projecting future performance.
The users could be coaches, athletes and general personnel involved with the training, and the sport should have a time-trial success criteria, like in swimming, cycling, running - or any other sport where the athete should finish in the lowest time possible. The analysis is meant for a specific course/track, so the data should be collected always for the same circuit. If there are different circuits, then the data should be collected for each circuit, because each circuit may benefit from a different type of training. In this study we are also trying to simplify the analysis, so other variables like temperature, humidity, wind speed, etc are not being taken into consideration at this time, but could be added to the model in the future.

As mentioned previsouly, we will consider the 5 inputs/variables below:
- hours of resistance training per week,
- hours of strenght training per week,
- hours of rest per week,
- carbohydrate ingestion per week (g/kg),
- protein ingestion per week (g/kg).

We will then add the results, which will be the observed Performance Improvement in milliseconds. The Performance Improvement is how much an athlete managed to improve his/her time after that specific training (inputs).

Finally we will use linear regression to understand what inputs/variables impacted the Performance the most for that specific track/circuit (obtain the model´s coefficients).

```
# input values x: hours of resistance training per week,hours of strenght training per week,hours of rest per week,carbohydrate ingestion per week (g/kg),protein ingestion per week (g/kg).
# input values y: observed performance gain in milliseconds
	
import numpy as np

x = np.array([
             [60, 24, 84, 3.5, 2.2], 
             [54, 30, 84, 3.4, 2.1], 
             [54, 18, 96, 3.3, 2], 
             [48, 18, 102, 2.8, 2], 
             [48, 24, 96, 3, 1.8]
            ])   
y = np.array([1000, 1100, 1200, 1150, 950])

c = np.linalg.lstsq(x, y)[0]
print(c)
print(x @ c)
```


## Data sources and AI methods

The data used in this study was randomly generated. The data to feed the model should be collected by the athlete or someone in the athlete´s team.
As mentioned previously, we are executing a linear regression to identify the coefficients and their impact on Performance.

In this case, and with this training data, the calculated coefficients were:

- hours of resistance training per week: -84,27
- hours of strenght training per week: -27,86
- hours of rest per week: 0,34
- carbohydrate ingestion per week (g/kg): 1115,38
- protein ingestion per week (g/kg): 1269,23

Interestingly, it basically suggests that the diet and rest are impacting performance more than the training exercises (still we know that the exercises should be kept at least at the minimum level shown on the sample)!
So Protein ingestion, Carbohydrate ingestion and Rest, in this order, are showing to affect the Performance more, for this specific circuit. Also, it is more important to execute Strenght training than Resistance training.

## Challenges

The first challenge I can think of is that this model is based on quantitative data and not qualitative data. Meaning, we know that there has been a certain number of hours of training, but we are not able to identify the intensity of the exercises. Two different athletes can execute both 18 hours of strenght training per week, but have performed those at different strenght intensities. Maybe in the future it could be added to the model (hours if intensity 1-3, hours of intensity 3-5, etc). Also, other factors are not being taken in consideration to not overcomplicate the model (variables like temperature, humidity, wind speed, etc). I am also curious to see how the model will perform with real data, there might be overfitting, or maybe the data will not take us to a clear conclusion? I also believe cases with high ingestion of carbohydrate and protein and with low performance gains should also help to reduce the weight of those coefficients seen on the sample´s linear regression.

## What next?

I believe first we could check how the model behaves with real data and then we could think of improvements and resources / what´s needed to implement those improvements.


## Acknowledgments

I would like to thank the University of Helsinki and everybody involved for making this training available, it was very interesting and answered a lot of questions I had about how the AI algorithms work under the hood. I was actually very surprised to see that many of those concepts I had seen in the past when I was studying to graduate as an electric engineer, and I could never imagine that they were applied in AI! It was also fun to remember many of those concepts!
- The image used in this work was created with Microsoft Copilot/Chat-GPT.
![image](/Triathlon3.jpg)
