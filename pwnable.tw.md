#Start
######0x08048060  push esp            
```
[stack]
old_esp <- esp
```
######0x08048061  push 0x804809d      
```
[stack]
0x804809d(=*_exit) <- esp    
old_esp 
```
######0x08048066  xor eax, eax
######0x08048068  xor ebx, ebx
######0x0804806a  xor ecx, ecx
######0x0804806c  xor edx, edx
```
[eax] = 0
[ebx] = 0
[ecx] = 0
[edx] = 0

[stack]
0x804809d(=*_exit) <- esp
old_esp 
```
######0x0804806e  push 0x3a465443
######0x08048073  push 0x20656874
######0x08048078  push 0x20747261
######0x0804807d  push 0x74732073
######0x08048082  push 0x2774654c
```
[eax] = 0
[ebx] = 0
[ecx] = 0
[edx] = 0

[stack]
0x2774654c(=Let') <- esp
0x74732073(=s st)
0x20747261(=art )
0x20656874(=the )
0x3a465443(=CTF:)
0x804809d(=*_exit) 
old_esp 
```
######0x08048087  mov ecx, esp
```
[eax] = 0
[ebx] = 0
[ecx] = esp1
[edx] = 0

[stack]
0x2774654c(=Let') <- esp1, esp
0x74732073(=s st)
0x20747261(=art )
0x20656874(=the )
0x3a465443(=CTF:)
0x804809d(=*_exit) 
old_esp 
```
######0x08048089  mov dl, 0x14
######0x0804808b  mov bl, 0x1
######0x0804808d  mov al, 0x4
######0x0804808f  int 0x80
```
[eax] = 0x4
[ebx] = 0x1
[ecx] = esp1
[edx] = 0x14(=20)

[stack]
0x2774654c(=Let') <- esp1, esp
0x74732073(=s st)
0x20747261(=art )
0x20656874(=the )
0x3a465443(=CTF:)
0x804809d(=*_exit) 
old_esp 
```
[linux system call](http://syscalls.kernelgrok.com/)
######sys_write : eax=0x4, ebx=unsigned int fd, ecx=const char *buf, edx=size_t count

######0x08048091  xor ebx, ebx
######0x08048093  mov dl, 0x3c
######0x08048095  mov al, 0x3
######0x08048097  int 0x80
```
[eax] = 0x3
[ebx] = 0x0
[ecx] = esp1
[edx] = 0x3c(=16*3+12=48+12=60)

[stack]
0x2774654c(=Let') <- esp1, esp
0x74732073(=s st)
0x20747261(=art )
0x20656874(=the )
0x3a465443(=CTF:)
0x804809d(=*_exit) 
old_esp 
```
######sys_read : eax=0x3, ebx=unsigned int fd, ecx=char *buf, edx=size_t count

######0x08048099  add esp, 0x14
```
[eax] = 0x3
[ebx] = 0x0
[ecx] = esp1
[edx] = 0x3c(=16*3+12=48+12=60)

[stack]
0x........ <- esp1
0x........
0x........
0x........
0x........
0x804809d(=*_exit) <-esp 
old_esp 
```
######0x0804809c  ret
```
[eip] = 0x804809d(=*_exit)
[eax] = 0x3
[ebx] = 0x0
[ecx] = esp1
[edx] = 0x3c(=16*3+12=48+12=60)

[stack]
0x........ <- esp1
0x........
0x........
0x........
0x........
0x804809d(=*_exit) 
old_esp <-esp 
```

