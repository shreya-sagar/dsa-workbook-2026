# DSA Workbook 2026

## 1. Java Arrays vs ArrayList

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
