## My Code

```asm
section .text
    global _start

_start:
    mov eax, [var1]
    add eax, [var2]
    mov [result], eax
    mov eax, 1
    int 0x80

segment .bss
result resd 1

segment .data
var1    dd 10
var2    dd 15

```

## Challenges

The greatest challenge was debugging my program to make sure it was running properly. It was the first time that I had used a debugger, so I had to watch the instructional video for a while. Another challenge I had was understanding that initialized variables are put in .data an uninitialized variables that receive values later from the user input is put in .bss.

## Flowchart

<img width="190" height="589" alt="Variables and constants" src="https://github.com/user-attachments/assets/d08c717f-b951-4c5e-9827-a164675a5416" />
