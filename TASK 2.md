# Task 2 – Don't Read What You Don't Need

## Buffering Analysis & Trade-offs
* A 50 MB file (`52,428,800` bytes) read one byte at a time via `FileInputStream.read()` makes ~52.4 million calls dominated by call overhead[cite: 60].
* Using an `8,192`-byte buffer or `BufferedInputStream` reduces OS read calls to ~6,400 (8,192 times fewer)[cite: 61].
* Buffering helps less when reading large blocks already, doing sparse random seeks, reading from slow/chunked streams like keyboard or network, or handling tiny files[cite: 61].
* `Files.readAllLines()` runs in $O(n)$ time but uses $O(\text{file size})$ heap memory instead of $O(\text{buffer size})$, risking `OutOfMemoryError` on large files; buffered streaming suits large/one-pass reads, while `readAllLines` fits small files needing all lines at once[cite: 61].
