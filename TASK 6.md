# Task 6 – Implement and Instrument the File Store

## Validation, Comparison & Performance
* Tests cover valid add/find (`T1`, `T2`), missing ID (`T3`), damaged lines (`T4`–`T6`), route listing (`T7`, `T8`), and missing file handling (`T9`, `T10`)[cite: 64, 65].
* `find()` reads lines via `BufferedReader` in try-with-resources, skips lines without 5 fields, and returns matching pass fields (with `double` amounts formatted as `3800.0`)[cite: 65].
* The starter 5-field format and unescaped names differ from the 7-field comma-escaped design in the file-format task, with `listByRoute()` added for route queries[cite: 65].
* Buffered reads (`BufferedInputStream` or `byte[8192]`) cut OS read calls compared to unbuffered single-byte `read()` (~52.4M calls vs ~6,400 calls for 50 MB), while `readAllLines()` uses $O(n)$ memory[cite: 61, 65].
* Linear `find()` scales as $O(n)$ per search ($O(q \times n)$ for $q$ queries), whereas a startup `HashMap` achieves $O(n + q)$ time at $O(n)$ memory cost[cite: 66].
