## My Code

```asm
section .text
  global _start

_start:

  mov eax, 4
  mov ebx, 1
  mov ecx, msg
  mov edx, len
  int 0x80

  mov eax, 1
  mov ebx, 0
  int 0x80

section .data

msg db 'I came,', 0Ah
    db 'I saw,', 0Ah
    db 'I conquered.', 0Ah

len equ $ - msg
```

## Challenges

My greatest challenge trying to code in assembly code was remembering that the semicolon at the end doesn't end a code of line, but it tells you to treat whatever is after it as a comment. Another thing that stumped me a bit was to differentiate eax, ebx, ecx, edx.

## Flowchart

<img width="190" height="598" alt="First assembly program flowchart" src="https://github.com/user-attachments/assets/df179433-c3be-4875-bd2c-1bb32fd8602a" />
