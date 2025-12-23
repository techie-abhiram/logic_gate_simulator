  import itertools
def universal_truth_table(variables_count, expression):
    # Create column headers (A, B, C, ...)
    headers = [chr(65 + i) for i in range(variables_count)]
    print(f"Truth Table for: {expression}")
    print(" | ".join(headers) + " | Output")
    print("-" * (len(headers) * 4 + 8))
    # Generate all combinations for N variables
    for values in itertools.product([0, 1], repeat=variables_count):
        # Create a local dictionary mapping 'A': value, 'B': value, etc.
        context = dict(zip(headers, values))
        try:
            # Evaluate the expression based on the context
            result = eval(expression, {}, context)
            # Ensure result is 0 or 1
            result = int(bool(result))
            row = " | ".join(map(str, values))
            print(f"{row} |   {result}")
        except Exception as e:
            print(f"Error in expression: {e}")
            break
# Examples to try:
# 3 Variables: (A AND B) OR C
universal_truth_table(3, "(A & B) | C")
