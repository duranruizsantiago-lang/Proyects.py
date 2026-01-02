Project Description (English)
ATM Cashup System - Python Implementation This script simulates a secure Automated Teller Machine (ATM) interface. It features a robust multi-stage validation process:

Identity & Residency Verification: Validates that names and locations do not contain numeric characters.

Age Restraint: Implements a strict security filter that denies access to users under 18.

Security Layer: Includes a mandatory 4-digit PIN creation and verification system for financial transactions.

Financial Operations: Supports real-time balance updates for deposits and withdrawals, including minimum withdrawal limits and overdraft protection.

Personalized UX: Uses string parsing to address the user by their first name for a more intuitive experience.




    





    


    
   
    
    
    
    
 

try:
    print("---- ATM Cashup User Registration ----")
    full_name = input("Enter your full name: ")
       
    if not full_name.replace(" ", "").isalpha():
        print("Error: The name cannot contain numbers.")
    else:
        # Extract only the first name for a personalized experience
        first_name = full_name.split()[0]
        
        age = int(input("Enter your age: "))
        
        if age < 18:
            print(f"ACCESS DENIED: We are sorry {first_name}, you must be 18 or older.")
        else:
            city = input("What is your fiscal residence (City)?: ")
            
            if not city.replace(" ", "").isalpha():
                print("Error: The city name cannot contain numbers.")
            else:
                # --- SECURITY PIN CREATION ---
                while True:
                    pin = input("Create your 4-digit security PIN: ")
                    if len(pin) == 4 and pin.isdigit():
                        print("PIN saved successfully.")
                        break
                    else:
                        print("Error: The PIN must be exactly 4 digits.")

                print(f"\nWelcome {first_name}! Access verified in {city}.")
                
                balance = 1000
                min_withdrawal = 20
                
                while True:
                    print("\n====================")
                    print(f"AVAILABLE BALANCE: ${balance}")
                    print("====================")
                    print("1. Deposit money")
                    print("2. Withdraw money")
                    print("3. Exit")

                    option = input(f"{first_name}, select an option: ")

                    if option == "1":
                        try:
                            deposit = int(input("How much do you want to deposit?: "))
                            if deposit > 0:
                                balance += deposit
                                print(f"Deposit successful. New balance: ${balance}")
                            else:
                                print("Error: The amount must be greater than 0.")
                        except ValueError:
                            print("Error: Please enter a valid number.")

                    elif option == "2":
                        confirm_pin = input("Enter your PIN to authorize the withdrawal: ")
                        if confirm_pin == pin:
                            try:
                                withdrawal = int(input(f"How much to withdraw (minimum ${min_withdrawal})?: "))
                                if withdrawal < min_withdrawal:
                                    print(f"Error: The minimum withdrawal is ${min_withdrawal}.")
                                elif withdrawal > balance:
                                    print("Error: Insufficient funds.")
                                else:
                                    balance -= withdrawal
                                    print(f"\nWithdrawal successful, {first_name}.")
                                    print(f"REMAINING BALANCE: ${balance}")
                            except ValueError:
                                print("Error: Please enter only whole numbers.")
                        else:
                            print("Incorrect PIN. Transaction cancelled.")

                    elif option == "3" or option.lower() == "exit":
                        print(f"Thank you for using ATM Cashup, {first_name}. GOODBYE!")
                        break
                    
                    else:
                        print("Invalid option, please try again.")

except ValueError:
    print("Error: Please enter only numeric values for age.")
   
