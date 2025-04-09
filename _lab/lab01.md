---
layout: lab  
num: lab01  
ready: true  
desc: "LeetCode 3-Sum + Empirical Runtime Analysis"  
assigned: 2025-03-31 09:00:00.00-08:00  
due: 2025-04-11 23:59:00.00-08:00  
---

## Learning Goals  
- Set up and use LeetCode for algorithmic practice  
- Implement a brute-force solution to the 3-Sum problem  
- Perform empirical analysis to measure and model program runtime  
- Visualize and interpret runtime data using linear and log-log plots  

## Collaboration Policy  
This lab is an **individual assignment**. You must:  
- Solve the LeetCode 3-Sum problem and perform the empirical analysis yourself, without assistance from AI tools or others.  
- However, you **may use AI tools or online resources** to assist with writing code for timing measurements, file I/O, and plotting (but not for the 3-Sum solution itself).  
- Cite any external resources (e.g., libraries, tutorials) used for these auxiliary tasks in your report.  

## Part 1: Getting Started with LeetCode  
To build algorithmic problem-solving skills, 10% of your final grade will come from completing a curated set of LeetCode problems over the next 9 weeks. These problems align with course topics and will help prepare you for exams, where some questions will be drawn from this set. If you haven't used github before, we recommend completing the optional (lab00) first before starting this assignment.

### Steps to Set Up:  
1. **Create an Account**:  
   - Sign up at <https://leetcode.com/accounts/signup/>.  
   - Use a username format: `DS_[YourInitials]_[RandomNumber]` (e.g., `DS_JD_1234`). Pick any number you like.  
2. **Submit Your Profile**:  
   - By **Monday, Week 2, 11:59 PM**, submit a Google Form with:  
     - Your full name  
     - Student ID  
     - Direct link to your LeetCode profile (e.g., <https://leetcode.com/DS_JD_1234/>)  
   - Google Form link: <https://forms.gle/vWx73VW5H2rdRQav9>  
3. **Start Early**:  
   - Set up your account in Week 1 and begin practicing. Late setups must be coordinated with your TA by Monday of Week 2.  

**Tip**: LeetCode is low-stakes practice with high payoff—consistent effort will boost your exam performance!  

## Part 2: Solving the 3-Sum Problem  
Your task is to solve the **3-Sum problem** on LeetCode using a brute-force approach and analyze its runtime empirically.  

### Problem Details:  
- LeetCode Problem: [3-Sum](https://leetcode.com/problems/3sum/)  
- Goal: Given an integer array `nums`, return all unique triplets `[nums[i], nums[j], nums[k]]` where `i != j != k` and `nums[i] + nums[j] + nums[k] == 0`.  
- Constraint: Use a **brute-force approach** (e.g., three nested loops) for this lab, even though more efficient solutions exist.  

### Steps:  
1. **Solve on LeetCode**:  
   - Implement a brute-force solution in LeetCode’s editor.  
   - Test and submit to ensure correctness.  
2. **Local Implementation**:  
   - Transfer your solution to a C++ program (`3sum_analysis.cpp`) on your local machine or CSIL.  
   - Modify it to handle runtime measurements (see Part 3).  

## Part 3: Empirical Runtime Analysis  
Analyze how your brute-force 3-Sum solution’s runtime scales with input size.  

### Tasks:  
1. **Measure Runtime**:  
   - In `3sum_analysis.cpp`, add code to:  
     - Generate random input arrays of increasing sizes (e.g., `n = 100, 200, 400, 800, 1600`).  
     - Time your 3-Sum function for each size using `chrono` (see sample code below).  
     - Use at least 5 data points, up to `n = 8000`.  If `n = 8000` takes too long, adjust your max size (e.g., to 4000) and note this in your report.”
     - Ensure inputs have at least one valid triplet (e.g., include `-a, -b, a+b` in the array).  
   - Record times in milliseconds.  

   **Sample Timing Code**:  
   ```cpp
   auto start = chrono::high_resolution_clock::now();
   vector<vector<int>> result = threeSum(nums);
   auto end = chrono::high_resolution_clock::now();
   double time_ms = chrono::duration_cast<chrono::microseconds>(end - start).count() / 1000.0;
   ```

2. **Plot Runtime Data**:  
   - **Linear Plot**: Plot runtime `T(n)` (ms) vs. input size (`n`).  Here, T(n) represents your program’s runtime in milliseconds for an input array of size n.
   - **Log-Log Plot**: Plot `log2(T(n))` vs. `log2(n)`.  
   - Use any tool (e.g., Python/Matplotlib, Excel) for plotting.  

3. **Derive an Empirical Model**:  
   - Based on the log-log plot, fit a line to estimate the relationship `log2(T(n)) = m * log2(n) + b`.  
   - Convert to a power-law form: `T(n) = k * n^m`, where `k = 2^b`.  
   - Hint: Examine your brute-force 3-Sum solution. How many nested loops does it use? How does this relate to the exponent of `n` in the power-law formula?

4. **Update Plots**:  
   - Overlay your empirical model (predicted runtime) on both plots.  

5. **Analyze Results**:  
   - In your report:  
     - Do a Big-O analysis of your code and discuss how it relates to your emprical analysis
     - Discuss differences between linear and log-log plots.  
     - Your main takeaways and observations  
       
6. **Optional Challenge (10 Bonus Points)**:
   - Implement an optimized 3-Sum solution (e.g., using sorting and two pointers) with a lower time complexity than your brute-force approach. Measure T(n) for the same input sizes, derive a new empirical model, and compare it to your brute-force results in your report.

## Submission on Gradescope  
Submit **one file**:  
1. **`report.pdf`**: Include:
   - Include a link to your github repo containing the brute-force 3-Sum solution (and the optional, extra credit, optimized 3-Sum solution)
   - Linear plot (runtime vs. `n`) with model overlay  
   - Log-log plot (`log2(runtime)` vs. `log2(n)`) with model overlay  
   - Derivation of your empirical model (show calculations)  
   - Observations (1-2 paragraphs)
   - (If attempted) Optional challenge: Optimized solution description, new plots/models, and comparison to brute-force results

**Note**: Plotting code is optional to submit; focus on the C++ logic and report quality.  

## Grading Rubric (100 points)  
- LeetCode setup (profile submitted): 10 points  
- Correct brute-force 3-Sum solution: 20 points  
- Runtime measurements (5+ data points): 20 points  
- Plots (linear + log-log with model): 20 points  
- Empirical model derivation: 15 points  
- Observations and analysis: 15 points  
- Optional challenge: 10 bonus

## Tips for Success  
- Start early—debugging and plotting take time!  
- Test small inputs first (`n ≤ 100`) to verify correctness.  
- Use a consistent machine for timing (CSIL preferred).  
- Reach out to TAs on Ed for clarification.
- FAQ document: https://docs.google.com/document/d/1FLdL3pMy3bimSAG1hb44OOWpwNxSfo0UV6di6wnpqfw/edit?usp=sharing

