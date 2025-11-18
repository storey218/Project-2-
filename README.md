# Project-2-
#!/usr/bin/env python3
"""
Budget Calculator Program
Calculates monthly budget for someone earning $3,000 with $1,000 rent
"""

def calculate_budget(monthly_income, categories, amounts):
    """
    Calculate and display budget breakdown with remaining balance.
    
    Parameters:
    - monthly_income: Total monthly income
    - categories: List of expense category names (parallel array)
    - amounts: List of expense amounts corresponding to categories (parallel array)
    
    Returns:
    - remaining_balance: Amount left after all expenses
    """
    print("=" * 50)
    print("MONTHLY BUDGET CALCULATOR")
    print("=" * 50)
    print(f"\nMonthly Income: ${monthly_income:,.2f}")
    print("\nExpense Breakdown:")
    print("-" * 50)
    
    total_expenses = 0
    
    # Nested loop: outer loop for categories, inner loop for formatting display
    for i in range(len(categories)):
        category = categories[i]
        amount = amounts[i]
        
        # Inner loop: create visual bar representation
        bar_length = int((amount / monthly_income) * 40)
        bar = ""
        for j in range(bar_length):
            bar += "█"
        
        print(f"{category:.<20} ${amount:>8,.2f}  {bar}")
        total_expenses += amount
    
    print("-" * 50)
    print(f"{'Total Expenses':.<20} ${total_expenses:>8,.2f}")
    
    remaining_balance = monthly_income - total_expenses
    print(f"{'Remaining Balance':.<20} ${remaining_balance:>8,.2f}")
    
    # Calculate percentage of income remaining
    percentage_remaining = (remaining_balance / monthly_income) * 100
    print(f"\nYou have {percentage_remaining:.1f}% of your income remaining.")
    
    if remaining_balance < 0:
        print("⚠️  WARNING: You are over budget!")
    elif remaining_balance < monthly_income * 0.1:
        print("⚠️  CAUTION: Low savings margin!")
    else:
        print("✓ Good job! You have a healthy savings buffer.")
    
    print("=" * 50)
    
    return remaining_balance


def main():
    # Monthly income
    monthly_income = 3000
    
    # Parallel arrays: categories and their corresponding amounts
    expense_categories = [
        "Rent",
        "Utilities",
        "Groceries",
        "Transportation",
        "Insurance",
        "Entertainment",
        "Savings"
    ]
    
    expense_amounts = [
        1000,  # Rent
        150,   # Utilities
        400,   # Groceries
        200,   # Transportation
        150,   # Insurance
        100,   # Entertainment
        500    # Savings
    ]
    
    # Call the budget calculation function
    remaining = calculate_budget(monthly_income, expense_categories, expense_amounts)
    
    # Additional summary
    print(f"\n💡 TIP: Consider setting aside ${remaining:.2f} for emergencies.")


if __name__ == "__main__":
    main()
 for Project 2 
