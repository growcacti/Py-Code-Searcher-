# Py-Code-Searcher-
Find specific blocks of code
 

Overview of the Enhanced Python Code Searcher Application
This program is a Graphical User Interface (GUI) application built using Tkinter, designed for efficiently searching Python code files for specific patterns, structures, and constructs. Its primary use case is to aid developers or analysts in searching large codebases, analyzing Python scripts, and extracting relevant blocks of code.

Key Features
Recursive or Non-Recursive Directory Search:

Allows users to search all .py files in a directory, optionally including subdirectories.
Pattern Matching:

Searches for specific Python constructs, including:
Dictionaries
Lists
Tuples
Sets
Generators
Methods/Functions
Modules (functools, itertools, collections, or user-specified ones)
Custom Module Support:

Users can specify additional module names for pattern matching through an input field.
Contextual Output:

Displays a configurable number of lines of code before and after each match (default is 10 lines, adjustable via a spinbox).
User-Friendly Output:

Results are shown in a scrollable text box with clear formatting and separators for better readability.
Summary of Results:

A dedicated summary box displays the number of matches for each pattern.
Save and Clear Options:

Users can save the search results to a .txt file.
Results and summaries can be cleared with a single click.
Progress Tracking:

A progress bar visually tracks the progress of the search process.
Cancellation:

Includes a cancel button to stop long-running searches.
Threading for Responsiveness:

The search operation is run in a separate thread to ensure the GUI remains responsive.
Technology Stack
Programming Language: Python
GUI Framework: Tkinter
Modules Used:
os and glob: For file traversal.
re: For regular expression-based pattern matching.
threading: For handling long-running tasks without freezing the GUI.
ScrolledText: For displaying scrollable output.
filedialog: For file and directory browsing.
How It Works
Directory Selection:

The user selects a directory using the "Browse" button.
Search Configuration:

The user chooses what to search for:
Built-in patterns (e.g., dictionaries, lists, functions).
User-defined modules.
Specifies the number of context lines.
Search Execution:

When "Search" is clicked, the program:
Recursively scans the directory (if enabled).
Matches patterns using re (regular expressions).
Displays results incrementally in a text widget.
Updates the summary of matches dynamically.
Result Handling:

Results can be reviewed in a scrollable output box.
The user can save or clear the results.
Cancel Search:

The user can stop the search mid-way by clicking "Cancel."
Potential Use Cases
Code Auditing: Quickly locate specific constructs or usages in large Python projects.
Debugging Assistance: Identify problematic patterns or missed imports.
Code Analysis: Review specific structures like generators or modules.
Educational Purposes: Demonstrate or explore Python constructs in real-world projects.
User Interface Description
Directory Selection:

An entry box and a "Browse" button for selecting the directory.
Search Options:

Checkboxes for predefined search patterns.
Input field for specifying additional modules.
Context Settings:

A spinbox to control how many lines of code before and after each match are displayed.
Output Area:

A large, scrollable text box for displaying search results.
A summary box for match counts.
Controls:

Search: Starts the search operation.
Cancel: Stops the search operation.
Save Results: Saves the results to a file.
Clear: Clears all results and the summary.
Progress Bar:

Shows progress for directories being processed.



What might come as updates to this program :

The issue likely arises because the ast.parse logic isn't robust enough to handle all cases, particularly for widget-related assignments and function calls. The current implementation assumes widgets are directly instantiated or assigned within the parsed code. Here's how to refine it:

Improvements for Better Widget Detection:
Ensure All Assignments Are Detected:

Look at all Assign nodes and ensure that widget creations (tk.Entry, ttk.Button, etc.) are captured, even if nested within other constructs.
Improve Handling of Direct Function Calls:

Add logic to detect widgets created and directly configured with .pack(), .grid(), etc., without assignment.
Account for Namespace Differences:

Detect widgets regardless of whether they use tk. or ttk. prefixes or are imported directly (e.g., from tkinter import Entry).
Enhance find_widgets Debugging:

Add logging or print statements to verify which nodes are visited and what matches are found.
