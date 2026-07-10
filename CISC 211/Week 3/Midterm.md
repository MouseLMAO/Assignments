## Question 1 Code

```asm
; Equation: result = (var1 + 2) / (var3 - var2)
; var1 = 19, var2 = 3, var3 = 8
; result = (19 + 2) / (8 - 3) = 21 / 5 = 4
; quotient = 4, remainder = 1

section .text
    global _start

_start:
    ; Calculate the numerator: var1 + 2
    mov eax, [var1]
    add eax, 2

    ; Prepare EDX:EAX for signed division
    cdq

    ; Calculate the denominator: var3 - var2
    mov ebx, [var3]
    sub ebx, [var2]

    ; Divide 21 by 5
    idiv ebx               ; EAX = quotient, EDX = remainder

    mov [result], eax

    ; Convert result from integer to ASCII
    add al, 48
    mov [output], al

    ; Display the result
    mov eax, 4
    mov ebx, 1
    mov ecx, output
    mov edx, 1
    int 0x80

    ; Display a newline
    mov eax, 4
    mov ebx, 1
    mov ecx, newline
    mov edx, 1
    int 0x80

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    var1    dd 19
    var2    dd 3
    var3    dd 8
    newline db 10

section .bss
    result  resd 1
    output  resb 1
```

## Question 1 gdb

<img width="893" height="675" alt="Screenshot 2026-07-11 at 3 38 59 AM" src="https://github.com/user-attachments/assets/09dca063-46db-4205-9186-9426d2136c60" />

## Question 2

ab: a=1, b=1\
a'b: a=0, b=1\
ab′: a=1, b=0\
    a/b    0    1\
    0      0    1\
    1      0    1

a'b + ab = b
ab' + ab = a

Solution: Y = a + b\

## Question 3 Code

```asm
section .text
    global _start

_start:
    ; Load the number into EAX
    mov eax, [number]

    ; Check the least significant bit, if last bit is 0, it's even, if last bit is 1, it's odd
    test eax, 1

    ; Jump to evenNumber if the Zero Flag is set
    jz evenNumber

oddNumber:
    ; Display "odd number"
    mov eax, 4
    mov ebx, 1
    mov ecx, oddMessage
    mov edx, 11
    int 0x80

    ; Skip the even-number section
    jmp exitProgram

evenNumber:
    ; Display "even number"
    mov eax, 4
    mov ebx, 1
    mov ecx, evenMessage
    mov edx, 12
    int 0x80

exitProgram:
    ; Exit the program
    mov eax, 1
    mov ebx, 0
    int 0x80

section .data
    number      dd 7
    oddMessage  db "odd number", 10
    evenMessage db "even number", 10

```

## Question 3 Design

Can't use AND or OR, so have to use TEST
A binary number is even if last bit is 0, odd if last bit is 1.

First loaded numbers into EAX
Tested with EAX,1
If the zero flag was set, make it display "even number"
If the zero flag wasn't set, make it display "odd number"
Finish Code
