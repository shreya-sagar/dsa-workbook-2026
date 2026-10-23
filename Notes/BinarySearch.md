# Binary Search

**Pattern:** Divide the sorted search space in half.

- **Time:** `O(log n)` | **Space:** `O(1)`
- **Mid:** `start + (end - start) / 2` (avoids overflow)

## 1. Classic Binary Search — LC 704
**Goal:** Find target; return `-1` if absent.

- `start = 0`, `end = n - 1`
- Loop: `start <= end`
- Found → return `mid`
- `nums[mid] < target` → `start = mid + 1`
- `nums[mid] > target` → `end = mid - 1`
- Loop ends → return `-1`

## 2. Lower Bound — LC 35
**Goal:** First index where `nums[i] >= target`.

- `nums[mid] < target` → `start = mid + 1`
- Otherwise → `end = mid - 1`
- Return `start` (insertion index if absent).

## 3. First & Last Occurrence — LC 34
Run binary search twice.

- **First:** Found → save `mid`; `end = mid - 1`
- **Last:** Found → save `mid`; `start = mid + 1`
- Otherwise: move pointers using classic rules.
- Initialize result to `-1`.

## 4. First Bad Version — LC 278
**Pattern:** First-true / boundary search.

- Bad → `end = mid` (mid may be the answer).
- Good → `start = mid + 1`.
- Loop: `start < end`.
- Return `start` when pointers converge.

## Common Mistakes
- Incorrect midpoint formula.
- Moving the wrong pointer.
- Using `mid - 1` when `mid` could still be the answer.
- Returning immediately when searching for a boundary.
- Forgetting missing-target handling.

## Mental Checklist
1. What is the search space?
2. What do `start` and `end` represent?
3. Which half can I eliminate?
4. Could `mid` still be the answer?
5. What should I return?

**Next problem:** LC 153 — Find Minimum in Rotated Sorted Array.