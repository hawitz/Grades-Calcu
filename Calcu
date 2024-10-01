def calculate_grade(absences, prelim_exam, quizzes, requirements, recitation):
    try:
        # Validate that the grades are between 0 and 100
        if not (0 <= prelim_exam <= 100):
            return "Error: Prelim Exam grade must be between 0 and 100."
        if not (0 <= quizzes <= 100):
            return "Error: Quizzes grade must be between 0 and 100."
        if not (0 <= requirements <= 100):
            return "Error: Requirements grade must be between 0 and 100."
        if not (0 <= recitation <= 100):
            return "Error: Recitation grade must be between 0 and 100."

        # Attendance Calculation
        attendance = 100 - (absences * 10)

        if absences >= 4:
            return "FAILED due to absences."
        
        # Class Standing Calculation
        class_standing = (0.40 * quizzes) + (0.30 * requirements) + (0.30 * recitation)

        # Prelim Grade Calculation
        prelim_grade = (0.60 * prelim_exam) + (0.10 * attendance) + (0.30 * class_standing)

        # Midterm/Final Grades for 75 Passing
        prelim_percent = 0.20
        midterm_percent = 0.30
        final_percent = 0.50

        passing_grade = 75
        passing_grade2 = 90  # Dean's Lister Grade

        current_total = prelim_grade * prelim_percent
        required_total = passing_grade - current_total
        required_total2 = passing_grade2 - current_total

        # Midterm/Final Grades for 75 Passing
        if required_total > 0:
            required_midterm_and_final = required_total / (midterm_percent + final_percent)
        else:
            required_midterm_and_final = 0

        # Midterm/Final Grades for 90 Passing (Dean's Lister)
        if required_total2 > 0:
            required_midterm_and_final2 = required_total2 / (midterm_percent + final_percent)
        else:
            required_midterm_and_final2 = 0

        result = (f"Prelim Grade: {prelim_grade:.2f}%\n"
                  f"To pass with 75%, you need a Midterm grade of {required_midterm_and_final:.2f}% and "
                  f"a Final grade of {required_midterm_and_final:.2f}%.\n"
                  f"To achieve 90%, you need a Midterm grade of {required_midterm_and_final2:.2f}% and "
                  f"a Final grade of {required_midterm_and_final2:.2f}%.")
        return result

    except ZeroDivisionError:
        return "Error: Cannot divide by zero!"
    except Exception as e:
        return f"Error: {e}"

# Input simulation with validation for grades not exceeding 100
def get_input(prompt, min_value=0, max_value=100):
    while True:
        try:
            value = float(input(prompt))
            if min_value <= value <= max_value:
                return value
            else:
                print(f"Please enter a value between {min_value} and {max_value}.")
        except ValueError:
            print("Invalid input. Please enter a numeric value.")

absences = int(input("Enter Number of Absences: "))
prelim_exam = get_input("Enter Prelim Exam Grade (0-100): ")
quizzes = get_input("Enter Quizzes Grade (0-100): ")
requirements = get_input("Enter Requirements Grade (0-100): ")
recitation = get_input("Enter Recitation Grade (0-100): ")

# Calculate and display the result
result = calculate_grade(absences, prelim_exam, quizzes, requirements, recitation)
print(result)
