## XORing Code

```asm

section .text
    global _start

_start:
    mov eax, [var1]
    xor eax, eax
    mov [result], eax

    mov eax, 1
    int 0x80

section .bss
result resd 1

section .data
var1 dd 25

```

## Test Code

```asm

section .text
        global _start

_start:
        mov eax, 8

        test eax, 1
        jz even

        mov eax, 'n'
        mov [result], eax
        mov eax, 1
        int 0x80

even:
        mov eax, 'y'
        mov [result], eax
        mov eax, 1
        int 0x80

section .bss
        result resb 1

```

## Challenges

One of the challenges was trying to set the register to zero. I thought about using mov eax, 0, but that requires and immediate value. But then I learned that doing xor eax, eax is much simpler and is shorter. It also demonstrates the purpose of XOR, which was one of the goals of the lab. ANother challenge I had was between using TEST and AND. TEST uses AND but it just doesn't save the results, which is better for my test function.

## Flowchart

<img width="210" height="899" alt="Logical Instructions" src="https://github.com/user-attachments/assets/9d65c9fc-5ace-4825-946c-79cdf4dac872" />
