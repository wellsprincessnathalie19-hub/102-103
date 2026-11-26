import random

print("================================================")
print("             STUDY REVIEW PROGRAM")
print("================================================")

name = input("Enter your name: ")

lessons = {
    "1": {
        "title": "PRELIM - Introduction to Python",
        "lesson": [
            "Python is a widely-used programming language that was created by Guido van Rossum in 1991.",
            "Syntax refers to the set of rules that tells us how to correctly write a program in Python.",
            "Python is also case-sensitive, meaning that uppercase and lowercase letters are diffent",
            "The print() function displays output.",
            "Python ignores comments when running a program",
            "Variables is a named used to store data.",
            "The input() function allows user to input.",
            "Str-used for text \n-Int-used for numbers \n-Float-used for decimal number \n-Boolean-used for true or false values",
            "Arithmetic Operators-Arithmetic operators are symbols used to perform mathematical calculations on number.",
        ],
        "quiz": [
            ("Who created Python Programming language?", "Guido van Rossum"),
            ("What function displays output?", "print()"),
            ("What function accepts user input?", "input()"),
            ("What stores data in Python?", "variable"),
            ("What function display whole numbers?", "int"),
            ("What function display text or characters?", "str"),
            ("What programming language are we studying?", "python")
           
        ]
    },

    "2": {
        "title": "MIDTERM - Conditional Statements",
        "lesson": [
            "Conditional statements allow programs to make decisions.",
            "The if statement checks a condition.",
            "The elif statement checks another condition.",
            "The else statement executes when other conditions are false.",
            "Conditions can be True or False."
            "\n\n  Logical Operators \n AND- both conditions must be True \n OR- At least one condition must be True \n NOT- Reverse the result.",
            
        ],
        "quiz": [
            ("What statement checks a condition?", "if"),
            ("What keyword checks another condition?", "elif"),
            ("What executes if the conditions are false?", "else"),
            ("What are the two Boolean values?", "true and false"),
            ("What statement is used for decision-making?", "if"),
            ("What is the output of True AND False?", "False"),
        ]
    },

    "3": {
        "title": "FINALS - While Loop",
        "lesson": [
            "A while loop repeats code while a condition is True.",
            "A loop is used to repeat instructions.",
            "The break keyword stops a loop.",
            "A loop can become infinite if its condition never becomes False.",
            "A counter can be used to control a loop."
        ],
        "quiz": [
            ("What loop repeats while a condition is True?", "while"),
            ("What keyword stops a loop?", "break"),
            ("What Boolean value keeps a condition active?", "true"),
            ("What is a loop that never stops called?", "infinite loop"),
            ("What variable is commonly used to count repetitions?", "counter")
        ]
    }
}

scores = {"1": None, "2": None, "3": None}

while True:
    print("\n[1] Prelim")
    print("[2] Midterm")
    print("[3] Finals")
    print("[4] Show Total Score")
    print("[5] Exit")

    choice = input("\nChoose a period: ")

    if choice in lessons:
        selected = lessons[choice]

        print("\n================================================")
        print(selected["title"])
        print("================================================")

        print("\n--- LESSON ---")
        for topic in selected["lesson"]:
            print("-", topic)

        print("\n--- RANDOM QUIZ ---")

        questions = random.sample(selected["quiz"], 3)
        score = 0

        for i, (question, correct_answer) in enumerate(questions, 1):
            print(f"\nQuestion {i}: {question}")
            answer = input("Your answer: ").strip().lower()

            if answer == correct_answer.lower():
                print("Correct!")
                score += 1
            else:
                print("Wrong!")
                print("Correct answer:", correct_answer)

        print("\nYour Score:", score, "/ 3")
        scores[choice] = score

    elif choice == "4":
        print("\n========== SCORE SUMMARY ==========")
        print("Student Name:", name)

        total_score = 0
        completed = 0

        for period, label in [
            ("1", "Prelim"),
            ("2", "Midterm"),
            ("3", "Finals")
        ]:
            if scores[period] is not None:
                print(label + ":", scores[period], "/ 3")
                total_score += scores[period]
                completed += 1
            else:
                print(label + ": Not yet taken")

        print("----------------------------------")
        print("Total Score:", total_score, "/", completed * 3)

        if completed == 3:
            percentage = (total_score / 9) * 100
            print("Overall Percentage:", round(percentage, 2), "%")

    elif choice == "5":
        print("\nThank you for using the study review program!")
        break

    else:
        print("\nInvalid choice! Please try again.")