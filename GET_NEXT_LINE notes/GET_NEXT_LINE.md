
## <span class="color-blue">Read function</span>

### <span class="color-red">1-Prototype</span>
**ssize_t read (int fd, void * buff, size_t count)**

| Parameter | Meaning                                                                                                      |
| --------- | ------------------------------------------------------------------------------------------------------------ |
| `fd`      | File descriptor: an integer that represents an open file. Examples: `0 = stdin`, `1 = stdout`, `2 = stderr`. |
| `buf`     | Pointer to a memory buffer where the data will be stored.                                                    |
| `count`   | Maximum number of bytes you want to read.                                                                    |
### <span class="color-red">2-Description</span>
`read()` is a **low-level system call** used to read raw bytes from a file, device, or input stream.  
It belongs to the **POSIX  API** and is defined in `<unistd.h>`.
It does **not** understand text, lines, or strings — it only transfers bytes.
**so shortly read() attempts to read up to  count  bytes from file descriptor fd  into the buffer pointed to by buff.**
### <span class="color-red">3-Return value</span>
**on successful  read return number of bytes that was  read
returns zero upon reading end-of-File
and return -1 on errors .**

| Return | Meaning                          |
| ------ | -------------------------------- |
| `> 0`  | Number of bytes actually read.   |
| `0`    | End Of File (EOF). No more data. |
| `-1`   | Error happened (check `errno`).  |
### <span class="color-red">4-Diagram — How read() Copies Data Into Your Buffer</span>

```
               ┌───────────────────────────────────────────┐
               │                 FILE on DISK              │
               │-------------------------------------------│
               │  H  e  l  l  o     W  o  r  l  d  !  \n    │
               └───────▲────▲────▲────▲────────────────────┘
                       │    │    │    │
                       │    │    │    │
               read(fd, buffer, 5 bytes)
                       │
                       ▼
        ┌──────────────────────────────────────────────┐
        │                  YOUR BUFFER                 │
        │----------------------------------------------│
Index → │  0   |   1   |   2   |   3   |   4   |   ... │
        │----------------------------------------------│
Data  → │  'H' |  'e'  |  'l'  |  'l'  |  'o'  |        │
        └──────────────────────────────────────────────┘

               ┌──────────────────────────┐
               │   RETURN VALUE = 5       │
               │   (5 bytes copied)       │
               └──────────────────────────┘

```


