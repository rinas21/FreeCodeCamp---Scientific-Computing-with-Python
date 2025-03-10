def arithmetic_arranger(problems, show_answers=False):
    if len(problems) > 5:
        return "Error: Too many problems."

    first_line = ""
    second_line = ""
    dashes_line = ""
    results_line = ""

    for problem in problems:
        split = problem.split()
        num1 = split[0]
        operator = split[1]
        num2 = split[2]

        # Validate operator
        if operator not in ('+', '-'):
            return "Error: Operator must be '+' or '-'."

        # Validate numbers
        if not num1.isdigit() or not num2.isdigit():
            return "Error: Numbers must only contain digits."

        if len(num1) > 4 or len(num2) > 4:
            return "Error: Numbers cannot be more than four digits."

        # Perform calculation
        if operator == '+':
            answer = int(num1) + int(num2)
        else:
            answer = int(num1) - int(num2)

        # Formatting
        width = max(len(num1), len(num2)) + 2
        first_line += num1.rjust(width) + "    "
        second_line += operator + num2.rjust(width - 1) + "    "
        dashes_line += "-" * width + "    "
        results_line += str(answer).rjust(width) + "    "

    # Construct output
    if show_answers:
        return f"{first_line.rstrip()}\n{second_line.rstrip()}\n{dashes_line.rstrip()}\n{results_line.rstrip()}"
    else:
        return f"{first_line.rstrip()}\n{second_line.rstrip()}\n{dashes_line.rstrip()}"

# Test case
print(arithmetic_arranger(["32 + 698", "3801 - 2", "45 + 43", "123 + 49"], True))

