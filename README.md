# Data_Analysis_Program
# =========================================================
# STUDENT DATA ANALYSIS SYSTEM WITH ALL GRAPHS
# BCA 1st Year Mini Project
# =========================================================

# Import Libraries
import pandas as pd
import matplotlib.pyplot as plt

# ---------------------------------------------------------
# Create Student Database
# ---------------------------------------------------------

data = {
    'Name': ['Amit', 'Ravi', 'Neha', 'Priya', 'Karan',
             'Sneha', 'Arjun', 'Pooja', 'Vikas', 'Anjali'],

    'Year': ['1st', '1st', '1st', '2nd', '2nd',
             '2nd', '3rd', '3rd', '3rd', '1st'],

    'Maths': [80, 65, 90, 75, 60, 85, 70, 95, 66, 78],

    'Science': [85, 70, 95, 80, 65, 88, 72, 90, 68, 82],

    'English': [78, 60, 88, 82, 70, 90, 75, 92, 74, 80]
}

# Create DataFrame
df = pd.DataFrame(data)

# ---------------------------------------------------------
# Calculate Total and Average
# ---------------------------------------------------------

df['Total'] = df['Maths'] + df['Science'] + df['English']
df['Average'] = df['Total'] / 3

# ---------------------------------------------------------
# Display Student Data
# ---------------------------------------------------------

print("\n========== STUDENT DATABASE ==========\n")
print(df)

# ---------------------------------------------------------
# Topper Student
# ---------------------------------------------------------

max_marks = df['Total'].max()

topper = df[df['Total'] == max_marks]

print("\n========== TOPPER STUDENT ==========\n")
print(topper[['Name', 'Year', 'Total', 'Average']])

# ---------------------------------------------------------
# Average Students
# ---------------------------------------------------------

average_students = df[(df['Average'] >= 60) & (df['Average'] < 80)]

print("\n========== AVERAGE STUDENTS ==========\n")
print(average_students[['Name', 'Average']])

# ---------------------------------------------------------
# Year-wise Average
# ---------------------------------------------------------

year_average = df.groupby('Year')['Average'].mean()

print("\n========== YEAR-WISE AVERAGE ==========\n")
print(year_average)

# =========================================================
# GRAPH 1 : LINE GRAPH
# =========================================================

plt.figure(figsize=(8, 5))

plt.plot(df['Name'], df['Total'], marker='o')

plt.title("Student Total Marks - Line Graph")

plt.xlabel("Student Name")

plt.ylabel("Total Marks")

plt.grid(True)

plt.show()

# =========================================================
# GRAPH 2 : BAR GRAPH
# =========================================================

plt.figure(figsize=(8, 5))

plt.bar(df['Name'], df['Total'])

plt.title("Student Total Marks - Bar Graph")

plt.xlabel("Student Name")

plt.ylabel("Total Marks")

plt.show()

# =========================================================
# GRAPH 3 : PIE CHART
# =========================================================

plt.figure(figsize=(8, 8))

plt.pie(
    df['Total'],
    labels=df['Name'],
    autopct='%1.1f%%'
)

plt.title("Student Marks Distribution - Pie Chart")

plt.show()

# =========================================================
# GRAPH 4 : HISTOGRAM
# =========================================================

plt.figure(figsize=(8, 5))

plt.hist(df['Total'], bins=5)

plt.title("Histogram of Student Total Marks")

plt.xlabel("Total Marks")

plt.ylabel("Frequency")

plt.show()

# =========================================================
# GRAPH 5 : SCATTER PLOT
# =========================================================

plt.figure(figsize=(8, 5))

plt.scatter(df['Name'], df['Total'])

plt.title("Scatter Plot of Student Marks")

plt.xlabel("Student Name")

plt.ylabel("Total Marks")

plt.show()

# =========================================================
# GRAPH 6 : YEAR-WISE BAR GRAPH
# =========================================================

plt.figure(figsize=(6, 5))

year_average.plot(kind='bar')

plt.title("Year-wise Average Marks")

plt.xlabel("Year")

plt.ylabel("Average Marks")

plt.show()

# ---------------------------------------------------------
# Program End
# ---------------------------------------------------------

print("\nProject Completed Successfully!")