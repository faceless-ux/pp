import numpy as np

# Ask user for number of students and subjects
students = int(input("Enter number of students: "))
subjects = int(input("Enter number of subjects: "))

# Create an empty list to store marks
marks_list = []

# Take marks input from user
for i in range(students):
    print(f"\nEnter marks for Student {i+1}:")
    student_marks = []
    for j in range(subjects):
        m = int(input(f"  Subject {j+1}: "))
        student_marks.append(m)
    marks_list.append(student_marks)

# Convert the list to NumPy array
marks = np.array(marks_list)

# Total and average marks
total_marks = marks.sum(axis=1)
average_marks = marks.mean(axis=1)

# Subject-wise average
subject_avg = marks.mean(axis=0)

# Topper
topper_index = total_marks.argmax()

# Extra stats
std_dev = round(marks.std(), 2)
min_mark = marks.min()
max_mark = marks.max()

# Display results
print("\n------------------- Results -------------------")
for i in range(students):
    print(f"Student {i+1} - Total: {total_marks[i]}, Average: {round(average_marks[i], 2)}")

print("\nSubject-wise average marks:", subject_avg)
print(f"Topper: Student {topper_index + 1} with {total_marks[topper_index]} marks")
print("Standard Deviation of all marks:", std_dev)
print("Minimum mark in dataset:", min_mark)
print("Maximum mark in dataset:", max_mark)
