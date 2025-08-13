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
### 5 rail
def rail_fence(text, rails, mode='encrypt'):
    fence = [[] for _ in range(rails)]
    rail, step = 0, 1

    for i in range(len(text)):
        fence[rail].append(i if mode == 'decrypt' else text[i])
        rail += step
        if rail == 0 or rail == rails - 1:
            step *= -1

    if mode == 'encrypt':
        return ''.join(''.join(row) for row in fence)

    # For decryption
    order = [i for row in fence for i in row]
    decrypted = [''] * len(text)
    for idx, i in enumerate(order):
        decrypted[i] = text[idx]
    return ''.join(decrypted)

msg = input("Enter a Secret Message: ")
r = int(input("Enter number of rails: "))

enc = rail_fence(msg, r, 'encrypt')
dec = rail_fence(enc, r, 'decrypt')

print("\nEncrypted Message:", enc)
print("Decrypted Message:", dec)

```

# OUTPUT
![424299145-a02281ad-b611-4788-a193-148b9143c20c](https://github.com/user-attachments/assets/2bfceb74-4f55-4cb6-a37e-f52ffea7d822)

# RESULT
  The program is executed successfully
