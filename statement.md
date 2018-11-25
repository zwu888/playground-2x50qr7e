# memcpy vs. memmove
```C++ runnable
#include <stdio.h>
#include <string.h>

void* memcpy1(void* dest, const void* src, size_t n)
{
    char*      d = (char*) dest;
    const char*  s = (const char*) src;
    while(n--)
       *d++ = *s++;
    return dest;
}

void* memmove1(void* dest, const void* src, size_t n)
{
    char*     d  = (char*) dest;
    const char*  s = (const char*) src;
  
    if (s>d)
    {
         // start at beginning of s
         while (n--)
            *d++ = *s++;
    }
    else if (s<d)
    {
        // start at end of s
        d = d+n-1;
        s = s+n-1;
  
        while (n--)
           *d-- = *s--;
    }
    return dest;
}

int main (void)
{
    char string [] = "stackoverflow";
    char *first, *second;
    first = string;
    second = string;

    puts(string);
    memcpy1(first+5, first, 5);
    puts(first);
    memmove1(second+5, second, 5);
    puts(second);
    return 0;
}
