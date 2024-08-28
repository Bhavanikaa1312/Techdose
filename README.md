# Techdose 
Number System Conversions
a. Binary to Decimal
To convert a binary number to decimal (base 10), use the formula: 
Decimal
=
𝑏
𝑛
×
2
𝑛
+
𝑏
𝑛
−
1
×
2
𝑛
−
1
+
…
+
𝑏
1
×
2
1
+
𝑏
0
×
2
0
Decimal=b 
n
​
 ×2 
n
 +b 
n−1
​
 ×2 
n−1
 +…+b 
1
​
 ×2 
1
 +b 
0
​
 ×2 
0
 

For example, converting (1010)_2 to decimal: 
1
×
2
3
+
0
×
2
2
+
1
×
2
1
+
0
×
2
0
=
8
+
0
+
2
+
0
=
10
1×2 
3
 +0×2 
2
 +1×2 
1
 +0×2 
0
 =8+0+2+0=10 So, (1010)2 = (10){10}.

b. Octal to Binary
To convert from octal (base 8) to binary (base 2): Convert each digit to its 3-bit binary equivalent and combine: 
(
237
)
8
=
(
010
 
011
 
111
)
2
=
(
10011111
)
2
(237) 
8
​
 =(010 011 111) 
2
​
 =(10011111) 
2
​
 

c. Base 9 to Decimal
To convert from base 9 to decimal (base 10): 
5
×
9
2
+
3
×
9
1
+
5
×
9
0
=
405
+
27
+
5
=
437
5×9 
2
 +3×9 
1
 +5×9 
0
 =405+27+5=437 So, (535)9 = (437){10}.

Logarithm Properties
Product Rule: 
log
⁡
𝑏
(
𝑥
⋅
𝑦
)
=
log
⁡
𝑏
(
𝑥
)
+
log
⁡
𝑏
(
𝑦
)
log 
b
​
 (x⋅y)=log 
b
​
 (x)+log 
b
​
 (y)
Quotient Rule: 
log
⁡
𝑏
(
𝑥
/
𝑦
)
=
log
⁡
𝑏
(
𝑥
)
−
log
⁡
𝑏
(
𝑦
)
log 
b
​
 (x/y)=log 
b
​
 (x)−log 
b
​
 (y)
Power Rule: 
log
⁡
𝑏
(
𝑥
𝑐
)
=
𝑐
⋅
log
⁡
𝑏
(
𝑥
)
log 
b
​
 (x 
c
 )=c⋅log 
b
​
 (x)
Change of Base Rule: 
log
⁡
𝑏
(
𝑥
)
=
log
⁡
𝑘
(
𝑥
)
log
⁡
𝑘
(
𝑏
)
log 
b
​
 (x)= 
log 
k
​
 (b)
log 
k
​
 (x)
​
 
Log of 1: 
log
⁡
𝑏
(
1
)
=
0
log 
b
​
 (1)=0
Log of the Base: 
log
⁡
𝑏
(
𝑏
)
=
1
log 
b
​
 (b)=1
1's Complement and 2's Complement
1's Complement: Invert all bits of a binary number. Example: 1's complement of 1010 is 0101.
2's Complement: Invert all bits and add 1 to the least significant bit (LSB). Example: 2's complement of 1010 is 0101 + 1 = 0110.
Applications: Used to represent negative numbers in binary systems and simplifies binary subtraction.

Power of 2 Code Implementation
To check if a number 
𝑁
N is a power of 2:

python
Copy code
def is_power_of_2(n: int) -> bool:
    return n > 0 and (n & (n - 1)) == 0
Representing Positive and Negative Numbers
Positive Numbers: Represented directly in binary.
Negative Numbers: Represented using 2's complement.
Binary Addition and Subtraction
Addition: Follow the same rules as decimal addition. If a sum exceeds 1, carry 1 to the next column.
Subtraction: Take the 2's complement of the subtrahend and add it to the minuend.
Operator Precedence Table
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
Bitwise OR	|	Left-to-right
Logical AND	&&	Left-to-right
Logical OR	|	Left-to-right
Assignment	=, +=, -=, etc.	Right-to-left
Leading and Trailing Zeroes
Leading Zeroes: Zeros before the first non-zero digit.
Trailing Zeroes: Zeros after the last non-zero digit.
Significant Zeroes
Significant Zeroes: Zeros between non-zero digits or after a non-zero digit in decimal places.
Bit Masking
Bit masking is used to manipulate individual bits of a number using bitwise operations (AND, OR, XOR, etc.).

Code Implementations
a. How Many Set Bits Are There
python
Copy code
def count_set_bits(n: int) -> int:
    count = 0
    while n:
        n &= (n - 1)  # Remove the last set bit
        count += 1
    return count
b. Check if the ith Bit is Set or Not
python
Copy code
def is_ith_bit_set(n: int, i: int) -> bool:
    return (n & (1 << i)) != 0
c. Set the ith Bit
python
Copy code
def set_ith_bit(n: int, i: int) -> int:
    return n | (1 << i)
d. Unset the ith Bit
python
Copy code
def unset_ith_bit(n: int, i: int) -> int:
    return n & ~(1 << i)
e. Generate All Possible Subsets of Array
python
Copy code
from typing import List

def generate_subsets(nums: List[int]) -> List[List[int]]:
    subsets = []
    n = len(nums)
    for i in range(1 << n):  # 2^n subsets
        subset = [nums[j] for j in range(n) if i & (1 << j)]
        subsets.append(subset)
    return subsets
f. Swapping Two Numbers
python
Copy code
def swap(a: int, b: int) -> (int, int):
    a = a ^ b
    b = a ^ b
    a = a ^ b
    return a, b
g. Odd or Even
python
Copy code
def is_odd(n: int) -> bool:
    return (n & 1) == 1
h. Upper to Lower Case and Related Problems
python
Copy code
def to_lower_case(char: str) -> str:
    return chr(ord(char) | 32) if 'A' <= char <= 'Z' else char

def to_upper_case(char: str) -> str:
    return chr(ord(char) & ~32) if 'a' <= char <= 'z' else char
i. Toggle the Bit
python
Copy code
def toggle_bit(n: int, i: int) -> int:
    return n ^ (1 << i)