## Code

```asm

SECTION .data
  filename db "quotes.txt",0

  quote1 db "To be, or not to be, that is the question.",10
  quote1Len equ $-quote1
  quote2 db "A fool thinks himself to be wise, but a wise man knows himself to be a fool.",10
  quote2Len equ $-quote2

  quote3 db "Better three hours too soon than a minute too late.",10
  quote3Len equ $-quote3
  quote4 db "No legacy is so rich as honesty.",10
  quote4Len equ $-quote4

SECTION .bss
  fd_out resd 1

SECTION .text
  global _start

_start:
  mov eax, 5
  mov ebx, filename
  mov ecx, 0101o
  mov edx, 0777o
  int 0x80

  mov [fd_out], eax

  mov eax, 4
  mov ebx, [fd_out]
  mov ecx, quote1
  mov edx, quote1Len
  int 0x80

  mov eax, 4
  mov ebx, [fd_out]
  mov ecx, quote2
  mov edx, quote2Len
  int 0x80

  mov eax, 19
  ov ebx, [fd_out]
  mov ecx, 0
  mov edx, 2
  int 0x80

  mov eax, 4
  mov ebx, [fd_out]
  mov ecx, quote3
  mov edx, quote3Len
  int 0x80

  mov eax, 4
  mov ebx, [fd_out]
  mov ecx, quote4
  mov edx, quote4Len
  int 0x80

  mov eax, 6
  mov ebx, [fd_out]
  int 0x80

  mov eax, 1
  mov ebx, 0
  int 0x80

```

## Challenges
One of the challenges I had with this code was using the right file flags. I noticed that if I had even 1 number different, the code would cause an error. I had to make sure from the lecture notes to use the right file flags.
Another challenge was definitely appending the new quotes in the file. I had to make sure the file pointer was moved to the end of the file before putting in the new quotes, which took me some time to figure out.
