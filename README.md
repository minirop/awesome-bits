# awesome-bits
A curated list of awesome bitwise operations and tricks

## Integers
**Set n-th bit**
```
x | (1<<n)
```
**Unset n-th bit**
 ```
 x & ~(1<<n)
 ```
**Toggle n-th bit**
```
x ^ (1<<n)
```
**Get the maximum integer**
```
int maxInt = ~(1 << 31);
int maxInt = (1 << 31) - 1;
int maxInt = (1 << -1) - 1;
```
**Get the minimum integer**
```
int minInt = 1 << 31;
int minInt = 1 << -1;
```
**Get the maximum long**
```
long maxLong = ((long)1 << 127) - 1;
```
**Multiplied by 2**
```
n << 1; // n*2
```
**Divided by 2**
```
n >> 1; // n/2
```
**Multiplied by the m-th power of 2**
```
n << m;
```
**Divided by the m-th power of 2**
```
n >> m;
```
**Check odd number**
```
(n & 1) == 1;
```
**Exchange two values**
```
a ^= b;
b ^= a;
a ^= b;
```
**Get absolute value**
```
(n ^ (n >> 31)) - (n >> 31);
```
**Get the max of two values**
```
b & ((a-b) >> 31) | a & (~(a-b) >> 31);
```
**Get the min of two values**
```
a & ((a-b) >> 31) | b & (~(a-b) >> 31);
```
**Check whether both have the same sign**
```
(x ^ y) >= 0;
```
**Calculate 2^n**
```
2 << (n-1);
```
**Whether is factorial of 2**
```
n > 0 ? (n & (n - 1)) == 0 : false;
```
**Modulo 2^n against m**
```
m & (n - 1);
```
**Get the average**
```
(x + y) >> 1;
((x ^ y) >> 1) + (x & y);
```
**Get the m-th bit of n (from low to high)**
```
(n >> (m-1)) & 1;
```
**Set the m-th bit of n to 0 (from low to high)**
```
n & ~(1 << (m-1));
```
**Check if n-th bit is set**
```
if (x & (1<<n)) {
  n-th bit is set
}
else {
  n-th bit is not set
}
```
**Isolate (extract) the right most 1 bit**
```
x & (-x)
```
**Isolate (extract) the right most 0 bit**
```
~x & (x+1)
```

**Right most 0 bit to 1**
```
x | (x+1)
```

**n + 1**
```
-~n
```
**n - 1**
```
~-n
```
**Get the contrast number**
```
~n + 1;
(n ^ -1) + 1; 
```
**if (x==a) x=b; if (x==b) x=a;**
```
x = a ^ b ^ x;
```

## Strings

**Convert letter to lowercase:**
```
OR by space => (x | ' ')
Result is always lowercase even if letter is already lowercase
eg. ('a' | ' ') => 'a' ; ('A' | ' ') => 'a'
```

**Convert letter to uppercase:**
```
AND by underline => (x & '_')
Result is always uppercase even if letter is already uppercase
eg. ('a' & '_') => 'A' ; ('A' & '_') => 'A'
```
**Invert letter's case:**
```
XOR by space => (x ^ ' ')
eg. ('a' ^ ' ') => 'A' ; ('A' ^ ' ') => 'a'
```
**Letter's position in alphabet:**
```
AND by chr(31)/binary('11111')/(hex('1F') => (x & "\x1F")
Result is in 1..26 range, letter case is not important
eg. ('a' & "\x1F") => 1 ; ('B' & "\x1F") => 2
```
**Get letter's position in alphabet (for Uppercase letters only):**
```
AND by ? => (x & '?') or XOR by @ => (x ^ '@')
eg. ('C' & '?') => 3 ; ('Z' ^ '@') => 26
```
**Get letter's position in alphabet (for lowercase letters only):**
```
XOR by backtick/chr(96)/binary('1100000')/hex('60') => (x ^ '`')
eg. ('d' ^ '`') => 4 ; ('x' ^ '`') => 25
```

Note: using anything other than the english letters will produce garbage results

For more Complicated Stuffs [Read This](https://graphics.stanford.edu/~seander/bithacks.html)
