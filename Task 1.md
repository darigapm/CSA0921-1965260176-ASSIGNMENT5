# Task 1 – Design a File Format (Bus-Pass Records)

## Record Layouts
* **Field Order:** Pass ID, register number, name, route number, boarding stop, validity date, amount[cite: 58].
* **Delimited Text Format:** Comma-delimited with one record per line (`yyyy-MM-dd` date and plain decimal amount), ending with a newline[cite: 58]. Commas inside a name are escaped as `\,`, backslashes as `\\`, newlines are removed, and splitting happens only on unescaped commas[cite: 58]. Any line with an unexpected field count is treated as a damaged line[cite: 58].
* **Binary Format (`DataOutputStream`):** `passId`, `regNo`, `name`, and `boardingStop` use `writeUTF` (2-byte length + text); `routeNo` uses `writeInt` (4 bytes); `validityDate` uses `writeLong` epoch day (8 bytes); `amount` uses `writeDouble` (8 bytes).

## Stream Choice & Pseudocode
* **Add:** `FileWriter` wrapped in `BufferedWriter` in append mode so existing data is not rewritten.
* **Find & List:** `FileReader` wrapped in `BufferedReader` for line-by-line text reading.
* **Byte Streams:** `FileInputStream` / `FileOutputStream` are reserved for binary layouts rather than text records.

```text
ALGORITHM FindPass (file, passId)
1. IF file does not exist THEN RETURN NOT_FOUND
2. OPEN file with BufferedReader
3. WHILE (line <- READLINE) is not END_OF_FILE DO
4.     fields <- split(line)
5.     IF count(fields) is not the expected number THEN CONTINUE // damaged line
6.     IF fields [0] = passId THEN CLOSE, RETURN fields
7. END WHILE
8. CLOSE reader, RETURN NOT_FOUND
END
