## Counter Code

```asm

section .text
  global _start

_start:
  mov ecx,10
  mov ebx,0

label:
  inc ebx
  loop label

  mov [counter],ebx

  mov eax,1
  mov ebx,0
  int 0x80

section .bss
counter resd 1

```

## Fiboncacci sequence code

```asm

section .text
  global _start

_start:
  mov eax,0
  mov ebx,1
  mov ecx,10

top:
  mov edx,eax
  add edx,ebx
  mov eax,ebx
  mov ebx,edx

  loop top

  mov [result],eax

  mov eax,1
  mov ebx,0
  int 0x80

section .bss
result resd 1

```

## Integer array code

```asm

section .text
  global _start

_start:
  mov eax,3
  mov ecx,array
  mov ebx,[ecx]

top:
  cmp ebx,[ecx]
  jge next

  mov ebx,[ecx]

next:
  add ecx,4
  dec eax
  jnz top

  mov [largest],ebx

  mov eax,1
  mov ebx,0
  int 0x80

section .data
  array dd 12,-4,27

section .bss
largest resd 1

```

## Challenges

One challenge was using ebx instead of ecx for the loop counter. In order to solve this,
I used ecx only for the loop, and used ebx to store the values. However, ebx is later used
to end the program, and so to not lose the counter value, I then transferred the counter value
into a seperate variable so I can exit the program without losing the value.

## Flowcharts

<img width="497" height="530" alt="Loops   Arrays" src="https://github.com/user-attachments/assets/c6a1eb53-4558-41d1-b29e-2be3a64bf08f" />
