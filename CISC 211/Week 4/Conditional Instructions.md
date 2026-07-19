## 20 Numbers Code

```asm

section .text
  global _start

_start:
  mov eax, 2           ;If i wanted to do odd, I can just do mov eax, 1
  mov ecx, 0

generate_even:
  cmp eax, 20
  jg finished

  mov [numbers + ecx * 4], eax

inc ecx
add eax, 2

jmp generate_even

finished:
  mov eax, 1
  mov ebx, 0
  int 0x80

section .bss
  numbers resd 10

```

## Largest Integer Code

```asm

section .text
  global _start

_start:
  mov eax, [num1]

check_num2:
  cmp eax, [num2]
  jge check_num3
  mov eax, [num2]

check_num3:
  cmp eax, [num3]
  jge check_num4
  mov eax, [num3]

check_num4:
  cmp eax, [num4]
  jge check_num5
  mov eax, [num4]

check_num5:
  cmp eax, [num5]
  jge store_largest
  mov eax, [num5]

store_largest:
  mov [largest],eax

  mov eax, 1
  mov ebx, 0
  int 0x80

section .data
  num1 dd 14
  num2 dd 32
  num3 dd 7
  num4 dd 45
  num5 dd 21

section .bss
  largest resd 1

```

## Challenges

One of the challenges that I had was setting up the conditional jump.
I originally only had ```cmp eax, 20```
but it wasn't including the number 20. So when I tested odd, the code would work but when I tested even, it would always leave out 20.
I later learned that I need to include ```jg finished```
so that the loop would only end when the value becomes greater than 20.
I could have done just ```cmp eax, 21```
but that is too simple, although simple is good.

## 20 numbers flowchart

<img width="170" height="598" alt="20 numbers" src="https://github.com/user-attachments/assets/ca45c831-5101-4bfe-8348-89ee07050f97" />

## Largest integer flowchart

<img width="170" height="580" alt="Largest integer" src="https://github.com/user-attachments/assets/1d3d8c86-59b2-441d-a1de-1ad52b7d058c" />

