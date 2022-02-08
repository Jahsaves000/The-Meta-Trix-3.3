# The-Meta-Trix-3.3
cs50 lecture 3 (algorithms)

exit.c

#include <cs50.h>
#include <stdio.h>

int main(int argc, string argv[])
{
    if (argc != 2)
    {
        printf("missing command-line argument\n");
        return 1;
    }
    printf("hello, %s\n", argv[1]);
    return 0;
}


names.c

#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};
    
    for (int i = 0; i < 7; i++)
    {
        if (strcmp(names[i], "Ron") == 0)
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("not found\n");
    return 1;
}


numbers.c

#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int numbers[] = {4, 6, 8, 2, 7, 5, 0};
    
    for (int i = 0; i < 7; i++)
    {
        if (numbers[i] == 9) 
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}


phonebook.c

#include <cs50.h>
#include <stdio.h>
#include <string.h>

typedef struct
{
    string name;
    string number;
}
person;

int main(void)
{
    person people[2];
    
    people[0].name = "Brian";
    people[0].number = "+1-617-495-1000";
    
    people[1].name = "David";
    people[1].number = "+1-949=468-2750";
    
    for (int i = 0; i < 2; i++)
    {
        if (strcmp(people[i].name, "David") == 0)
        {
            printf("Found %s\n", people[i].number);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}


/*my own program*/
(login.c)

#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string arvg[])
{
    string name = "Jahquantee Johnson";
    string characterName = "Makavellion";

    if (argc == 3)
    {
        string accessCode = get_string("Who are you?\n");
        if (strcmp(accessCode, characterName))
        {
            printf("No access\n");
        }
        else
        {
            printf("Hello, %s. Welcome back\n", name);
        }
    }

    else
    {
        printf("Access Denied\n");
    }



#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string arvg[])
{
    string name = "Jahquantee Johnson";
    string codeName = "Makavellion";

    if (argc == 7)
    {
        string accessCode = get_string("Access granted\nWho are you?\n");
        if (strcmp(accessCode, codeName))
        {
            printf("No access\n");
        }
        else
        {
            printf("%s, Access granted\nHello, %s. Welcome back. ", codeName, name);
            
            string helpYou = get_string("How may I help you today?\n");
            string worship = get_string("Would you like to worship like the angels in Revelations 4:11?\n");
            string scripture = get_string("Then turn to Revelations 4:8-11, Revelation 5:9-14, or Revelations 7:9-12.\n");
            
            printf("You are welcome. Be blessed Child of God in JESUS name!\n");
        }
    }

    else
    {
        printf("Access Denied\n");
    }
}


cs50 lecture 4 memory (18:00 pointers)

#include <stdio.h>

int main(void)
{
    char *s = "HI!";
    printf("%c\n", *s);
    printf("%c\n", *(s+1));
    printf("%c\n", *(s+2));
    printf("%i\n", *(s+3));
    printf("%c\n", *(s+100000));
}

//"&" is address location i.e. figures out the address
//"*" goes to that specific address (also known as de-referencer)
//"p" is a pointer


compare.c

#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    char *s = get_string("s: ");
    char *t = get_string("t: ");
    
    if (strcmp(s, t) == 0)
    {
        printf("Same\n");
    }
    else
    {
        printf("Different\n");
    }
}


copy.c

#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    char *s = get_string("s: ");
    
    char *t = malloc(strlen(s) + 1);
    if (t == NULL)
    {
        return 1;
    }
    
    strcpy(t, s);
    
    if (strlen(t) > 0)
    {
        t[0] = toupper(t[0]);
    }
    
    printf("s: %s\n", s);
    printf("t: %s\n", t);

    free(t);
}

//malloc is memory allocation
// NULL is not the same as NUL(\0). NULL is a null pointer. Use NULL for pointers. Use NUL for characters

swap.c

#include <stdio.h>

void swap(int *a, int *b);

int main(void)
{
    int x = 1;
    int y = 2;

    printf("x is %i, y is %i\n", x, y);
    swap(&x, &y);
    printf("x is %i, y is %i\n", x, y);
}

void swap(int *a, int *b)
{
    int tmp = *a;
    *a = *b;
    *b = tmp;
}
// main take away is that we use pointers to swap the values of x and y

mario1

#include <cs50.h>
#include <stdio.h>

void draw(int h);
int main(void)
{
    int height = get_int("Height: ");
    draw(height);
}

void draw(int h)
{
    for (int i = 0; i <= h; i++)
    {
        for (int j = 1; j <= i; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}

exe. mario1

#include <cs50.h>
#include <stdio.h>

void draw(int h);
int main(void)
{
    int height = get_int("Height: ");
    
    draw(height);
}

void draw(int h)
{
    if (h == 0)
    {
        return;
    }
    draw(h - 1);
    
    for (int i = 0; i < h; i++)
    {
        printf("#");
    }
    printf("\n");
}

scanf 

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *s = malloc(4);
    printf("s: ");
    scanf("%s", s);
    printf("s: %s\n", s);
    free(s);
}

//each time we use malloc we have to free it with "free"
