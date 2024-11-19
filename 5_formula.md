### 1. **Bash (Bourne Again Shell)**
Bash is a Unix shell and command language. It is widely available on various operating systems and is the default shell on most Linux distributions. Bash scripts are used for automating tasks.

### 2. **`grep`**
`grep` is a command-line utility for searching plain-text data sets for lines that match a regular expression. In this script, `grep` is used to find lines containing the phrase "skipping servicemonitor" in the log files.

### 3. **`date`**
The `date` command is used to display or set the system date and time. In this script, it is used to:
   - Calculate the timestamp for one day ago.
   - Convert log dates to epoch time for comparison.

### 4. **Regular Expressions**
Regular expressions (regex) are patterns used to match character combinations in strings. In this script, regex is used within `grep` and `if` statements to extract timestamps and `servicemonitor` names from log entries.

### 5. **Pipelines and Redirection**
Pipelines (`|`) and redirection (`>`, `<`) are used to pass the output of one command as input to another. In this script:
   - `|` is used to pass the output of `grep` to a `while read` loop.
   - `| sort | uniq` is used to sort the output and remove duplicate entries.

### Script Breakdown
- **Defining Log File Paths**: The script starts by defining the paths to the log files.
- **Function `extract_servicemonitor`**: This function processes each log file to extract relevant `servicemonitor` entries from the past day.
  - **`grep`**: Searches for lines containing "skipping servicemonitor".
  - **Regex Matching**: Extracts timestamps and `servicemonitor` names.
  - **Date Comparison**: Converts dates to epoch time and compares them to the timestamp for one day ago.
  - **Output Formatting**: Formats and prints the results.
- **Displaying Results**: The script calls the function for each log file and displays the results.