
# PRODIGY_PIT-JUN24-01374_TASKNO.01
# Cyber Security Internship
def caesar_cipher(text, shift, mode):
    result = ""
    for char in text:
        if char.isalpha():
            # Determine the offset based on the mode (encrypt or decrypt)
            if mode == 'encrypt':
                offset = shift
            elif mode == 'decrypt':
                offset = -shift
            # Apply the shift to the character
            if char.islower():
                result += chr((ord(char) - ord('a') + offset) % 26 + ord('a'))
            else:
                result += chr((ord(char) - ord('A') + offset) % 26 + ord('A'))
        else:
            result += char
    return result

def main():
    while True:
        choice = input("Do you want to encrypt or decrypt? (encrypt/decrypt): ").lower()
        if choice not in ['encrypt', 'decrypt']:
            print("Invalid choice. Please enter 'encrypt' or 'decrypt'.")
            continue
        message = input("Enter your message: ")
        shift = int(input("Enter the shift value (an integer between 1 and 25): "))
        if shift < 1 or shift > 25:
            print("Shift value must be between 1 and 25.")
            continue
        if choice == 'encrypt':
            encrypted_message = caesar_cipher(message, shift, 'encrypt')
            print("Encrypted message:", encrypted_message)
        else:
            decrypted_message = caesar_cipher(message, shift, 'decrypt')
            print("Decrypted message:", decrypted_message)

        another = input("Do you want to perform another operation? (yes/no): ").lower()
        if another != 'yes':
            break

if _name_ == "_main_":
    main()
