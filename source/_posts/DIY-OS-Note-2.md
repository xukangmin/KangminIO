---
title: DIY OS Note (2) - Reach beyond 512 bytes
date: 2021-02-08 19:47:35
tags: diy, operating system
---

# bochs debug command

bochs -q -f 

ref: http://bochs.sourceforge.net/doc/docbook/user/using-bochs.html


```
mbrseg         equ    7c0h     ; boot sector address
outseg         equ    800h     ; store sector address

jmp   start
megwelcome:     db '------Wlecome Jiang Os------','$'
message1:       db 'step1:now  is   in   mbr','$'
message2:       db 'step2:now  jmp  out  mbr','$'
message3:       db 'memory address is---','$'
message4:       db 'CS:????','$'

start:
mov   ax,mbrseg
mov   ds,ax
call  welcome
call  newline
call  newline
call  inmbr
call  showcs
call  newline
call  newline

jmp   outseg:0        ;通过此条指令跳出MBR区

call  outmbr
call  showcs


welcome:
mov   si,megwelcome
call  printstr
ret


inmbr:
mov   si,message1
call  printstr
call  newline
mov   si,message3
call  printstr
ret

outmbr:
mov   si,message2
call  printstr
call  newline
mov   si,message3
call  printstr
ret

printstr:                  ;finish with '$'
      mov al,[si]         ; mov *si content to al 
      cmp al,'$'          ; compare al to '$'
      je disover          ; 
      mov ah,0eh
      int 10h
      inc si
      jmp printstr
disover:
      ret

newline:                     ;显示回车换行
      mov ah,0eh
      mov al,0dh
      int 10h
      mov al,0ah
      int 10h
      ret


showcs:                       ;展示CS的值
      mov  ax,cs

      mov  dl,ah
      call HL4BIT
      mov  dl,  BH
      call  ASCII
      mov  [message4+3],dl

      mov  dl,  Bl
      call  ASCII
      mov  [message4+4],dl

      mov  dl,al
      call HL4BIT
      mov  dl,  BH
      call  ASCII
      mov  [message4+5],dl

      mov  dl,  Bl
      call  ASCII
      mov  [message4+6],dl

      mov  si,  message4
      call printstr

      ret

;-----------------将16进制数字(1位)转换成ASCII码，输入DL,输出DL------
ASCII:   CMP  DL,9
         JG   LETTER  ;DL>OAH
         ADD  DL,30H  ;如果是数字,加30H即转换成ASCII码
         RET
LETTER:  ADD  DL,37H  ;如果是A～F,加37H即转换成ASCII码
         RET

;-----------------取出1个字节Byte的高4位和低4位,输入DL,输出BH和BL----------

HL4BIT:  MOV  DH,dl
         MOV  BL,dl
         SHR  DH,1
         SHR  DH,1
         SHR  DH,1
         SHR  DH,1
         MOV  BH,DH                    ;取高4位
         AND  BL,0FH                   ;取低4位
         RET


times 510-($-$$) db 0
db 0x55,0xaa
```