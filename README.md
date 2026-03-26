# ATM-BS
# ATM Banking System

# Initial Data
balance = 10000
correct_pin = "1234"

# Function for authentication
def authenticate():
    attempts = 3
    while attempts > 0:
        pin = input("Enter your PIN: ")
        if pin == correct_pin:
            print(" Login Successful!\n")
            return True
        else:
            attempts -= 1
            print(f" Incorrect PIN! Attempts left: {attempts}")
    print(" Too many failed attempts. Card blocked!")
    return False

# Function to check balance
def check_balance():
    print(f" Your current balance is: ₹{balance}")

# Function to deposit money
def deposit():
    global balance
    amount = float(input("Enter amount to deposit: ₹"))
    if amount > 0:
        balance += amount
        print(f" ₹{amount} deposited successfully!")
    else:
        print(" Invalid amount!")

# Function to withdraw money
def withdraw():
    global balance
    amount = float(input("Enter amount to withdraw: ₹"))
    if amount <= 0:
        print(" Invalid amount!")
    elif amount > balance:
        print(" Insufficient balance!")
    else:
        balance -= amount
        print(f" ₹{amount} withdrawn successfully!")

# Main Program
if authenticate():
    while True:
        print("\n--- ATM MENU ---")
        print("1. Check Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            check_balance()
        elif choice == "2":
            deposit()
        elif choice == "3":
            withdraw()
        elif choice == "4":
            print(" Thank you for using ATM!")
            break
        else:
            print(" Invalid choice! Try again.")
