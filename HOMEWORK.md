# 1.Number System Conversions

## a. Binary to Decimal

To convert a binary number to decimal (base 10), use the formula:

Decimal = b_n × 2^n + b_(n-1) × 2^(n-1) + … + b_1 × 2^1 + b_0 × 2^0

For example, converting `(1010)_2` to decimal:
1 × 2^3 + 0 × 2^2 + 1 × 2^1 + 0 × 2^0 = 8 + 0 + 2 + 0 = 10
So, `(1010)_2 = (10)_{10}`.

## b. Octal to Binary

To convert from octal (base 8) to binary (base 2):
Convert each digit to its 3-bit binary equivalent and combine:
(237)_8 = (010 011 111)_2 = (10011111)_2


## c. Base 9 to Decimal
To convert from base 9 to decimal (base 10):
5 × 9^2 + 3 × 9^1 + 5 × 9^0 = 5 × 81 + 3 × 9 + 5 × 1 = 405 + 27 + 5 = 437
So, `(535)_9 = (437)_{10}`.

# 2.Logarithm Properties

## Product Rule
log_b(x ⋅ y) = log_b(x) + log_b(y)

## Quotient Rule
log_b(x / y) = log_b(x) − log_b(y)


## Power Rule
log_b(x^c) = c ⋅ log_b(x)


## Change of Base Rule
log_b(x) = log_k(x) / log_k(b)


## Log of 1
log_b(1) = 0

## Log of the Base
log_b(b) = 1

# 3. 1's Complement and 2's Complement

## 1's Complement
Invert all bits of a binary number.
Example: The 1's complement of `1010` is `0101`.

## 2's Complement
Invert all bits and add 1 to the least significant bit (LSB).
Example: The 2's complement of `1010` is `0101 + 1 = 0110`.

# 4.Power of 2 Code Implementation

To check if a number `N` is a power of 2:

```python
def is_power_of_2(n: int) -> bool:
    return n > 0 and (n & (n - 1)) == 0

## 5.Representing Positive and Negative Numbers
Positive Numbers: Represented directly in binary.
Negative Numbers: Represented using 2's complement.

# 6. Binary Addition and Subtraction
Addition: Follow the same rules as decimal addition. If a sum exceeds 1, carry 1 to the next column.
Subtraction: Take the 2's complement of the subtrahend and add it to the minuend.

# 7.Operator Precedence Table
Operator Type	Operators	Associativity
Parentheses	()	Left-to-right
Unary	+, -, ~, !	Right-to-left
Multiplicative	*, /, %	Left-to-right
Additive	+, -	Left-to-right
Shift	<<, >>	Left-to-right
Relational	<, <=, >, >=	Left-to-right
Equality	==, !=	Left-to-right
Bitwise AND	&	Left-to-right
Bitwise XOR	^	Left-to-right
Bitwise OR	`	`
Logical AND	&&	Left-to-right
Logical OR	`	
Assignment	=, +=, -=, etc.	Right-to-left

# 8.Leading and Trailing Zeroes
Leading Zeroes: Zeros before the first non-zero digit.
Trailing Zeroes: Zeros after the last non-zero digit.

# 9 .Significant Zeroes
Significant Zeroes: Zeros between non-zero digits or after a non-zero digit in decimal places.

# 10 . Bit Masking
Bit masking is used to manipulate individual bits of a number using bitwise operations (AND, OR, XOR, etc.).

#  11 .Code Implementations

## a. How Many Set Bits Are There

```python
def count_set_bits(n: int) -> int:
    count = 0
    while n:
        n &= (n - 1)  
        count += 1
    return count

## b. Check if the ith Bit is Set or Not

    def is_ith_bit_set(n: int, i: int) -> bool:
    return (n & (1 << i)) != 0
## c. Set the ith Bit

    def set_ith_bit(n: int, i: int) -> int:
    return n | (1 << i)

## d. UnSet the ith Bit

def unset_ith_bit(n: int, i: int) -> int:
    return n & ~(1 << i)

## e .Generate All Possible Subsets of Array
from typing import List
def generate_subsets(nums: List[int]) -> List[List[int]]:
    subsets = []
    n = len(nums)
    for i in range(1 << n):  # 2^n subsets
        subset = [nums[j] for j in range(n) if i & (1 << j)]
        subsets.append(subset)
    return subsets
## f. Swapping Two Numbers

def swap(a: int, b: int) -> (int, int):
    a = a ^ b
    b = a ^ b
    a = a ^ b
    return a, b
## g. Odd or Even
def is_odd(n: int) -> bool:
    return (n & 1) == 1

## h. Upper to Lower Case and Related Problems
def to_lower_case(char: str) -> str:
    return chr(ord(char) | 32) if 'A' <= char <= 'Z' else char

def to_upper_case(char: str) -> str:
    return chr(ord(char) & ~32) if 'a' <= char <= 'z' else char

## i. Toggle the Bit
def toggle_bit(n: int, i: int) -> int:
    return n ^ (1 << i)








