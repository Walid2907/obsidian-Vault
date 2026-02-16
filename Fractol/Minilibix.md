
# starting with mlx
## what is mlx
**mlx** is a graphical library that is build on X library to make it simple to work with will see X library later but now will focus on mlx 

include : \#include <minilibx-linux/mlx.h>
compile : cc test.c -Lminilibx-linux -lmlx -lX11 -lXext \#to be explained

## Functions:

1-mlx_init():
which is a function that initialize the connection with the x server and it return a void pointer.

2-mlx_destroy_display();
which is a function that ends the connection with the x server before freeing the pointer.

3-mlx_new_window():
takes the pointer returned by init as argument + width + height + name of the window created returns a void pointer  

4-mlx_destroy_window():
takes the init pointer and the window pointer to free the window pointer

5-mlx_loop():
it takes the init pointer as arg ,which keeps the window alive that is an event loop , is means that it a loop that waits for an event a mouse click keyboard etc 

