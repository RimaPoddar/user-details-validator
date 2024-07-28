# user-details-validator

This project provides a simple Python program to validate user details during registration for a web application. The program includes functions to validate the user's name, phone number, and email ID. The main function `validate_all` invokes these functions to validate the inputs and displays appropriate messages.

## Features

- Validate user name:
  - Name should not be empty
  - Name should contain only alphabets
  - Name should not exceed 15 characters
- Validate phone number:
  - Phone number should have exactly 10 digits
  - Phone number should not contain any characters or special characters
  - All digits of the phone number should not be the same
- Validate email ID:
  - Email ID should contain one '@' character
  - Email ID should end with '.com'
  - Domain name should be either 'gmail', 'yahoo', or 'hotmail'

## Usage

### Function Definitions

- `validate_name(name)`: Validates the user name based on the specified criteria.
- `validate_phone_no(phone_no)`: Validates the phone number based on the specified criteria.
- `validate_email_id(email_id)`: Validates the email ID based on the specified criteria.
- `validate_all(name, phone_no, email_id)`: Invokes the appropriate validation functions and displays appropriate messages.

### Example Usage

```python
def validate_name(name):
    # Check if the name is not empty, contains only alphabets, and does not exceed 15 characters
    if name and name.isalpha() and len(name) <= 15:
        return True
    return False

def validate_phone_no(phone_no):
    # Check if the phone number is exactly 10 digits, contains only digits, and all digits are not the same
    if phone_no.isdigit() and len(phone_no) == 10 and len(set(phone_no)) > 1:
        return True
    return False

def validate_email_id(email_id):
    # Check if the email ID contains '@' and ends with '.com', and the domain name is either 'gmail', 'yahoo', or 'hotmail'
    if '@' in email_id and email_id.endswith('.com'):
        domain = email_id.split('@')[1].split('.')[0]
        if domain in ['gmail', 'yahoo', 'hotmail']:
            return True
    return False

def validate_all(name, phone_no, email_id):
    # Validate name, phone number, and email ID using the respective functions
    if not validate_name(name):
        print("Invalid name. Name should not be empty, should contain only alphabets, and should not exceed 15 characters.")
    elif not validate_phone_no(phone_no):
        print("Invalid phone number. Phone number should be exactly 10 digits, should not contain any characters or special characters, and all digits should not be the same.")
    elif not validate_email_id(email_id):
        print("Invalid email ID. Email ID should contain one '@' character, end with '.com', and the domain name should be either 'gmail', 'yahoo', or 'hotmail'.")
    else:
        print("All details are valid.")
        return True
    
    return False

# Example usage:
name = "Alice"
phone_no = "1234567890"
email_id = "alice@gmail.com"

validate_all(name, phone_no, email_id)
