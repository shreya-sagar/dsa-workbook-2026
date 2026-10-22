# DSA Workbook 2026

## Patterns

### 1. Hashing — Presence Array

**Concept:** Use an array to track whether a value has already been encountered.

**When to use:**
- Check if an array contains duplicates.
- Find repeating elements.
- Track whether values have appeared before.
- Count frequencies of values (with a frequency array).

**Java Implementation:**

```java
public boolean containsDuplicate(int[] nums) {
    int[] seen = new int[11];

    for (int num : nums) {
        if (seen[num] == 1) {
            return true;
        }
        seen[num] = 1;
    }

    return false;
}
```

**Complexity:**
- Time: `O(n)`
- Space: `O(k)`, where `k` is the size of the value range.

**Limitation:** This implementation assumes all values are between `0` and `10`. For arbitrary integer values, use a `HashSet<Integer>`.

**Recognition clue:** "Have I seen this value before?" → Think **Hashing — Presence Array**.

## Java Arrays vs ArrayList

**Array**
- Fixed size; index access: O(1).
- Search: O(n).
- Cannot resize; create a new array and copy elements.

**ArrayList**
- Dynamic array; maintains `size` and `capacity`.
- Resizes automatically when full.
- `new ArrayList<>(5)` sets initial capacity, not maximum size.

| Operation                             | Complexity |
|---------------------------------------|------------|
| ArrayList append (capacity available) | O(1)       |
| Append requiring resize               | O(n)       |
| Repeated appends (amortized)          | O(1)       |

**Amortized O(1):** Occasional expensive resizing is spread across many appends; n appends take O(n) total time.

## 2. Types of Sets in Java

`Set` stores unique elements; no index-based access.

| Type                    | Ordering               | Lookup       |
|-------------------------|------------------------|--------------|
| `HashSet`               | No guaranteed order    | O(1) average |
| `LinkedHashSet`         | Insertion order        | O(1) average |
| `TreeSet`               | Sorted order           | O(log n)     |
| `EnumSet`               | Enum declaration order | Very fast    |
| `CopyOnWriteArraySet`   | Insertion order        | O(n)         |
| `ConcurrentSkipListSet` | Sorted order           | O(log n)     |

**When to use**
- `HashSet`: Uniqueness, duplicate detection, fast membership checks.
- `LinkedHashSet`: Preserve insertion order.
- `TreeSet`: Unique, sorted elements.
- `EnumSet`: Enum values.
- `CopyOnWriteArraySet`: Thread-safe, read-heavy workloads.
- `ConcurrentSkipListSet`: Thread-safe, sorted elements.

## 3. Array vs Set: DSA Rule

| Requirement                               | Choose    |
|-------------------------------------------|-----------|
| Index-based access, two pointers          | Array     |
| Detect duplicates, track visited elements | `HashSet` |
| Unique elements in sorted order           | `TreeSet` |

**Complexity reminders**
- Array index access: O(1); unsorted search: O(n).
- `HashSet` add, remove, and lookup: O(1) average, O(n) worst case.
- `HashSet` uses hashing; collisions can require additional checks.
- Set insertion/deletion has no beginning or end position unless the implementation defines an order.
