# TASK-3-Password-generators
import random
import string


def generate_password(length):
    if length < 6:
        print("Password length should be at least 6 characters for security purposes.")
        return None

    # Define the character sets
    lower_case = string.ascii_lowercase
    upper_case = string.ascii_uppercase
    digits = string.digits
    special_characters = string.punctuation

    # Combine all character sets
    all_characters = lower_case + upper_case + digits + special_characters

    # Ensure password contains at least one character from each category (lowercase, uppercase, digits, special chars)
    password = [
        random.choice(lower_case),
        random.choice(upper_case),
        random.choice(digits),
        random.choice(special_characters)
    ]

    # Fill the remaining length with random characters
    password += random.choices(all_characters, k=length - 4)

    # Shuffle the password to ensure randomness
    random.shuffle(password)

    # Join the list to form the final password
    return ''.join(password)


def main():
    print("Password Generator")

    # Get the desired password length from the user
    while True:
        try:
            length = int(input("Enter the desired password length (at least 6 characters): "))
            if length >= 6:
                break
            else:
                print("Password length must be at least 6 characters. Please try again.")
        except ValueError:
            print("Invalid input! Please enter a valid number.")

    # Generate and display the password
    password = generate_password(length)

    if password:
        print(f"Generated Password: {password}")


if __name__ == "__main__":
    main()
output:Password Generator
Enter the desired password length (at least 6 characters): 12
Generated Password: Ri/y4"UO0?c7
