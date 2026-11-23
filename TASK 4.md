# Task 4 – What Should Be Serialized?

## Serialization & Versioning
* Secrets like `password` and non-serializable runtime objects like database connections should be marked `transient` (`Connection` is not `Serializable` and cannot survive program termination)[cite: 63].
* Serializing a `Hostel` object traverses reachable `Room` and `Resident` objects implementing `Serializable`, skipping `transient` and `static` fields[cite: 63].
* Declaring a constant `serialVersionUID` lets older serialized files load when adding a `phone` field (defaulting to `null`), whereas omitting it changes the generated UID and causes `InvalidClassException`[cite: 63].
* Serialization, CSV, and JSON all run in $O(n)$ time for $n$ residents, but CSV/JSON are text-based and language-neutral while Java serialization carries class metadata and is Java-specific[cite: 63].
