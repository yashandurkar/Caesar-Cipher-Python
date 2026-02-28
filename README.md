# Caesar-Cipher-Python
Task 01 - Caesar Cipher Implementation using Python
#Name - Yash Andurkar 

# This program performs basic encryption and decryption
# using the Caesar Cipher technique.


def encrypt_message(message, shift_value):
    result = ""

    for ch in message:
        # Check if character is alphabet
        if ch.isalpha():
            # Decide ASCII base depending on case
            if ch.isupper():
                base = ord('A')
            else:
                base = ord('a')

            # Shift character and wrap using modulo
            new_char = chr((ord(ch) - base + shift_value) % 26 + base)
            result += new_char
        else:
            # If not alphabet, keep it same
            result += ch

    return result


def decrypt_message(message, shift_value):
    # For decryption we shift in opposite direction
    return encrypt_message(message, -shift_value)


print("------ Caesar Cipher Program ------")

while True:
    print("\nChoose an option:")
    print("1. Encrypt")
    print("2. Decrypt")
    print("3. Exit")

    user_choice = input("Enter your choice (1/2/3): ")

    if user_choice == "1":
        text = input("Enter text to encrypt: ")

        try:
            shift = int(input("Enter shift value: "))
        except ValueError:
            print("Please enter a valid number.")
            continue

        encrypted_text = encrypt_message(text, shift)
        print("Encrypted Text:", encrypted_text)

    elif user_choice == "2":
        text = input("Enter text to decrypt: ")

        try:
            shift = int(input("Enter shift value: "))
        except ValueError:
            print("Please enter a valid number.")
            continue

        decrypted_text = decrypt_message(text, shift)
        print("Decrypted Text:", decrypted_text)

    elif user_choice == "3":
        print("Program ended.")
        break

    else:
        print("Invalid option. Try again.")
