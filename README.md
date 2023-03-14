# Stock-Indexing-Optimization


### Problem Statement

Create an index fund with "m" stocks to track the NASDAQ-100 index with "n" stocks, where m << n.

Constructing an index fund that tracks a specific broad market index could be done by simply purchasing all n stocks in the index, with the same weights as in the index. However, this approach is impractical (many small positions) and expensive (rebalancing costs may frequently be incurred, price response to trading). An index fund with m stocks, where m is substantially smaller than the size of the target population, n, seems desirable.

### Approach

#### Method (i):  Solving one Integer Programming and one Linear Programming problem
We created the index fund in multiple steps. First, we formulated an integer program that picked exactly m out of n stocks for our portfolio. This integer program took as input a ‘similarity matrix’, which we call 𝜌. The individual elements of this matrix, 𝜌ij, represent daily return correlation between stock i and j.  Next, we solved a linear program to decide how many of each chosen stock to buy for your portfolio and finally evaluate how well our index fund does as compared to the NASDAQ-100 index, out of sample. 


#### Method (ii):  Solving one Mixed Integer Programming problem
This approach involved creating the index fund in a single shot by solving a mixed integer programming problem. We re-formulated the weight selection problem to be an MIP that constraints non-zero weights to be an integer. This problem solves for both stock selection and weight allocation in a single attempt.  

### Tracking error comparison

![image](https://user-images.githubusercontent.com/26767610/225147915-ecec4256-287d-4c0b-9881-e9f41eb3508b.png)

The main difference between the two approaches is that the first approach calculates stock selection and the weights separately, while the second approach ignores the stock picking aspect and calculates the weights and stocks used in one step. Both approaches have the same general trend with additional stocks decreasing the tracking error, but at the 60-stock mark the first approach diverges significantly.
