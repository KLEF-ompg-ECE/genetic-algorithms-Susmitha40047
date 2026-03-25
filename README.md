# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** G.Sri Susmitha  
**Student ID    :** 2310040047 
**Date Submitted:** 25-03-2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The fitness() function returns the total value of selected items in the knapsack if the total weight is within the capacity. If the solution exceeds the weight limit, it returns 0 as a penalty. This ensures that invalid (overweight) solutions are not selected and encourages feasible solutions.

```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
The tournament_select() function randomly selects a few individuals from the population and chooses the one with the highest fitness among them. Higher-fitness individuals are more likely to be selected because they have a better chance of winning the tournament. This helps in promoting better solutions in future generations.

```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
This line copies the best chromosome from the current generation into the next generation. This process is called elitism. It ensures that the best solution found so far is not lost during crossover or mutation and helps the algorithm converge more reliably.


```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50 |
| Best value at generation 1 |60 |
| Final best value | 77|
| Total weight of best solution (kg) |14.4 |
| Is solution valid (Yes / No) |Yes |

**Copy the printed packing list here:**
```
+ Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The graph shows a sharp increase in fitness in the early generations, indicating that the algorithm quickly finds good solutions. After around 10–15 generations, the curve flattens, showing that improvements slow down as the algorithm converges. The best value stabilizes at 77, indicating that an optimal or near-optimal solution has been reached.

```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-------------------|-------------|--------|----------------|
| 0.01         |   75              | 14.9        | Yes    | Rapid rise then early plateau|
| 0.05         |   77              | 14.4        | Yes    | Smooth rise then stable convergence|
| 0.30         |   78              | 14.1        | Yes    | Fluctuating then sharp improvement |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
When the mutation rate is very low (0.01), the algorithm quickly converges but gets stuck early, leading to a lower final value. With a moderate mutation rate (0.05), the algorithm shows smooth and stable improvement, reaching a good solution efficiently. When the mutation rate is high (0.30), the search becomes more exploratory and fluctuates more, but it is able to find a better solution. This shows that a balance between exploration and stability is important.


```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate of 0.30 gave the best result with a value of 78. This is because the higher mutation rate increases diversity in the population, allowing the algorithm to explore more possible solutions and escape local optima. However, it also introduces instability compared to moderate mutation rates


```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |77 |The algorithm converges quickly and stabilizes at a good solution |
| 2 — Mutation rate | mutation_rate = ___ |78 |Higher mutation improves exploration and can find better solutions |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
From these experiments, I learned that mutation rate is a critical parameter in Genetic Algorithms. A low mutation rate reduces diversity and can cause the algorithm to get stuck in local optima. A moderate mutation rate provides a good balance between exploration and exploitation, leading to stable performance. A higher mutation rate increases exploration and can sometimes find better solutions, but may also introduce instability. Therefore, choosing the right mutation rate is essential for achieving optimal results.


```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
