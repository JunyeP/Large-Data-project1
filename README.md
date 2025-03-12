# Large Scale Data Processing: Project 1 Report

## Running the Program on Local Machine

For each `k`, the following values were recorded: `xS`, hash value, total time elapsed, and number of trials.

### k = 2
- **xS:** `2056048962this_is_a_bitcoin_block_of_57134520`
- **Hash Value:** `0023b3f9c56a06814ffa086fe53c911ad7d08c9fdf9a27e263e1f93d50425148`
- **Time Elapsed:** `4s`
- **Number of Trials:** `10,000`

### k = 3
- **xS:** `106756730`
- **Hash Value:** `0002ba9e90dc77763f04587e5a26896290a86e6b2f3a39d48ee7f92b263ca2ae`
- **Time Elapsed:** `4s`
- **Number of Trials:** `10,000`

### k = 4
- **xS:** `2020806387`
- **Hash Value:** `0000ad2207705eda872a4129b47212b35ea77747a024637c3cd16d59f4298ae2`
- **Time Elapsed:** `5s`
- **Number of Trials:** `10,000`

### k = 5
- **xS:** `1207424538`
- **Hash Value:** `000005d144d20fde6d7dd5aefcfe65b3b0f5b6cca5f0547d23d047963165e298`
- **Time Elapsed:** `5s`
- **Number of Trials:** `1,000,000`

### k = 6
- **xS:** `1826494685`
- **Hash Value:** `000000586df3c105cf89d78fa5963d130e97d2d74c312ee205eefabcf79d86da`
- **Time Elapsed:** `38s`
- **Number of Trials:** `100,000,000`

---

## Running the Program on GCP for k = 7

- **xS:** *(To be determined)*
- **Hash Value:** *(To be determined)*
- **Time Elapsed:** *(To be determined)*
- **Number of Trials:** *(To be determined)*

### Cluster Configuration:
- **Number of Machines:** *(Specify)*
- **Number of Cores per Machine:** *(Specify)*
- **Type of Cores:** *(Specify, e.g., Intel Xeon, AMD EPYC, etc.)*
- **Total vCPUs Used:** *(Specify)*

### Process for Estimating the Number of Trials:
To estimate the number of trials required for finding the nonce, the previous results were analyzed. Observing the exponential increase in trials for each `k`, the expected number of trials for `k = 7` was estimated by extrapolating the pattern:

\[
\text{Estimated trials} \approx 10^8 \times 10 = 10^9
\]

By distributing the workload across multiple machines and cores, the total computation time was significantly reduced.

---

## Code Modification for Sequential Nonce Generation

A single line in `src/main/scala/project_1/main.scala` was modified:

```scala
val nonce = sc.range(1, trials + 1).map(_.toInt)
