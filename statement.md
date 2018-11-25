# memcpy vs. memmove
```C++ runnable
#include <stdio.h>
#include <string.h>

int main (void)
{
    char string [] = "stackoverflow";
    char *first, *second;
    first = string;
    second = string;

    puts(string);
    memcpy(first+5, first, 5);
    puts(first);
    memmove(second+5, second, 5);
    puts(second);
    return 0;
}
