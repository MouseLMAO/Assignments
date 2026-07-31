## Code

```asm

section .data
  x dd 1
  y dd 2
  z dd 3
  result dd 0

section .text
  global _start

addThreeValues:
  push ebp
  mov ebp, esp

  mov eax, [ebp + 8]
  add eax, [ebp + 12]
  add eax. [ebp + 16]

  leave
  ret

_start:
  push [z]
  push [y]
  push [x]

  call addThreeValues

  add esp, 12
  mov [result], eax

  mov eax, 1
  mov ebx, 0
  int 0x80

```
