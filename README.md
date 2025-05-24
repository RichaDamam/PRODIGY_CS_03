# PRODIGY_CS_03
import re

def check_password_strength(password):
    length_error = len(password) < 8
    lowercase_error = re.search(r"[a-z]", password) is None
    uppercase_error = re.search(r"[A-Z]", password) is None
    digit_error = re.search(r"\d", password) is None
    special_char_error = re.search(r"[!@#$%^&*(),.?\":{}|<>]", password) is None

    # Total score (the more satisfied conditions, the better)
    score = 5 - sum([length_error, lowercase_error, uppercase_error, digit_error, special_char_error])

    # Feedback messages
    if score == 5:
        feedback = "✅ Excellent! Your password is very strong."
    elif score == 4:
        feedback = "👍 Good! Your password is strong, but could be slightly improved."
    elif score == 3:
        feedback = "⚠️ Fair. Try adding more complexity (uppercase, digits, or special characters)."
    elif score == 2:
        feedback = "❌ Weak. Consider using a longer password with a mix of characters."
    else:
        feedback = "❌ Very weak. Use at least 8 characters with upper/lowercase, digits, and special symbols."

    # Print feedback with breakdown
    print(f"\nPassword: {password}")
    print(f"Strength Score: {score}/5")
    print("Issues:")
    if length_error: print(" - Password is too short.")
    if lowercase_error: print(" - Add at least one lowercase letter.")
    if uppercase_error: print(" - Add at least one uppercase letter.")
    if digit_error: print(" - Include at least one number.")
    if special_char_error: print(" - Add at least one special character.")
    print(f"\nFeedback: {feedback}")

# Example usage
user_input = input("Enter your password to check its strength: ")
check_password_strength(user_input)
