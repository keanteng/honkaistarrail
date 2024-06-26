# Honkai Star Rail Warp Simulation Study

![Static Badge](https://img.shields.io/badge/license-MIT-blue)

Honkai Star Rail is a gacha game published worldwide by Cognosphere. As a gacha game, it features several banners that allows players to pull for the character and their respective light cone at a relatively low rate (0.6%). With limited resources in game (the amount of jade you can get as you play), and a relatively long time frame to accumulate resources (the time needed for you to save a certain amount of jade), it is often wise to plan your warp and set expectations before warping to ensure resources are being used effectively.

**Table of Contents:**
- [Honkai Star Rail Warp Simulation Study](#honkai-star-rail-warp-simulation-study)
  - [Objectives](#objectives)
  - [Methodology](#methodology)
    - [Probability Mass Function](#probability-mass-function)
    - [Cumulative Mass Function](#cumulative-mass-function)
  - [Getting 5 Star](#getting-5-star)
  - [Setting Expectation](#setting-expectation)
  - [Reference](#reference)

## Objectives

There are several questions that we could perhaps look into:

1. What are the chances of getting a five star with the current warp that we have at hand? Considering any pity or guarantee that will be carried forward as we perform the warp.
2. How many warps that we need to make so that we expect to see a 5-star output?

## Methodology

### Probability Mass Function

$$ PDF(N)=   \left\{
\begin{array}{ll}
      p(1-p)^{n-1}, \qquad N \leq 73 \\
      (1-p)^{73} \times (p + (N-73)d) \prod_{n=1}^{N-74}{(1-p-nd)}, \qquad 74 \leq N \leq 89 \\
\end{array} 
\right.  $$

### Cumulative Mass Function

$$ CDF(N)=   \left\{
\begin{array}{ll}
      1 - (1-p)^N, \qquad N \leq 73 \\
      \sum_{n = 1}^{N}{PDF(N)}, \qquad 74 \leq N \leq 89 \\
      1, \quad N = 90 \\
\end{array} 
\right.  $$

## Getting 5 Star
To get a five star, we will need to have a random number <= pull rate given by the banner. With the given rate, we can then study the distribution and some mathematical properties of successful pull. We can also gauge the average pull that we need to include a five star in it. 

<img src="image/image1.png"  class = "center"/>

## Setting Expectation
To set our expectation before warping, we could perform simulation to estimate our chances when we would like to pull for more copies of a character. This ensures we have enough warp when pulling. The simulation will then take into account of the pity, numbers of warp, any guarantee status, number of character copies we want and estimate the probability based on our condition. This can be done with the following [code](https://github.com/keanteng/honkaistarrail/blob/main/3_basic_simulation.ipynb).

## Reference
- https://github.com/Jose-AE/hsr-warp-calculator
- https://github.com/sr229/gacha-prng
- https://www.youtube.com/watch?v=gZGW190E3ok
