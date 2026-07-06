## Equation 1 Code

```asm

section .text
    global _start

_start:
    mov eax, [var1]
    neg eax
    imul eax, 10
    mov [result], eax

    mov eax, 1
    int 0x80

section .bss
    result resd 1

section .data
    var1 dd 5

```

## Equation 2 Code

```asm

section .text
    global _start

_start:
    mov eax, [var1]
    add eax, [var2]
    add eax, [var3]
    add eax, [var4]
    mov [result], eax

    mov eax, 1
    int 0x80

section .bss
    result resd 1

section .data
    var1 dd 10
    var2 dd 15
    var3 dd 20
    var4 dd 25
```

## Equation 3 Code

```asm

section .text
    global _start

_start:
    mov eax, [var1]
    neg eax
    imul eax, [var2]
    add eax, [var3]
    mov [result], eax

    mov eax, 1
    int 0x80

section .bss
    result resd 1

section .data
    var1 dd 5
    var2 dd 4
    var3 dd 30
```

## Equation 4 Code

```asm

section .text
    global _start

_start:
    mov eax, [var1]
    imul eax, 2

    mov ebx, [var2]
    sub ebx, 3

    cdq
    idiv ebx

    mov [result], eax

    mov eax, 1
    int 0x80

section .bss
    result resd 1

section .data
    var1 dd 10
    var2 dd 5
```

## Challenges

One of the challenges I had was making sure I had cdq before dividing in the fourth equation so the 32 bit value that was in EAX is copies it into EDX, which would make it a 64-bit. This allows the processor to divide the values correctly, preventing error. Another Challenge I faced was differentiating between mul and imul. Since some equations had negtive numbers in it, it helped me to choose the correct one, imul.

## Flowchart

<img width="210" height="740" alt="Arithmetic instructions" src="https://github.com/user-attachments/assets/32c65876-1b73-4715-9eb4-6e2d6ee9d8c3" />
