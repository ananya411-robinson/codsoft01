# codsoft01
PASSWORD GENERATOR 
import random
import string

# Welcome message
print("Welcome to the Password Generator!")

# Ask the user to input the password length
try:
    pwd_len = int(input("Enter the desired password length: "))
    
    # Ensure the password length is valid
    if pwd_len < 4:
        print("Password length must be at least 4 characters.")
    else:
        # Character groups
        small_letters = string.ascii_lowercase  # Lowercase letters
        big_letters = string.ascii_uppercase    # Uppercase letters
        num_chars = string.digits              # Numbers (0-9)
        special_symbols = "!@#$%^&*()_+-=[]{}|;:,.<>?/"

        # Start with one character from each group
        temp_pwd = [
            random.choice(small_letters),  # Add one lowercase letter
            random.choice(big_letters),   # Add one uppercase letter
            random.choice(num_chars),     # Add one number
            random.choice(special_symbols)  # Add one special character
        ]

        # Fill the rest of the password with random characters
        all_chars = small_letters + big_letters + num_chars + special_symbols
        temp_pwd += random.choices(all_chars, k=pwd_len - 4)

        # Shuffle the password to make it secure
        random.shuffle(temp_pwd)

        # Combine the list into a single string and display it
        final_pwd = ''.join(temp_pwd)
        print("Your generated password is:", final_pwd)
except ValueError:
    # Handle invalid input
    print("Invalid input. Please enter a valid number.")
