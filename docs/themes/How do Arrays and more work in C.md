tags: #c

# How do Arrays and more work in C

links: [[908 ED TOC - C Arrays|ED TOC - C Arrays]] - [[themes/000 Index|Index]]

---

**C Arrays & Pointers**

- Arrays in C are essentially pointers.
- Nothing is checked by the compiler. You can do whatever you want. There are no boundaries in C. 
- Example:
  ```c
  int array[5] = {1, 2, 3, 4, 5};
  array[0] = 0;
  array[4] = 0;
  ```
- Pointers can be used to manipulate array elements:
  ```c
  int *a = array;
  a[2] = 0;
  ```

**Copying Data**

- Strings in C are arrays of bytes.
- They are terminated by the 0 byte `\x00`
- Functions to copy strings:
  ```c
  strcpy(destination, source);
  memcpy(destination, source, len);
  gets(destination);
  ```
- Vulnerabilities arise when the destination buffer size is not considered, leading to buffer overflows.

**Exploitation Basics**

- Common vulnerability: Buffer overflow due to functions like `strcpy()` not considering the destination buffer size.
- `strncpy(destination, source, len)` does care about the length
- Example:
  ```c
  char destination[8];
  char source[16] = "1234567890123456\x00";
  strcpy(destination, source);
  ```

**Non-Arrays in C**

- C has basic types (int, float), enumerated types, void type, and derived types (pointers, arrays, structures, unions, functions).
- Arrays consist of multiple elements of the same type.
- Structures can hold multiple elements of different types.
- Example:
  ```c
  struct var {
      short x;
      long y;
      char z[3];
  }
  ```

**Conclusion**

- C does not enforce buffer boundaries, making it susceptible to buffer overflow attacks.
- `strcpy()` and similar functions do not check the size of the destination buffer, leading to potential overwrites of adjacent memory.
-  One buffer can overflow into another buffer
- Local variables/buffers are adjoin to each other
- Pointer can point to any memory address

---
links: [[908 ED TOC - C Arrays|ED TOC - C Arrays]] - [[themes/000 Index|Index]]