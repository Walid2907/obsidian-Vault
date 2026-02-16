
# AND operator (&):

## truth table
1 & 0 = 0
1 & 1 = 1
0 & 0 = 0
0 & 1 = 0

so the And return true only if <span style="color:rgb(192, 0, 0)">the two expressions</span> is true

# OR operator (|):

## truth table
1 | 0 = 1
1 | 1 = 1
0 | 0 = 0
0 | 1 = 1

so the OR return true if <span style="color:rgb(192, 0, 0)">at least</span> <span style="color:rgb(192, 0, 0)">one of the expressions</span> is true

# XOR operator (^):

## truth table
1 ^ 0 = 1
1 ^ 1 = 0
0 ^ 0 = 0
0 ^ 1 = 1

so the XOR returns true if only one of the expressions is true

# Left shift (<<):

the left shifting is used tho shift the bites of a byte to the left
## examples

a = 3  = 00000011
a << 1 = 00000110 = 6 = 3 * 2^1
a << 2 = 00001100 = 12 = 3 * 2^2
a << 3 = 00011000 = 24 = 3 * 2^3

Trick  left shifting is multiplying by 2 to the power of n (number of shifted bites)

# Right shift (>>):
the right shifting is used to shift the bites if a byte to the right

## examples

a = 3  = 00000011
a >> 1 = 00000001 = 1 = a / 2^1
a >> 2 = 00000000 = 0 = a / 2^2

b = 8  = 00001000
b >> 1 = 00000100 = 4 = b / 2^1
b >> 2 = 00000010 = 2 = b / 2^2
b >> 3 = 00000001 = 1 = b / 2^3
b >> 4 = 00000000 = 0 = b / 2^4

like left shifting but instead of multiplying we divide the number by 2 to the power of n  (number of shifted bites)




