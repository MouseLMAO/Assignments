## Functions Code

```asm

section .data
  evenMsg db "Even number",10
  evenLen equ $-evenMsg

  oddMsg db "Odd number",10
  oddLen equ $-oddMsg

section .text
  global _start

_check_number:
  push ebp

  mov ebp, esp
  mov eax, DWORD [ebp+8]
  mov edx, 0
  mov ebx, 2
  div ebx

  cmp edx, 0
  je even_number

odd_number:
  mov ecx, oddMsg
  mov edx, oddLen
  call output
  jmp check_done


even_number:
  mov ecx, evenMsg
  mov edx, evenLen
  call output


check_done:
  leave
  ret

output:
  mov ebx, 1
  mov eax, 4
  int 0x80
  ret

exit:
  mov ebx, 0
  mov eax, 1
  int 0x80


_start:

  push 15
  call _check_number
  add esp, 4
  call exit

```

## Challenges

One challenge I had was making sure that both the odd and even parts are return through the same code. So I have ```jmp check_done```
so I can continue with the even side after going through the odd message. Another part that was a bit confusing is the seperate functions.
There's a bit more functions than I have worked with, which confused me a bit.

## Flowchart

<img width="210" height="749" alt="Functions" src="https://github.com/user-attachments/assets/e6cbc398-f7ab-42bb-af04-ccd0bff499ba" />
