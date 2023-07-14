def has_lower_case(password):
    for char in password:
        if char.islower():
            return True
    return False

def has_upper_case(password):
    for char in password:
        if char.isupper():
            return True
    return False

def has_digit(password):
    for char in password:
        if char.isdigit():
            return True
    return False

def has_special_char(password):
    special_chars = "!@#$%^&*(),.?\":{}|<>"
    for char in password:
        if char in special_chars:
            return True
    return False

def classify_password(password):
    length = len(password)

    has_lower = has_lower_case(password)
    has_upper = has_upper_case(password)
    has_digit_char = has_digit(password)
    has_special = has_special_char(password)

    if length < 8 or not (has_lower and has_upper and has_digit_char and has_special):
        return "Weak"
    elif length >= 8 and length < 12 and ((has_lower and has_upper) or (has_lower and has_digit_char) or
                                          (has_lower and has_special) or (has_upper and has_digit_char) or
                                          (has_upper and has_special) or (has_digit_char and has_special)):
        return "Medium"
    else:
        return "Strong"

password = input("Enter the password: ")
password_strength = classify_password(password)
print("Password strength:", password_strength)
