tags: #exploiting #secure-coding
 
# Secure Coding

links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]

---

## Insecure Coding

- (Buffer Overflows)
- String handling mischief
- Integer overflows / underflows
- Information disclosure (unitialized memory, buffer overread)

## Insecure Functions

Functions which can create a buffer overflow:

- `gets(char *s)`
- `scanf(const char *format, ...)`
- `sprintf(char *str, const char *format, ...)`
- `strcat(char *dest, const char *src)`
- `strcpy(char *dest, const char *src)`

**Don't use functions which do not respect size of destination buffer**

## C Strings

![[secure-coding-1.png]]
![[secure-coding-2.png]]
![[secure-coding-3.png]]
![[secure-coding-4.png]]
![[secure-coding-5.png]]

## Integer overflow

A **signed integer** can be negative, halves the amount of numbers it can store

There are different weaknesses:

- **Unsigned Integer Wraparound**: This occurs when an arithmetic operation on an unsigned integer causes it to exceed its maximum value, wrapping around to start from zero again.
- **Signed Integer Overflow**: This happens when an arithmetic operation on a signed integer exceeds its maximum positive value or drops below its minimum negative value, causing it to wrap around and change its sign.
- **Numeric Truncation Error**: This occurs when a larger numeric value is assigned to a smaller variable type, causing the value to be truncated and lose its precision.

![[integer-overflow.png]]

---
links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]