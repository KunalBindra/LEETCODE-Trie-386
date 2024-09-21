# LEETCODE-Trie-386
The provided code generates the lexicographical order of integers from 1 to `n`. Let's walk through a dry run to see how it works.

### Problem Statement:
Given an integer `n`, the goal is to return a list of integers from 1 to `n` in lexicographical order.

### Plan:
1. Start at `curr = 1`.
2. Add `curr` to the list `ans`.
3. If multiplying `curr` by 10 doesn't exceed `n`, move to the next "deeper" lexicographical level (e.g., `1 -> 10`).
4. If not, check if `curr` can be incremented by one while maintaining lexicographical order (e.g., `19 -> 2`).
5. Skip numbers that end in `9` (they should "jump up" a level).

### Dry Run Example for `n = 13`:

```java
n = 13
List<Integer> ans = []
curr = 1
```

- Start with `curr = 1`.
- Add `1` to the list: `ans = [1]`.
- Since `1 * 10 = 10 <= 13`, go deeper: `curr = 10`.

---

- Add `10` to the list: `ans = [1, 10]`.
- Since `10 * 10 = 100 > 13`, increment: `curr = 11`.

---

- Add `11` to the list: `ans = [1, 10, 11]`.
- Since `11 * 10 = 110 > 13`, increment: `curr = 12`.

---

- Add `12` to the list: `ans = [1, 10, 11, 12]`.
- Since `12 * 10 = 120 > 13`, increment: `curr = 13`.

---

- Add `13` to the list: `ans = [1, 10, 11, 12, 13]`.
- Now, `curr = 13`, which is equal to `n`, so go back to the upper level.
- Divide `curr` by 10: `curr = 1`.
- Increment `curr` to `2`.

---

- Add `2` to the list: `ans = [1, 10, 11, 12, 13, 2]`.
- Since `2 * 10 = 20 > 13`, increment: `curr = 3`.

---

- Add `3` to the list: `ans = [1, 10, 11, 12, 13, 2, 3]`.
- Since `3 * 10 = 30 > 13`, increment: `curr = 4`.

---

- Add `4` to the list: `ans = [1, 10, 11, 12, 13, 2, 3, 4]`.
- Continue this process until the list contains all numbers from 1 to `n`.

### Final List for `n = 13`:
`[1, 10, 11, 12, 13, 2, 3, 4, 5, 6, 7, 8, 9]`

This is the lexicographical order from 1 to 13.

---

### Edge Cases:
1. **n = 1**: The output will simply be `[1]`.
2. **n = 9**: Output will be `[1, 2, 3, 4, 5, 6, 7, 8, 9]`, as no multiplication by 10 happens.
3. **n = 1000**: The algorithm efficiently handles larger values by leveraging the lexicographical pattern.
