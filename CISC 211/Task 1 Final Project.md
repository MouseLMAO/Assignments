## Task 1 Encryption and Decryption Code

```asm

section .data
  plainPrompt db "Enter plaintext: "
  plainPromptLen equ $-plainPrompt

  keyPrompt db "Enter key: "
  keyPromptLen equ $-keyPrompt

  plainLabel db "Plain text: "
  plainLabelLen equ $-plainLabel

  keyLabel db "Key: "
  keyLabelLen equ $-keyLabel

  encryptedLabel db "Encrypted text: "
  encryptedLabelLen equ $-encryptedLabel

  decryptedLabel db "Decrypted text: "
  decryptedLabelLen equ $-decryptedLabel

  newline db 10

  filename db "output.txt", 0

section .bss
  plaintext resb 100
  key resb 100
  encrypted resb 100
  decrypted resb 100

  length resd 1
  fileDesc resd 1

section .text
  global _start

_start:

  mov eax, 4
  mov ebx, 1
  mov ecx, plainPrompt
  mov edx, plainPromptLen
  int 0x80

  mov eax, 3
  mov ebx, 0
  mov ecx, plaintext
  mov edx, 100
  int 0x80

  dec eax
  mov [length], eax

  mov eax, 4
  mov ebx, 1
  mov ecx, keyPrompt
  mov edx, keyPromptLen
  int 0x80

  mov eax, 3
  mov ebx, 0
  mov ecx, key
  mov edx, 100
  int 0x80

  mov ecx, [length]
  mov esi, 0

encrypt:
  mov al, [plaintext + esi]
  xor al, [key + esi]
  mov [encrypted + esi], al

  inc esi
  loop encrypt

  mov ecx, [length]
  mov esi, 0

decrypt:
  mov al, [encrypted + esi]
  xor al, [key + esi]
  mov [decrypted + esi], al

  inc esi
  loop decrypt

  mov eax, 8
  mov ebx, filename
  mov ecx, 600o
  int 0x80

  mov [fileDesc], eax

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, plainLabel
  mov edx, plainLabelLen
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, plaintext
  mov edx, [length]
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, newline
  mov edx, 1
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, keyLabel
  mov edx, keyLabelLen
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, key
  mov edx, [length]
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, newline
  mov edx, 1
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, encryptedLabel
  mov edx, encryptedLabelLen
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, encrypted
  mov edx, [length]
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, newline
  mov edx, 1
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, decryptedLabel
  mov edx, decryptedLabelLen
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, decrypted
  mov edx, [length]
  int 0x80

  mov eax, 4
  mov ebx, [fileDesc]
  mov ecx, newline
  mov edx, 1
  int 0x80

  mov eax, 6
  mov ebx, [fileDesc]
  int 0x80

  mov eax, 1
  mov ebx, 0
  int 0x80

```

## Flowchart

[Cisc 211 Final Project Task 1.drawio.pdf](https://github.com/user-attachments/files/30849310/Cisc.211.Final.Project.Task.1.drawio.pdf)

## Presentation Video

https://youtu.be/FX_1r9DFDnA

