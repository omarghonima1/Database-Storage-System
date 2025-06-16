🎯 Project Objective
This milestone aims to extend your DBMS implementation (from Milestone 1) by adding core database features that are common in real-world systems:

Bitmap Indexing (for efficient search)

Index-Based Selection

Data Recovery from Missing Pages

You will build on your previous Milestone 1 work or use a provided base implementation.

⚙️ Main Functionalities Implemented
Create Bitmap Index
A compressed, efficient representation of column values for fast filtering.

Insert into Bitmap Index
Whenever a new record is inserted, the relevant index is updated accordingly.

Select Using Index
Perform optimized queries using one or more bitmap indexes.

Data Recovery (Restoring)
Reconstruct a full missing page using a recovery mechanism, not just partial rows.

🧾 Assumptions & Simplifications
To reduce complexity and focus on key database concepts:

Indexes are created manually using createBitMapIndex.

Indexes are not auto-created on table creation.

After an index is created, insertions must update both table and index.

Only full-page loss is considered for recovery.

A helper function is provided to simulate page deletion.

📂 Project Structure (Files & Classes)
File	Purpose
DBApp.java	Main logic for DB operations, including new index and recovery methods.
FileManager.java	Handles file I/O for tables, pages, and bitmap indexes. Two new functions are added.
DBAppTestsMS2.java	Provided JUnit test file to validate your milestone 2 features. Cannot be modified.
BitMapIndex.java (optional)	Your custom class to represent the Bitmap Index structure.

📌 Key New Methods in DBApp.java
Method Signature	Description
validateRecords(String tableName)	Returns missing records if any pages are lost.
recoverRecords(String tableName, ArrayList<String[]> missing)	Recovers the original structure of deleted pages.
createBitMapIndex(String tableName, String colName)	Builds and stores the bitmap index for a given column.
getValueBits(String tableName, String colName, String value)	Returns the bitstream (0s/1s) indicating value positions.
selectIndex(String tableName, String[] cols, String[] vals)	Performs selection using indexes (ANDs result sets, fallbacks to linear if needed).

📥 New Helper Methods in FileManager.java
java
Copy
Edit
public static boolean storeTableIndex(String tableName, String columnName, BitmapIndex b);
public static BitmapIndex loadTableIndex(String tableName, String columnName);
These manage serialization and deserialization of index files in the /Tables/ directory.

🧪 Grading System
Unit-test based: Each function is tested by JUnit tests.

Your grade = Number of passed test cases / Total number of tests.

Initial test file is provided; additional tests are released later.

🧠 Tips for Implementation
Create the BitMapIndex class with methods like:

insertValue(String val)

getBitStream(String val)

updateIndexOnInsert(...)

Ensure you use the same signatures as specified. Do not rename or change parameters.

Keep the bitmap files saved with naming convention:
Tables/{tableName}/{columnName}.db

When recovering pages, reintegrate records in their original page order.

✅ Milestone Completion Checklist
 Can create and save bitmap index.

 Insertions update both table and bitmap index.

 Can return bitstreams for indexed values.

 Selection logic uses index when available.

 Recovery accurately restores missing pages.

 All method signatures exactly match required format.

 All test cases in DBAppTestsMS2.java pass.

🧰 Running the Project in Eclipse
Create a new Java project in Eclipse.

Import all milestone 1 files and replace FileManager.java with the updated one.

Add new classes:

BitMapIndex.java (optional but recommended)

Implement all missing methods in DBApp.java.

Place your DBAppTestsMS2.java in the src directory and run it as a JUnit test.

Create a /Tables/ folder in your project root for storing serialized tables and indexes.

