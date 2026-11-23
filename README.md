CSA09 – Programming in Java – Assignment 5
Data Persistence Engineering – Files and Databases
Name	P.M.DARIGA
Register number	1965260176
Java version	run java -version and write it here (code needs Java 11 or later; tested with 21)
GitHub repository	https://github.com//CSA09--Assignment5
Rename this folder to CSA09-<YourRegisterNumber>-Assignment5 before pushing.

Folder structure
PartA/            Part A design answers (record layouts, pseudocode, analysis)  – no Java code
Task01/  (B1)     PassStore (TODO 1), tests, buffering + growth benchmark
Task02/  (B2)     SQL-injection demo, damaged-file demo, schema.sql
Task03/  (B3)     PassLoader (TODO 1-3), Statement / Prepared / Batch benchmark, schema.sql
Task04/  (B4)     Migration (file -> MySQL), DbInfo (DatabaseMetaData), schema.sql
lib/              put the MySQL Connector/J jar here (Tasks 02-04)
TaskXX/ANALYSIS.md  alternative-concept analysis + tables where YOU enter your measurements
TaskXX/screenshots/ put your output screenshots here
One-time setup
Install JDK 11+ (javac -version must work).
Install MySQL, then run the scripts below. Use a test database only.
Download MySQL Connector/J and copy the .jar into lib/.
If your MySQL login is not root with an empty password, set environment variables DB_USER, DB_PASS (optional DB_URL). Windows: set DB_USER=root and set DB_PASS=yourpassword.
How to compile and run each task
Open a terminal inside the task folder, then use run.bat (Windows) or ./run.sh (Linux/Mac) – or the commands below (Windows classpath separator ;, Linux/Mac :).

Task	Setup	Commands
Task01 (B1)	none	javac *.java then java PassStore, java Task01Tests, java Task01Benchmark
Task02 (B2)	mysql -u root -p < schema.sql	javac -cp ".;..\lib\*" *.java then java -cp ".;..\lib\*" DamagedFileDemo and LoginDemo
Task03 (B3)	mysql -u root -p < schema.sql	java -cp ".;..\lib\*" BatchBenchmark (the 100,000-row Statement test can take minutes; you may pass sizes, e.g. BatchBenchmark 1000 10000)
Task04 (B4)	mysql -u root -p < schema.sql	java -cp ".;..\lib\*" Migration then DbInfo
Measurement results are saved automatically in Task01/results/*.csv and Task03/results/*.csv. Run each benchmark 2–3 times and report typical values; close other programs while measuring.
