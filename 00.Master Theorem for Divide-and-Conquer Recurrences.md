# Master Theorem for Divide-and-Conquer Recurrences

The Master Theorem provides a straightforward way to determine the time complexity of recurrence relations that arise in the analysis of divide-and-conquer algorithms. It applies to recurrences of the form:

    T(n) = aT(n/b) + f(n)

where:
- `a >= 1` is the number of subproblems.
- `b > 1` is the factor by which the problem size is divided in each subproblem.
- `f(n)` is the cost outside the recursive calls, such as the cost to divide the problem and combine the results of the subproblems.

## The Master Theorem

The Master Theorem provides three cases based on the comparison between `f(n)` and `n^(log_b a)`:

1. **Case 1**: `f(n) = O(n^d)` where `d < log_b a`
   - `T(n) = O(n^(log_b a))`
   - The recursion term dominates.

2. **Case 2**: `f(n) = Θ(n^d)` where `d = log_b a`
   - `T(n) = Θ(n^(log_b a) log n)`
   - Both terms contribute equally with an additional logarithmic factor.

3. **Case 3**: `f(n) = Ω(n^d)` where `d > log_b a`
   - If `af(n/b) <= kf(n)` for some `k < 1` and sufficiently large `n`,
   - `T(n) = Θ(f(n))`
   - The cost function `f(n)` dominates.

## Examples

### Example 1: Merge Sort

- **Recurrence relation**: `T(n) = 2T(n/2) + O(n)`
- Here, `a = 2`, `b = 2`, and `f(n) = O(n)`.
- Calculate `log_b a = log_2 2 = 1`.
- Compare `f(n)` with `n^(log_b a) = n^1`:
  - `f(n) = Θ(n)`, which matches Case 2.
- **Time complexity**: `T(n) = Θ(n log n)`.

### Example 2: Binary Search

- **Recurrence relation**: `T(n) = T(n/2) + O(1)`
- Here, `a = 1`, `b = 2`, and `f(n) = O(1)`.
- Calculate `log_b a = log_2 1 = 0`.
- Compare `f(n)` with `n^(log_b a) = n^0 = 1`:
  - `f(n) = O(1)`, which matches Case 2.
- **Time complexity**: `T(n) = Θ(log n)`.

### Example 3: Complex Divide and Conquer

- **Recurrence relation**: `T(n) = 3T(n/4) + n^2`
- Here, `a = 3`, `b = 4`, and `f(n) = n^2`.
- Calculate `log_b a = log_4 3 ≈ 0.79`.
- Compare `f(n)` with `n^(log_b a) ≈ n^0.79`:
  - `f(n) = Ω(n^2)`, which matches Case 3.
- Check the regularity condition: `3(n^2/16) <= kn^2` for some `k < 1` and large `n`, which is true.
- **Time complexity**: `T(n) = Θ(n^2)`.

## Summary

The Master Theorem is a very useful tool for analyzing recurrences of the form `T(n) = aT(n/b) + f(n)`, but it has limitations and cannot be applied to all types of recurrence relations. When the Master Theorem does not apply, other methods such as iteration, recursion tree, or the Akra-Bazzi method might be used to solve the recurrence.

 𝑇(𝑛)=10𝑇(𝑛/3)+17𝑛^1.2 (We can use master theorem for this as well. let f(n)=17n^1.2 -> Then d=1.2)
