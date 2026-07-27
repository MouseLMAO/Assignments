## Procedures Code

```asm

section .text
  global _start

_start:
  mov eax,65

alphabet_loop:
  mov [res],al
  mov byte [res+1],10

  mov ecx,res
  push eax
  call output
  pop eax

  inc eax
  cmp eax,90
  jle alphabet_loop

  call exit


output:
  mov edx,2
  mov ebx,1
  mov eax,4
  int 0x80
  ret


exit:
  mov ebx,0
  mov eax,1
  int 0x80


segment .bss
  res resb 2

```

## Challenges

One of the challenges I had was when I was writing to call EAX with ```sys_write```. It would cause the EAX value to be overrode since the main loop also uses EAX. I decided that I would use ```push EAX``` before and then use ```pop EAX``` afterwards so the values aren't overridden.

## Flowchart

<img width="210" height="740" alt="Procedures" src="https://github.com/user-attachments/assets/0bb01a28-2ede-4a3b-a0e1-e1d2e3738334" />
