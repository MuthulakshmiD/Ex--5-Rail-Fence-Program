# Ex--5-Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM

Name: Muthulakshmi D
Reg : 212223040122
```
def rail_fence_encrypt(message, rails):
    len_msg = len(message)
    code = [['\n'] * len_msg for _ in range(rails)]  # Initialize grid with newlines
    
    row, direction = 0, 1  # Start at row 0, moving downward
    for j in range(len_msg):
        code[row][j] = message[j]
        row += direction
        if row == rails - 1 or row == 0:
            direction *= -1  # Change direction at top or bottom

    encrypted_text = ''.join(code[i][j] for i in range(rails) for j in range(len_msg) if code[i][j] != '\n')
    return encrypted_text

def rail_fence_decrypt(encrypted_text, rails):
    len_msg = len(encrypted_text)
    code = [['\n'] * len_msg for _ in range(rails)]
    
    # Mark the zigzag pattern positions
    row, direction = 0, 1
    for j in range(len_msg):
        code[row][j] = '*'
        row += direction
        if row == rails - 1 or row == 0:
            direction *= -1

    # Fill the pattern with the actual encrypted characters
    index = 0
    for i in range(rails):
        for j in range(len_msg):
            if code[i][j] == '*' and index < len_msg:
                code[i][j] = encrypted_text[index]
                index += 1

    # Read the message in a zigzag pattern
    row, direction = 0, 1
    decrypted_text = []
    for j in range(len_msg):
        decrypted_text.append(code[row][j])
        row += direction
        if row == rails - 1 or row == 0:
            direction *= -1

    return ''.join(decrypted_text)

# Input from user
message = input("Enter a Secret Message: ")
rails = int(input("\nEnter number of rails: "))

# Encrypt and Decrypt
encrypted_message = rail_fence_encrypt(message, rails)
decrypted_message = rail_fence_decrypt(encrypted_message, rails)

# Output results
print("\nEncrypted Message:", encrypted_message)
print("\nDecrypted Message:", decrypted_message)
```

# OUTPUT
![424299145-a02281ad-b611-4788-a193-148b9143c20c](https://github.com/user-attachments/assets/2bfceb74-4f55-4cb6-a37e-f52ffea7d822)

# RESULT
  The program is executed successfully
