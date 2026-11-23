# Task 3 – Discover the Data Access Design Pattern

## DAO Design & Table Mapping
* Repeating connection setup, SQL execution, `ResultSet` iteration, and cleanup across `StudentDB`, `CourseDB`, and `MarksDB` motivates the Data Access Object (DAO) pattern[cite: 61, 62].

```text
INTERFACE Dao<T, K>
    insert(T entity)    : integer
    findById(K key)     : T or NULL
    findAll()           : List<T>
    update(T entity)    : integer
    delete(K key)       : integer
END INTERFACE

CLASS StudentDao IMPLEMENTS Dao<Student, String>
    insert(s):
        SQL <- "INSERT INTO student(reg_no, name, dept, cgpa) VALUES (?,?,?,?)"
        PREPARE, SET parameters from s, EXECUTE_UPDATE
    findById(k):
        SQL <- "SELECT * FROM student WHERE reg_no=?"
        IF a row exists THEN RETURN mapRow(row) ELSE RETURN NULL
END CLASS
