# Problem Solving and Programming (C Language) — Outline Notes (IGNOU BCA)

Nov 7, 2026 · @x

## How to use these notes

These are outline-method notes for MCS-011: each topic starts with its one-line point, then main ideas (bold letters), then indented details, a working program with its output, and an exam tip. Topics run from most-asked (8/8 papers) to least (3/8).

- **A. The outline method in one minute**
  - Big idea at the left edge; smaller points indented under the idea they belong to; details one step further in.
  - Every program sits directly under the point it demonstrates, with its output shown, because programming cannot be learned from headings alone.
- **B. The three labels on each topic**
  - Your subject has 23 common topics: 11 to practise, 6 to understand, 6 to memorise. Each heading is tagged with one label (my sorting, based on how each topic is asked):

| Label | What to do | Topics |
| --- | --- | --- |
| **Practise** (11) | Write the program yourself on paper until you can do it without looking | 1 Algorithm and flowchart, 4 Strings, 5 Patterns, 6 Decision control, 8 Recursion, 10 Functions, 12 Structures, 15 Array programs, 20 Number programs, 22 Matrices, 23 ++/−− tracing |
| **Understand** (6) | Be able to explain it with a diagram and a short example | 2 File handling, 3 Macros, 7 Pointers, 9 Call by value vs reference, 16 Dynamic memory, 17 Loops |
| **Memorise** (6) | Learn the definitions and comparison tables by heart | 11 Structure vs union, 13 Storage classes, 14 Operators, 18 break vs continue, 19 Ternary operator, 21 Array declaration |

- **C. How to practise a program (do this for every Practise topic)**
  1. Read the program and its explanation once.
  2. Trace it by hand with the sample input and check you get the shown output.
  3. Close the notes and write it on paper.
  4. Compare, fix mistakes, repeat the next day.
  - Free online compilers (search "online C compiler") let you type and run any program here without installing anything.
- **D. Your solved-paper videos** (all from the IGNOUverse YouTube channel; watch after reading the matching topics here)

| Exam paper | Videos | Playlist |
| --- | --- | --- |
| June 2024 | 6 | [MCS-011 June 2024 solution](https://www.youtube.com/playlist?list=PLKzz9hY3xDDWSEIwryaINfVNPPdaaGGz6) |
| December 2023 | 7 | [MCS-011 Dec 2023 solution](https://www.youtube.com/playlist?list=PLKzz9hY3xDDWigFm1iHQyYCMwyecj8DY9) |
| June 2023 | 16 | [MCS-011 June 2023 solution](https://www.youtube.com/playlist?list=PLKzz9hY3xDDX8w5Q1-EbRnQW3i5J8h1Cv) |
| December 2022 | 6 | [MCS-011 Dec 2022 solution](https://www.youtube.com/playlist?list=PLKzz9hY3xDDW5ZqP9Z0QBLBUn4-xmDo9z) |
| June 2022 | 10 | [MCS-011 June 2022 solution](https://www.youtube.com/playlist?list=PLKzz9hY3xDDVeMosAxuiP-llEVNYlb3pB) |

- **E. Suggested order if you are starting from zero**
  - Read "C from zero" first. Then topics 14 (operators), 6 (decisions), 17 (loops), 21 (arrays) to learn the building blocks, then follow the list in order.

## C from zero: read this first

C is a language for writing instructions a computer can follow; you write the instructions in a text file, a compiler translates them into machine code, and the computer runs the result. Every topic below uses the ten ideas in this section.

- **A. Program, language, compiler**
  - A **program** is a list of instructions for the computer.
  - The computer only understands 0s and 1s (**machine code**). Humans write in a readable **programming language** such as C.
  - A **compiler** translates the C file (e.g. hello.c) into a program the computer can run.
  - The journey: write code → **preprocess** (handles # lines, topic 3) → **compile** → **link** (adds ready-made library code like printf) → **run**.
  - **Syntax error**: you broke a grammar rule (e.g. forgot a semicolon); the compiler refuses. **Logical error**: it runs but gives the wrong answer.
- **B. Your first C program**

```c
#include <stdio.h>          /* bring in printf and scanf */

int main()                  /* every C program starts running here */
{
    printf("Hello, IGNOU!\n");   /* show text on screen */
    return 0;               /* tell the system: finished OK */
}
```

- **B (output).** `Hello, IGNOU!`
  - `#include <stdio.h>`: "stdio" = standard input/output. It gives you printf (print) and scanf (read input).
  - `main()`: the starting point. The `{ }` braces hold its instructions.
  - Every instruction ends with a **semicolon ;** (like a full stop).
  - `\n` means "go to a new line".
  - `/* ... */` and `// ...` are **comments**: notes for humans, ignored by the compiler.
- **C. Variables: named boxes in memory**
  - A variable is a named box that holds one value. You must **declare** it (say its type and name) before use.
    - `int age;` makes a box called age for whole numbers.
    - `age = 19;` puts 19 in it (= means "store", not "equals").
    - `int age = 19;` does both at once (**initialisation**).
  - Naming rules (identifiers): letters, digits and underscore only; cannot start with a digit; no spaces; not a keyword (like int, if); case-sensitive (Age and age are different).
- **D. Basic data types**

| Type | Holds | Example | Usual size | printf/scanf code |
| --- | --- | --- | --- | --- |
| int | Whole numbers | 25, −7 | 4 bytes (2 on old 16-bit compilers like Turbo C) | %d |
| float | Decimal numbers (about 6 digits) | 3.14 | 4 bytes | %f |
| double | Decimal numbers (about 15 digits) | 3.14159265 | 8 bytes | %lf |
| char | One character | 'A' | 1 byte | %c |
| char\[ \] (string) | Text | "IGNOU" | 1 byte per letter + 1 | %s |

- **D (notes).** Modifiers change the range: short, long, unsigned (no negatives). A **byte** is a small unit of memory (8 bits).
- **E. Output with printf, input with scanf**

```c
#include <stdio.h>
int main()
{
    int a, b, sum;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);      /* & = "the address of": where to put the input */
    sum = a + b;
    printf("Sum = %d\n", sum);   /* %d is replaced by the value of sum */
    return 0;
}
```

- **E (sample run).** Input `4 5` → output `Sum = 9`.
  - In scanf, put **&** before ordinary variables (not before a string array name). Forgetting & is the most common beginner bug.
  - `%5d` prints in a width of 5; `%.2f` prints 2 decimal places.
- **F. Constants and keywords**
  - Constants are fixed values: 10, 3.5, 'x', "hello". Also `const int MAX = 100;` or `#define MAX 100` (topic 3).
  - Keywords are reserved words with fixed meaning (32 in standard C): int, float, char, if, else, for, while, do, switch, case, break, continue, return, struct, union, void, static, extern, auto, register, sizeof, goto, and others.
- **G. Statements and blocks**
  - A **statement** is one instruction ending in ;. A **block** is several statements inside { } treated as one.
- **H. The three ways a program flows**
  - **Sequence**: one line after another.
  - **Selection**: choose a path (if, switch; topic 6).
  - **Repetition**: repeat (for, while, do-while; topic 17).
  - Every program in these notes is built only from these three.
- **I. Header files you will meet**
  - stdio.h (printf, scanf, files), string.h (strlen, strcpy…), math.h (sqrt, pow), stdlib.h (malloc, free, exit), conio.h (clrscr, getch; old Turbo C only).
- **J. Reading the programs in these notes**
  - Each program is complete: copy it into an online compiler and it runs.
  - The "Output" line after each program shows exactly what appears on screen for the sample input.

## 1. Algorithm and flowchart for a simple problem (8/8) · Practise

An algorithm is the solution written as numbered steps in plain English; a flowchart is the same solution drawn with standard shapes joined by arrows. Every paper asks you to write both for a small problem, so learn the symbols and practise the three examples below.

- **A. Algorithm**
  - A finite, ordered list of clear steps that solves a problem.
  - Properties: input, output, definiteness (each step clear), finiteness (it ends), effectiveness (each step doable).
  - Exam style: "Step 1: Start. Step 2: Read … Step n: Stop."
- **B. Flowchart**
  - A picture of the algorithm. Easier to follow and to spot mistakes in.
  - Drawn top to bottom, arrows show the order.
- **C. Flowchart symbols (memorise)**

| Shape | Name | Used for |
| --- | --- | --- |
| Oval / rounded box ( ) | Terminal | Start and Stop |
| Parallelogram / / | Input/Output | Read a, Print sum |
| Rectangle \[ \] | Process | Calculations: sum = a + b |
| Diamond < > | Decision | A yes/no question: is a > b? |
| Arrow → | Flow line | Shows the next step |
| Small circle ○ | Connector | Joins parts of a long chart |
| Rectangle with double side lines | Predefined process | Calling a function |

- **D. Example 1: is a number even or odd?**
  - Algorithm:
    1. Start.
    2. Read n.
    3. If n % 2 == 0 (remainder 0 when divided by 2), print "Even"; otherwise print "Odd".
    4. Stop.

```
          ( Start )
              |
          / Read n /
              |
        < n % 2 == 0 ? >
         yes /     \ no
            /       \
   / Print "Even" / / Print "Odd" /
            \       /
             \     /
           ( Stop )
```

- **E. Example 2: largest of three numbers** (the most-asked one)
  - Algorithm:
    1. Start.
    2. Read a, b, c.
    3. If a > b, go to step 4; else go to step 5.
    4. If a > c, max = a; else max = c. Go to step 6.
    5. If b > c, max = b; else max = c.
    6. Print max.
    7. Stop.

```
               ( Start )
                   |
            / Read a, b, c /
                   |
              < a > b ? >
          yes /         \ no
             /           \
      < a > c ? >     < b > c ? >
     yes/    \no      yes/    \no
       /      \         /      \
  [max = a] [max = c] [max = b] [max = c]
       \      |         |      /
        \_____|_________|_____/
                   |
             / Print max /
                   |
               ( Stop )
```

- **E (C program).**

```c
#include <stdio.h>
int main()
{
    int a, b, c, max;
    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);
    if (a > b)
        max = (a > c) ? a : c;
    else
        max = (b > c) ? b : c;
    printf("Largest = %d\n", max);
    return 0;
}
```

- **E (output).** Input `12 45 30` → `Largest = 45`.
- **F. Example 3: factorial of n (a flowchart with a loop)**
  - n! = 1 × 2 × 3 × … × n. Example: 5! = 120.
  - Algorithm:
    1. Start.
    2. Read n.
    3. Set fact = 1, i = 1.
    4. If i > n, go to step 7.
    5. fact = fact × i; i = i + 1.
    6. Go to step 4.
    7. Print fact.
    8. Stop.

```
            ( Start )
                |
            / Read n /
                |
        [ fact = 1, i = 1 ]
                |
      +---> < i <= n ? > ---no---> / Print fact / ---> ( Stop )
      |         | yes
      |  [ fact = fact * i ]
      |         |
      |   [ i = i + 1 ]
      |         |
      +---------+
```

- **F (trace for n = 4).** fact: 1 → 1 → 2 → 6 → 24; i: 1 → 2 → 3 → 4 → 5 (stop). Print 24.
- **G. Other problems often asked (same pattern)**
  - Sum of first n natural numbers (loop: sum = sum + i).
  - Check prime (loop dividing by 2 to n−1, a decision inside).
  - Swap two numbers (process boxes only: temp = a, a = b, b = temp).
  - Simple interest: SI = P × R × T / 100 (read → process → print).
  - Sum of digits, reverse a number (see topic 20).
- **H. Algorithm vs flowchart**

| Algorithm | Flowchart |
| --- | --- |
| Written in numbered steps (text) | Drawn with shapes and arrows |
| Easy to write and change | Easy to see at a glance |
| Hard to follow for big branching problems | Becomes huge for big problems |
| No special symbols | Standard symbols |

**Exam tip:** write the algorithm first, then draw the flowchart so every step has a box. Use a ruler-straight layout, label every diamond's arrows "yes" and "no", and always start with Start and end with Stop.

## 2. File handling: fopen, fclose, fseek, ftell, modes, sequential vs random access (8/8) · Understand

A file stores data on disk so it survives after the program ends; in C you open it with fopen (choosing a mode such as "r", "w" or "a"), read or write it, and close it with fclose. fseek jumps to any position and ftell reports the current position, which is what makes random access possible.

- **A. Why files?**
  - Variables live in RAM and vanish when the program ends. A file on disk keeps the data.
  - Two kinds: **text files** (readable characters, e.g. notes.txt) and **binary files** (raw bytes, e.g. records saved with fwrite).
- **B. The FILE pointer**
  - C tracks an open file through a pointer of type **FILE \*** (defined in stdio.h).
    - `FILE *fp;` declares it.
  - Think of fp as a bookmark: it remembers which file is open and where you are in it.
- **C. Opening and closing**
  - `fp = fopen("marks.txt", "r");` opens the file in the given mode.
    - If opening fails (e.g. the file does not exist for "r"), fopen returns **NULL**. Always check.
  - `fclose(fp);` closes it: saves any pending data and frees the bookmark. Returns 0 on success.
- **D. File opening modes (memorise)**

| Mode | Meaning | If file exists | If file does not exist |
| --- | --- | --- | --- |
| "r" | Read only | Opens, position at start | Returns NULL |
| "w" | Write only | **Erases** old content | Creates new file |
| "a" | Append (add at end) | Keeps content, writes at end | Creates new file |
| "r+" | Read and write | Opens, position at start | Returns NULL |
| "w+" | Write and read | Erases old content | Creates new file |
| "a+" | Read and append | Reads anywhere, writes at end | Creates new file |

- **D (binary).** Add **b** for binary files: "rb", "wb", "ab", "rb+", "wb+", "ab+".
- **E. Reading and writing functions**

| Function | Does | Example |
| --- | --- | --- |
| fgetc(fp) / getc(fp) | Read one character (returns EOF at end) | ch = fgetc(fp); |
| fputc(ch, fp) / putc | Write one character | fputc('A', fp); |
| fgets(str, n, fp) | Read a line (up to n−1 chars) | fgets(line, 80, fp); |
| fputs(str, fp) | Write a string | fputs("Hello", fp); |
| fprintf(fp, …) | Formatted write, like printf | fprintf(fp, "%d", roll); |
| fscanf(fp, …) | Formatted read, like scanf | fscanf(fp, "%d", &roll); |
| fwrite(&rec, size, count, fp) | Write raw blocks (binary) | fwrite(&s, sizeof(s), 1, fp); |
| fread(&rec, size, count, fp) | Read raw blocks (binary) | fread(&s, sizeof(s), 1, fp); |
| feof(fp) | True when end of file reached | while (!feof(fp)) |

- **E (EOF).** **EOF** (End Of File) is a special value, usually −1. Store fgetc's result in an **int**, not a char, so EOF can be detected correctly.
- **F. fseek, ftell, rewind: moving the bookmark**
  - **fseek(fp, offset, origin)** moves the position by offset bytes from origin. Returns 0 if it worked.

| Origin constant | Value | Counts from |
| --- | --- | --- |
| SEEK\_SET | 0 | Beginning of file |
| SEEK\_CUR | 1 | Current position |
| SEEK\_END | 2 | End of file |

- **F (examples).**
  - `fseek(fp, 10, SEEK_SET);` go to byte 10 from the start.
  - `fseek(fp, -5, SEEK_CUR);` go back 5 bytes.
  - `fseek(fp, 0, SEEK_END);` go to the very end.
  - **ftell(fp)** returns the current position as a long (bytes from the start).
  - **rewind(fp)** goes back to the start (same as fseek(fp, 0, SEEK\_SET)).
  - Mini example: data.txt holds `IGNOU BCA`. After `fseek(fp, 6, SEEK_SET);`, `fgetc(fp)` returns 'B' and then `ftell(fp)` returns 7.
- **G. Program 1: write to a file, then read it back**

```c
#include <stdio.h>
int main()
{
    FILE *fp;
    int ch;

    fp = fopen("note.txt", "w");          /* create / overwrite */
    if (fp == NULL) { printf("Cannot open file\n"); return 1; }
    fprintf(fp, "Welcome to IGNOU\n");
    fclose(fp);

    fp = fopen("note.txt", "r");          /* open again to read */
    if (fp == NULL) { printf("Cannot open file\n"); return 1; }
    while ((ch = fgetc(fp)) != EOF)        /* read until end of file */
        putchar(ch);                       /* show each character */
    fclose(fp);
    return 0;
}
```

- **G (output).** `Welcome to IGNOU`
- **H. Program 2: copy one file to another (asked very often)**

```c
#include <stdio.h>
int main()
{
    FILE *src, *dest;
    int ch;

    src = fopen("source.txt", "r");
    if (src == NULL) { printf("Cannot open source.txt\n"); return 1; }

    dest = fopen("copy.txt", "w");
    if (dest == NULL) { printf("Cannot create copy.txt\n"); fclose(src); return 1; }

    while ((ch = fgetc(src)) != EOF)   /* read one char ... */
        fputc(ch, dest);               /* ... write the same char */

    printf("File copied successfully.\n");
    fclose(src);
    fclose(dest);
    return 0;
}
```

- **H (how it works).** Open the source for reading and the target for writing; move characters one at a time until EOF; close both.
- **I. Program 3: size of a file using fseek and ftell**

```c
#include <stdio.h>
int main()
{
    FILE *fp = fopen("source.txt", "r");
    long size;
    if (fp == NULL) { printf("Cannot open file\n"); return 1; }
    fseek(fp, 0, SEEK_END);      /* jump to the end */
    size = ftell(fp);            /* position at end = size in bytes */
    printf("File size = %ld bytes\n", size);
    fclose(fp);
    return 0;
}
```

- **J. Program 4: count characters, lines and spaces** (a common variant)
  - Inside the fgetc loop: `chars++;` for every character, `if (ch == '\n') lines++;`, `if (ch == ' ') spaces++;`.
- **K. Sequential vs random access**
  - **Sequential**: read from the start, one item after another, like a cassette tape. Uses fgetc, fgets, fscanf.
  - **Random (direct)**: jump straight to any position, like choosing a song on a phone. Uses fseek, ftell, rewind, usually with fixed-size records (fread/fwrite).
    - To read the 5th student record: `fseek(fp, 4 * sizeof(struct student), SEEK_SET); fread(&s, sizeof(s), 1, fp);`

| Point | Sequential access | Random access |
| --- | --- | --- |
| How you reach data | Pass through everything before it | Jump directly to it |
| Speed for one record in the middle | Slow | Fast |
| Functions | fgetc, fgets, fscanf, fprintf | fseek, ftell, rewind + fread, fwrite |
| Record size | Can vary | Usually fixed |
| Example | Reading a text file line by line | Updating record 50 in a student database |

**Exam tip:** in every file program, check `if (fp == NULL)` after fopen and close every file. For theory, give the modes table and the fseek origins table; they carry most of the marks.

## 3. Macros and preprocessor directives (8/8) · Understand

The preprocessor is a text-editing step that runs before compilation and obeys lines starting with #; a macro (#define) is a name the preprocessor replaces with its text everywhere, so SQUARE(x) is pasted in, not called like a function. Always bracket macro arguments, or SQUARE(2+3) gives 11 instead of 25.

- **A. What the preprocessor does**
  - Before the compiler sees your code, the preprocessor reads it and handles every line that starts with **#** (a **directive**).
  - It only does text work: pasting in files, replacing names, keeping or dropping blocks of code.
  - Directives do **not** end with a semicolon.
- **B. Main directives (memorise)**

| Directive | Purpose | Example |
| --- | --- | --- |
| #include | Paste in a header file | #include \<stdio.h> |
| #define | Define a macro | #define PI 3.14159 |
| #undef | Cancel a macro | #undef PI |
| #ifdef / #ifndef | Keep code only if a macro is / is not defined | #ifdef DEBUG |
| #if, #elif, #else, #endif | Conditional compilation | #if MAX > 100 |
| #error | Stop compilation with a message | #error "Wrong setting" |
| #pragma | Special compiler instructions | #pragma once |

- **B (include forms).** `#include <stdio.h>` searches the system folders (library headers). `#include "myfile.h"` searches your own folder first (your headers).
- **C. Object-like macros (named constants)**
  - `#define PI 3.14159` → every PI in the code becomes 3.14159 before compiling.
  - `#define MAX 100` → `int a[MAX];` becomes `int a[100];`.
  - Convention: macro names in CAPITALS.
- **D. Function-like macros (macros with arguments)**
  - `#define SQUARE(x) ((x) * (x))`
  - `SQUARE(5)` is replaced by `((5) * (5))`. No function call happens.
  - **The bracket trap**:
    - Bad: `#define SQUARE(x) x * x`
    - `SQUARE(2 + 3)` becomes `2 + 3 * 2 + 3` = 2 + 6 + 3 = **11**, not 25.
    - Fix: brackets around each x and around the whole body.
  - **The side-effect trap**: `SQUARE(i++)` becomes `((i++) * (i++))`, so i increases twice. Avoid ++ inside macro arguments.
- **E. Program: square, cube and area macros (most-asked program)**

```c
#include <stdio.h>
#define PI 3.14159
#define SQUARE(x)       ((x) * (x))
#define CUBE(x)         ((x) * (x) * (x))
#define AREA_CIRCLE(r)  (PI * (r) * (r))
#define AREA_RECT(l, b) ((l) * (b))
#define MAX(a, b)       ((a) > (b) ? (a) : (b))

int main()
{
    int n = 4;
    float r = 2.0;
    printf("Square of %d = %d\n", n, SQUARE(n));
    printf("Cube of %d = %d\n", n, CUBE(n));
    printf("Area of circle (r = %.1f) = %.2f\n", r, AREA_CIRCLE(r));
    printf("Area of rectangle 5 x 3 = %d\n", AREA_RECT(5, 3));
    printf("Larger of 7 and 9 = %d\n", MAX(7, 9));
    printf("Square of (2+3) = %d\n", SQUARE(2 + 3));
    return 0;
}
```

- **E (output).**

```
Square of 4 = 16
Cube of 4 = 64
Area of circle (r = 2.0) = 12.57
Area of rectangle 5 x 3 = 15
Larger of 7 and 9 = 9
Square of (2+3) = 25
```

- **F. Conditional compilation (short example)**

```c
#define DEBUG
#ifdef DEBUG
    printf("x = %d\n", x);   /* compiled only while DEBUG is defined */
#endif
```

- **F (use).** Turn testing messages on or off, or build different versions for different computers, without deleting code.
- **G. Predefined macros**: **DATE** (compile date), **TIME** (compile time), **FILE** (file name), **LINE** (current line number).
- **H. Macro vs function (very frequently asked)**

| Point | Macro | Function |
| --- | --- | --- |
| Handled by | Preprocessor (before compiling) | Compiler; called while running |
| How it works | Text is pasted wherever it is used | Control jumps to the function and returns |
| Speed | Faster: no call overhead | Slightly slower: call and return cost time |
| Program size | Grows: code copied at every use | Smaller: code exists once |
| Type checking | None: SQUARE works on int or float alike, and mistakes go unnoticed | Arguments are type-checked |
| Side effects | Arguments may be evaluated twice (SQUARE(i++)) | Each argument evaluated once |
| Debugging | Harder (you never see the expanded text) | Easier |
| Recursion | Not possible | Possible |
| Best for | Very small, frequently used operations | Larger or complex logic |
| Example | #define SQUARE(x) ((x)\*(x)) | int square(int x) { return x \* x; } |

**Exam tip:** in any macro program, put brackets around every argument and the whole body, and mention the SQUARE(2+3) example to show you know why.

## 4. String programs without library functions (7/8) · Practise

A string in C is a character array ending with the invisible null character '\\0'; every "without library function" program is just a loop that walks the array until it reaches '\\0'. Learn the five programs below (length, reverse, palindrome, copy, concatenate) and the string-function table.

- **A. What a string is**
  - A string is text stored in a **char array**, ending with **'\\0'** (null character, value 0) to mark the end.
  - `char s[10] = "IGNOU";` is stored as:

| Index | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- |
| s\[index\] | 'I' | 'G' | 'N' | 'O' | 'U' | '\\0' |

- **A (facts).**
  - Indexes start at **0**. A 5-letter word needs at least 6 boxes.
  - Reading a word: `scanf("%s", s);` (no & needed: the array name is already an address). It stops at the first space.
  - Reading a full line with spaces: `fgets(s, 100, stdin);` (old books use gets, which is unsafe and removed from modern C).
  - Printing: `printf("%s", s);`
- **B. The master pattern**
  - `for (i = 0; s[i] != '\0'; i++) { ... }` visits every character. Every program below is a variation of this loop.
- **C. Program 1: length of a string**

```c
#include <stdio.h>
int main()
{
    char s[100];
    int len = 0;
    printf("Enter a word: ");
    scanf("%s", s);
    while (s[len] != '\0')     /* count until the end marker */
        len++;
    printf("Length = %d\n", len);
    return 0;
}
```

- **C (output).** Input `COMPUTER` → `Length = 8`.
- **D. Program 2: reverse a string (in place)**

```c
#include <stdio.h>
int main()
{
    char s[100], temp;
    int i, j, len = 0;
    printf("Enter a word: ");
    scanf("%s", s);
    while (s[len] != '\0')
        len++;
    for (i = 0, j = len - 1; i < j; i++, j--)   /* swap ends, move inwards */
    {
        temp = s[i];
        s[i] = s[j];
        s[j] = temp;
    }
    printf("Reversed = %s\n", s);
    return 0;
}
```

- **D (trace for "IGNOU").** Swap I↔U → UGNOI; swap G↔O → UONGI; i = j = 2, stop. Output `Reversed = UONGI`.
- **E. Program 3: check palindrome** (reads the same backwards, e.g. MADAM, LEVEL)

```c
#include <stdio.h>
int main()
{
    char s[100];
    int i = 0, j, len = 0, isPal = 1;
    printf("Enter a word: ");
    scanf("%s", s);
    while (s[len] != '\0')
        len++;
    j = len - 1;
    while (i < j)
    {
        if (s[i] != s[j])      /* mismatch: not a palindrome */
        {
            isPal = 0;
            break;
        }
        i++;
        j--;
    }
    if (isPal)
        printf("%s is a palindrome\n", s);
    else
        printf("%s is not a palindrome\n", s);
    return 0;
}
```

- **E (trace).**
  - MADAM: M=M, A=A, then i = j = 2 → `MADAM is a palindrome`.
  - HELLO: H ≠ O at the first check → `HELLO is not a palindrome`.
- **F. Program 4: copy one string into another**

```c
#include <stdio.h>
int main()
{
    char src[100], dest[100];
    int i = 0;
    printf("Enter a word: ");
    scanf("%s", src);
    while (src[i] != '\0')
    {
        dest[i] = src[i];      /* copy character by character */
        i++;
    }
    dest[i] = '\0';            /* do not forget the end marker */
    printf("Copied string = %s\n", dest);
    return 0;
}
```

- **G. Program 5: concatenate (join) two strings**

```c
#include <stdio.h>
int main()
{
    char s1[200], s2[100];
    int i = 0, j = 0;
    printf("Enter first word: ");
    scanf("%s", s1);
    printf("Enter second word: ");
    scanf("%s", s2);
    while (s1[i] != '\0')      /* go to the end of s1 */
        i++;
    while (s2[j] != '\0')      /* append s2 there */
    {
        s1[i] = s2[j];
        i++;
        j++;
    }
    s1[i] = '\0';
    printf("Joined string = %s\n", s1);
    return 0;
}
```

- **G (output).** Input `IGNOU` and `BCA` → `Joined string = IGNOUBCA`.
- **H. Bonus: compare two strings and count vowels** (short loop ideas)
  - Compare: walk both strings while the characters match and neither has ended; if both end together, they are equal; otherwise the difference s1\[i\] − s2\[i\] tells which is bigger.
  - Count vowels: inside the master loop, `if (c=='a'||c=='e'||c=='i'||c=='o'||c=='u') count++;` (add capitals too).
  - Upper to lower case: `if (s[i] >= 'A' && s[i] <= 'Z') s[i] = s[i] + 32;` (ASCII 'A' = 65, 'a' = 97).
- **I. Library string functions (string.h) — memorise**

| Function | Does | Example | Result |
| --- | --- | --- | --- |
| strlen(s) | Length (without '\\0') | strlen("IGNOU") | 5 |
| strcpy(d, s) | Copies s into d | strcpy(d, "BCA") | d = "BCA" |
| strncpy(d, s, n) | Copies first n characters | strncpy(d, "IGNOU", 3) | "IGN" (add '\\0' yourself) |
| strcat(d, s) | Appends s to the end of d | d = "IG"; strcat(d, "NOU") | d = "IGNOU" |
| strcmp(a, b) | Compares: 0 if equal, negative if a < b, positive if a > b | strcmp("abc", "abd") | negative |
| strchr(s, c) | Finds first c in s | strchr("IGNOU", 'N') | pointer to "NOU" |
| strstr(s, t) | Finds substring t in s | strstr("IGNOU", "NO") | pointer to "NOU" |
| strrev(s) | Reverses s (Turbo C only, not standard) | strrev("ABC") | "CBA" |
| strupr / strlwr | Upper / lower case (Turbo C only) | strupr("bca") | "BCA" |

**Exam tip:** when the question says "without using library functions", never include string.h; compute the length with your own loop. Always end a newly built string with '\\0' and mention why.

## 5. Pattern printing programs: number, star and "IGNOU" pyramids (7/8) · Practise

Every pattern is a nested loop: the outer loop counts rows, and inside it one loop prints spaces and another prints the stars, numbers or letters for that row. Work out "how many spaces and how many symbols on row i" first, and the code writes itself.

- **A. The method (use it for any pattern)**
  1. Count the rows: that is the outer loop, `for (i = 1; i <= n; i++)`.
  2. For row i, write down how many spaces and how many symbols appear. Find the rule (e.g. spaces = n − i, stars = 2i − 1).
  3. Inner loop 1 prints the spaces; inner loop 2 prints the symbols.
  4. After the inner loops, `printf("\n");` to start the next row.
  - Example rule table for the star pyramid with n = 4:

| Row i | Spaces (n − i) | Stars (2i − 1) | Looks like |
| --- | --- | --- | --- |
| 1 | 3 | 1 | `    * ` |
| 2 | 2 | 3 | `   *** ` |
| 3 | 1 | 5 | `  ***** ` |
| 4 | 0 | 7 | `*******` |

- **B. Pattern 1: right-angled star triangle**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4;
    for (i = 1; i <= n; i++)          /* rows */
    {
        for (j = 1; j <= i; j++)      /* row i has i stars */
            printf("* ");
        printf("\n");
    }
    return 0;
}
```

```
*
* *
* * *
* * * *
```

- **C. Pattern 2: number triangles** (change only the printf line of Pattern 1)
  - `printf("%d ", j);` gives 1 / 1 2 / 1 2 3 / 1 2 3 4
  - `printf("%d ", i);` gives 1 / 2 2 / 3 3 3 / 4 4 4 4
  - Floyd's triangle: keep a counter k = 1 outside; `printf("%d ", k++);` gives 1 / 2 3 / 4 5 6 / 7 8 9 10
- **D. Pattern 3: inverted star triangle**

```c
for (i = n; i >= 1; i--)
{
    for (j = 1; j <= i; j++)
        printf("* ");
    printf("\n");
}
```

```
* * * *
* * *
* *
*
```

- **E. Pattern 4: star pyramid**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4;
    for (i = 1; i <= n; i++)
    {
        for (j = 1; j <= n - i; j++)      /* leading spaces */
            printf(" ");
        for (j = 1; j <= 2 * i - 1; j++)  /* stars */
            printf("*");
        printf("\n");
    }
    return 0;
}
```

```
   *
  ***
 *****
*******
```

- **F. Pattern 5: number pyramid (1, 121, 12321 …)**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4;
    for (i = 1; i <= n; i++)
    {
        for (j = 1; j <= n - i; j++)
            printf(" ");
        for (j = 1; j <= i; j++)        /* count up: 1 2 ... i */
            printf("%d", j);
        for (j = i - 1; j >= 1; j--)    /* count down: i-1 ... 1 */
            printf("%d", j);
        printf("\n");
    }
    return 0;
}
```

```
   1
  121
 12321
1234321
```

- **G. Pattern 6: the "IGNOU" triangle** (asked several times)

```c
#include <stdio.h>
int main()
{
    char s[] = "IGNOU";
    int i, j;
    for (i = 0; i < 5; i++)
    {
        for (j = 0; j <= i; j++)      /* print first i+1 letters */
            printf("%c ", s[j]);
        printf("\n");
    }
    return 0;
}
```

```
I
I G
I G N
I G N O
I G N O U
```

- **H. Pattern 7: the "IGNOU" pyramid**

```c
#include <stdio.h>
int main()
{
    char s[] = "IGNOU";
    int i, j, n = 5;
    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n - 1 - i; j++)   /* leading spaces */
            printf(" ");
        for (j = 0; j <= i; j++)          /* letter followed by a space */
            printf("%c ", s[j]);
        printf("\n");
    }
    return 0;
}
```

```
    I
   I G
  I G N
 I G N O
I G N O U
```

- **H (variations).**
  - Reverse order (IGNOU, IGNO, IGN, IG, I): run the outer loop from i = 4 down to 0.
  - Each row ending at a different letter (U / O U / N O U …): print from j = 4 − i to 4.
- **I. Pattern 8: alphabet triangle (A / A B / A B C …)**
  - `printf("%c ", 'A' + j - 1);` inside Pattern 1's inner loop. Letters are numbers underneath (ASCII), so 'A' + 1 is 'B'.

**Exam tip:** draw the expected pattern, then write the small rows/spaces/symbols table beside it before coding. Examiners award marks for correct loop limits even if a space is out of place.

## 6. Decision control: if, else-if ladder, nested if, switch; grade, tax and calculator programs (6/8) · Practise

Decision statements let a program choose what to do: if/else for one yes-or-no test, an else-if ladder for several ranges (grades, tax slabs), nested if for a test inside a test, and switch for picking one of many exact values (a calculator's + − × ÷).

- **A. The simple if and if-else**
  - Conditions use relational operators (>, <, >=, <=, ==, !=). In C, 0 means false and any non-zero value means true.

```c
if (age >= 18)
    printf("Eligible to vote\n");
else
    printf("Not eligible\n");
```

- **A (warning).** `if (x = 5)` assigns 5 and is always true. Use `==` to compare.
- **B. Else-if ladder: several conditions checked top to bottom; the first true one runs, the rest are skipped**
  - **Program: grade from marks**

```c
#include <stdio.h>
int main()
{
    int marks;
    printf("Enter marks (0-100): ");
    scanf("%d", &marks);
    if (marks < 0 || marks > 100)
        printf("Invalid marks\n");
    else if (marks >= 90)
        printf("Grade A\n");
    else if (marks >= 75)
        printf("Grade B\n");
    else if (marks >= 60)
        printf("Grade C\n");
    else if (marks >= 40)
        printf("Grade D\n");
    else
        printf("Grade F (Fail)\n");
    return 0;
}
```

- **B (output).** Input `78` → `Grade B`. (78 ≥ 90? No. 78 ≥ 75? Yes → stop.)
  - **Program: income tax by slabs** (example slabs used in textbook questions; not current tax law)
    - Up to ₹2,50,000: nil. ₹2,50,001–5,00,000: 5% of the amount above 2.5 lakh. ₹5,00,001–10,00,000: ₹12,500 + 20% above 5 lakh. Above ₹10,00,000: ₹1,12,500 + 30% above 10 lakh.

```c
#include <stdio.h>
int main()
{
    float income, tax;
    printf("Enter annual income: ");
    scanf("%f", &income);
    if (income <= 250000)
        tax = 0;
    else if (income <= 500000)
        tax = (income - 250000) * 0.05;
    else if (income <= 1000000)
        tax = 12500 + (income - 500000) * 0.20;
    else
        tax = 112500 + (income - 1000000) * 0.30;
    printf("Tax = %.2f\n", tax);
    return 0;
}
```

- **B (output).** Input `700000` → `Tax = 52500.00` (12,500 + 20% of 2,00,000).
- **C. Nested if: an if inside another if**

```c
if (a > b)
{
    if (a > c)  printf("a is largest");
    else        printf("c is largest");
}
else
{
    if (b > c)  printf("b is largest");
    else        printf("c is largest");
}
```

- **D. Nested if vs multiple (separate) ifs**
  - Multiple ifs: each if is independent and **every** condition is checked.

```c
if (n > 0)  printf("Positive\n");
if (n < 0)  printf("Negative\n");
if (n == 0) printf("Zero\n");      /* all three tests always run */
```

| Point | Nested if | Multiple separate ifs |
| --- | --- | --- |
| Structure | An if inside another if's block | Several ifs one after another |
| Inner test runs | Only when the outer test is true | Every test always runs |
| Use when | Second question depends on the first answer | Conditions are independent |
| Efficiency | Skips needless tests | May do extra tests |
| Risk | Hard to read when deep; "dangling else" (an else pairs with the nearest unmatched if) | More than one block may run |

- **E. switch: choose one case from exact values**
  - Syntax rules:
    - The switch expression must be an **integer or char** (not float, not a string).
    - Each `case` label is a constant: `case 1:` or `case '+':`. No ranges, no duplicates.
    - **break** ends the switch. Without it, execution "falls through" into the next case.
    - **default** runs when no case matches (optional, can be anywhere).
  - **Program: simple calculator**

```c
#include <stdio.h>
int main()
{
    float a, b;
    char op;
    printf("Enter expression (e.g. 8 * 2): ");
    scanf("%f %c %f", &a, &op, &b);
    switch (op)
    {
        case '+': printf("Result = %.2f\n", a + b); break;
        case '-': printf("Result = %.2f\n", a - b); break;
        case '*': printf("Result = %.2f\n", a * b); break;
        case '/':
            if (b != 0) printf("Result = %.2f\n", a / b);
            else        printf("Error: division by zero\n");
            break;
        default:  printf("Invalid operator\n");
    }
    return 0;
}
```

- **E (output).** Input `8 * 2` → `Result = 16.00`. Input `9 / 0` → `Error: division by zero`.
  - Fall-through example (no break): with `case 1: printf("One "); case 2: printf("Two ");`, choosing 1 prints `One Two`.
  - Other common switch programs: day of the week from 1–7, vowel or consonant, month name.
- **F. switch vs else-if ladder**

| Point | switch | else-if ladder |
| --- | --- | --- |
| Tests | Equality with constant values only | Any condition: ranges, &&, \|\|, floats |
| Data types | int and char only | Any type |
| Readability with many options | Very clean | Gets long |
| Speed with many cases | Often faster (compiler can jump directly) | Checks each condition in turn |
| Missing break | Falls through to next case | Not applicable |
| Best example | Calculator, menu, day names | Grades, tax slabs |

**Exam tip:** for a grade or tax program use an else-if ladder (ranges); for a menu or calculator use switch with break in every case and a default. Show one sample input and output.

## 7. Pointers: declaration, use, characteristics (6/8) · Understand

A pointer is a variable that stores the memory address of another variable: & gives a variable's address, and \* placed before a pointer reaches the value stored at that address. Pointers make call by reference, arrays, strings, dynamic memory and files work.

- **A. Memory and addresses**
  - Memory is a long row of numbered boxes. The box number is its **address**.
  - `int x = 10;` puts 10 in some box, say address 1000.
  - **&x** = "address of x" = 1000.
- **B. Declaring and using a pointer**
  - `int *p;` declares p as a **pointer to int** (p will hold the address of an int).
  - `p = &x;` stores x's address in p. Now "p points to x".
  - `*p` = "the value at the address in p" = 10. This is called **dereferencing**; \* here is the **indirection** operator.
  - `*p = 20;` changes x to 20, through the pointer.

```
      x                         p
  +--------+               +--------+
  |   10   |  <----------  |  1000  |
  +--------+               +--------+
  address 1000             address 2000
```

- **C. Program: pointer basics**

```c
#include <stdio.h>
int main()
{
    int x = 10;
    int *p;                    /* p can hold the address of an int */
    p = &x;                    /* p now points to x */

    printf("Value of x      = %d\n", x);
    printf("Address of x    = %p\n", (void *)&x);
    printf("Value of p      = %p\n", (void *)p);   /* same address */
    printf("Value at *p     = %d\n", *p);          /* 10 */

    *p = 20;                   /* change x through p */
    printf("New value of x  = %d\n", x);           /* 20 */
    return 0;
}
```

- **C (output).** Addresses differ on every computer; a sample run:

```
Value of x      = 10
Address of x    = 0x7ffd5c2a1b4c
Value of p      = 0x7ffd5c2a1b4c
Value at *p     = 10
New value of x  = 20
```

- **D. Characteristics of pointers (the "features" question)**
  1. A pointer stores an **address**, not an ordinary value.
  2. Its type must match the data it points to: int \* for int, char \* for char, float \* for float.
  3. All pointers have the **same size** on a given system (usually 8 bytes on 64-bit, 4 on 32-bit, 2 on old Turbo C), whatever they point to.
  4. **NULL pointer**: `int *p = NULL;` points nowhere. Good starting value; always check before use.
  5. **Pointer arithmetic**: p + 1 moves forward by the size of one item, not by one byte. For int (4 bytes), address 1000 + 1 → 1004.
  6. Allowed arithmetic: add or subtract an integer, subtract two pointers into the same array, compare pointers. Not allowed: adding, multiplying or dividing two pointers.
  7. **Arrays and pointers are linked**: an array name is the address of its first element, so a\[i\] is the same as \*(a + i).
  8. **Pointer to pointer**: `int **pp = &p;` then \*\*pp is x's value.
  9. **void pointer** (generic): `void *v;` can hold any address but must be cast before dereferencing. malloc returns void \*.
  10. Dangers: an **uninitialised (wild)** pointer points at random memory; a **dangling** pointer points to memory already freed. Both can crash the program.
- **E. Pointer arithmetic with an array**

```c
int a[3] = {10, 20, 30};
int *p = a;          /* same as p = &a[0] */
printf("%d\n", *p);        /* 10 */
printf("%d\n", *(p + 1));  /* 20 */
p++;                       /* move to next element */
printf("%d\n", *p);        /* 20 */
```

- **F. Program: sum of array elements using a pointer**

```c
#include <stdio.h>
int main()
{
    int a[5] = {4, 8, 15, 16, 23};
    int *p, sum = 0;
    for (p = a; p < a + 5; p++)     /* walk the array with the pointer */
        sum += *p;
    printf("Sum = %d\n", sum);
    return 0;
}
```

- **F (output).** `Sum = 66`
- **G. Uses and advantages**
  - Call by reference: let a function change the caller's variables (topic 9), e.g. swap.
  - Return more than one value from a function.
  - Dynamic memory allocation (topic 16).
  - Efficient handling of arrays and strings.
  - Building data structures: linked lists, trees.
  - File handling (FILE \*fp, topic 2).
- **H. Disadvantages**: errors are hard to find; wrong pointers can crash the program or corrupt data; forgetting free() causes memory leaks.
- **I. Two meanings of \* (common confusion)**

| Where | Meaning | Example |
| --- | --- | --- |
| In a declaration | "this variable is a pointer" | int \*p; |
| In an expression | "value at this address" | y = \*p; |
| Between two values | Multiplication | z = a \* b; |

**Exam tip:** draw the box diagram (x with its address, p holding that address) whenever pointers are asked. It explains & and \* in one picture.

## 8. Recursion: recursive factorial and Fibonacci (5/8) · Practise

Recursion is a function calling itself on a smaller version of the same problem until it reaches a base case it can answer directly; factorial uses fact(n) = n × fact(n − 1) with fact(0) = 1, and Fibonacci uses fib(n) = fib(n − 1) + fib(n − 2) with fib(0) = 0, fib(1) = 1.

- **A. The idea**
  - Solve a big problem by trusting the same function to solve a slightly smaller one.
  - Russian dolls: open a doll, find a smaller doll, repeat until the tiniest solid doll (the base case).
  - Every recursive function needs two parts:
    1. **Base case**: a simple input answered directly, which stops the recursion.
    2. **Recursive case**: the function calls itself with a smaller input, moving towards the base case.
  - No base case → the function calls itself forever until memory runs out (**stack overflow**).
- **B. Program 1: factorial using recursion**
  - Maths: 5! = 5 × 4 × 3 × 2 × 1 = 120, and 0! = 1.
  - Recursive definition: fact(n) = 1 if n is 0 or 1; otherwise n × fact(n − 1).

```c
#include <stdio.h>

long fact(int n)
{
    if (n <= 1)                /* base case */
        return 1;
    return n * fact(n - 1);    /* recursive case */
}

int main()
{
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    if (n < 0)
        printf("Factorial of a negative number is not defined\n");
    else
        printf("Factorial of %d = %ld\n", n, fact(n));
    return 0;
}
```

- **B (output).** Input `5` → `Factorial of 5 = 120`.
- **C. How the computer runs fact(4): the call stack**
  - Each call waits for the one below it. Calls pile up ("winding"), then answers come back up ("unwinding").

```
fact(4) = 4 * fact(3)                 waits
          fact(3) = 3 * fact(2)       waits
                    fact(2) = 2 * fact(1)   waits
                              fact(1) = 1   base case
                    fact(2) = 2 * 1 = 2     returns
          fact(3) = 3 * 2 = 6               returns
fact(4) = 4 * 6 = 24                        answer
```

- **D. Program 2: Fibonacci series using recursion**
  - Series: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34 … Each term is the sum of the two before it.
  - Recursive definition: fib(0) = 0, fib(1) = 1, fib(n) = fib(n − 1) + fib(n − 2).

```c
#include <stdio.h>

int fib(int n)
{
    if (n == 0) return 0;          /* base case 1 */
    if (n == 1) return 1;          /* base case 2 */
    return fib(n - 1) + fib(n - 2);
}

int main()
{
    int n, i;
    printf("How many terms? ");
    scanf("%d", &n);
    printf("Fibonacci series: ");
    for (i = 0; i < n; i++)
        printf("%d ", fib(i));
    printf("\n");
    return 0;
}
```

- **D (output).** Input `8` → `Fibonacci series: 0 1 1 2 3 5 8 13`
- **E. Call tree for fib(4)**

```
                fib(4)
              /        \
         fib(3)          fib(2)
        /      \         /     \
    fib(2)   fib(1)   fib(1)  fib(0)
    /    \
 fib(1) fib(0)
```

- **E (reading it).** fib(4) = 3. The tree makes 9 calls, and fib(2) is worked out twice. This repeated work makes recursive Fibonacci very slow for large n (the number of calls roughly doubles with each extra n).
- **F. Other short recursive programs (same pattern)**
  - Sum of first n numbers: `sum(n) = (n == 0) ? 0 : n + sum(n - 1);`
  - Power: `power(x, n) = (n == 0) ? 1 : x * power(x, n - 1);`
  - Sum of digits: `sod(n) = (n == 0) ? 0 : n % 10 + sod(n / 10);`
  - GCD: `gcd(a, b) = (b == 0) ? a : gcd(b, a % b);`
- **G. Recursion vs iteration (loops)**

| Point | Recursion | Iteration (loop) |
| --- | --- | --- |
| How it repeats | Function calls itself | for / while / do-while |
| Stops when | Base case is reached | Loop condition becomes false |
| Memory | Uses stack space for every call | Little extra memory |
| Speed | Slower (call overhead) | Faster |
| Code | Short and close to the maths definition | Often longer |
| Risk | Stack overflow if no base case | Infinite loop if condition never false |
| Good for | Trees, Tower of Hanoi, divide-and-conquer | Simple counting and repetition |

**Exam tip:** always mark the base case with a comment, and for theory show the fact(4) stack picture. If asked "factorial without recursion", use a loop: `for (i = 1; i <= n; i++) f = f * i;`

## 9. Call by value vs call by reference (5/8) · Understand

In call by value the function gets a copy of the variable, so its changes do not affect the original; in call by reference the function gets the variable's address (a pointer), so it can change the original. The swap program shows the difference: swapping by value fails, swapping by reference works.

- **A. Two words first**
  - **Actual arguments**: the values written in the call, e.g. a, b in `swap(a, b);`.
  - **Formal parameters**: the variables in the function heading, e.g. x, y in `void swap(int x, int y)`.
- **B. Call by value**
  - The **values** of the actual arguments are **copied** into the formal parameters.
  - The function works on its copies. The caller's variables are untouched.
  - Like giving a friend a photocopy: they can scribble on it, your original stays clean.

```c
#include <stdio.h>

void swap(int x, int y)       /* x, y are copies */
{
    int t = x;
    x = y;
    y = t;
    printf("Inside swap: x = %d, y = %d\n", x, y);
}

int main()
{
    int a = 10, b = 20;
    swap(a, b);               /* pass values */
    printf("In main:     a = %d, b = %d\n", a, b);
    return 0;
}
```

```
Inside swap: x = 20, y = 10
In main:     a = 10, b = 20
```

- **B (why).** Only the copies x and y were swapped. a and b in main did not change.
- **C. Call by reference (using pointers)**
  - The **addresses** of the actual arguments are passed (using &). The formal parameters are pointers.
  - Through \* the function reaches and changes the original variables.
  - Like giving a friend your house key: what they change is changed in your house.

```c
#include <stdio.h>

void swap(int *x, int *y)     /* x, y hold addresses of a, b */
{
    int t = *x;
    *x = *y;
    *y = t;
}

int main()
{
    int a = 10, b = 20;
    swap(&a, &b);             /* pass addresses */
    printf("In main: a = %d, b = %d\n", a, b);
    return 0;
}
```

```
In main: a = 20, b = 10
```

- **D. Memory picture**

```
Call by value:                     Call by reference:
 main: a=10  b=20                   main: a=10 (addr 1000)  b=20 (addr 1004)
         |     |  (copied)                     ^              ^
 swap:  x=10  y=20                  swap:  x=1000 ---+      y=1004 ---+
 (swapping x, y leaves a, b alone)  (*x and *y ARE a and b)
```

- **E. Comparison (memorise)**

| Point | Call by value | Call by reference |
| --- | --- | --- |
| What is passed | Copy of the value | Address of the variable |
| Formal parameters | Ordinary variables (int x) | Pointers (int \*x) |
| Call looks like | swap(a, b) | swap(&a, &b) |
| Changes inside function affect caller? | No | Yes |
| Memory | Extra copy of each argument | Only an address is copied |
| Safety | Original data protected | Original can be changed by mistake |
| Use when | Function only needs to read values | Function must change values, or return several results, or data is large (arrays, structures) |
| Example | square(n), printing | swap, reading into several variables (scanf uses this!) |

- **F. Notes worth one mark each**
  - Strictly, C always passes by value; "call by reference" in C means passing the **value of an address** (a pointer).
  - Arrays are always passed by reference automatically: the array name is an address, so a function can change array elements.
  - scanf("%d", &n) is call by reference in action: scanf needs n's address to store the input.

**Exam tip:** write both swap programs side by side with their outputs; the different outputs are the whole answer. Then add the comparison table.

## 10. User-defined functions: writing functions (swap, square, nCr) and categories of functions (5/8) · Practise

A function is a named, reusable block of code that does one job; you declare it (prototype), define it (body), and call it. Functions fall into four categories depending on whether they take arguments and whether they return a value.

- **A. Why use functions**
  - Write once, use many times (no repeated code).
  - Break a big program into small, understandable pieces (**modular programming**).
  - Easier to test and fix: an error is inside one small function.
  - **Library functions** come ready-made (printf, sqrt, strlen). **User-defined functions** are written by you.
- **B. The three parts of a user-defined function**
  1. **Declaration (prototype)**: tells the compiler the name, return type and parameter types. Ends with ;.
     - `int square(int n);`
  2. **Definition**: the actual body.
     - `int square(int n) { return n * n; }`
  3. **Call**: uses it.
     - `y = square(5);`  → y becomes 25.
  - **return** sends a value back and ends the function. A function that returns nothing has return type **void**.
- **C. Program 1: square of a number**

```c
#include <stdio.h>

int square(int n);             /* 1. declaration */

int main()
{
    int x;
    printf("Enter a number: ");
    scanf("%d", &x);
    printf("Square = %d\n", square(x));   /* 3. call */
    return 0;
}

int square(int n)              /* 2. definition */
{
    return n * n;
}
```

- **C (output).** Input `7` → `Square = 49`.
- **D. Program 2: nCr (combinations) using a factorial function**
  - Formula: nCr = n! / ( r! × (n − r)! ). Example: 5C2 = 120 / (2 × 6) = 10.

```c
#include <stdio.h>

long fact(int n)
{
    long f = 1;
    int i;
    for (i = 2; i <= n; i++)
        f = f * i;
    return f;
}

long nCr(int n, int r)
{
    return fact(n) / (fact(r) * fact(n - r));
}

int main()
{
    int n, r;
    printf("Enter n and r: ");
    scanf("%d %d", &n, &r);
    if (r < 0 || r > n)
        printf("Invalid input: need 0 <= r <= n\n");
    else
        printf("%dC%d = %ld\n", n, r, nCr(n, r));
    return 0;
}
```

- **D (output).** Input `5 2` → `5C2 = 10`. (Note how one function, nCr, calls another, fact.)
- **E. Program 3: swap two numbers** (uses pointers; see topic 9 for the full explanation)
  - `void swap(int *x, int *y) { int t = *x; *x = *y; *y = t; }`, called as `swap(&a, &b);`
- **F. Categories of functions (memorise with one example each)**

| Category | Takes arguments? | Returns a value? | Example prototype | What it does |
| --- | --- | --- | --- | --- |
| 1 | No | No | void greet(void); | Prints a fixed message |
| 2 | Yes | No | void printSum(int a, int b); | Prints a + b itself |
| 3 | No | Yes | int readNumber(void); | Reads a number and returns it |
| 4 | Yes | Yes | int add(int a, int b); | Returns a + b to the caller |

- **F (all four in one program).**

```c
#include <stdio.h>

void greet(void)               { printf("Hello!\n"); }            /* 1 */
void printSum(int a, int b)    { printf("Sum = %d\n", a + b); }  /* 2 */
int  readNumber(void)          { int n; scanf("%d", &n); return n; } /* 3 */
int  add(int a, int b)         { return a + b; }                  /* 4 */

int main()
{
    int x, y;
    greet();
    printf("Enter two numbers: ");
    x = readNumber();
    y = readNumber();
    printSum(x, y);
    printf("add() returned %d\n", add(x, y));
    return 0;
}
```

- **F (output).** Input `3 4` →

```
Hello!
Enter two numbers: Sum = 7
add() returned 7
```

- **G. Key terms**
  - **Actual vs formal arguments**: values in the call vs variables in the definition.
  - **Local variable**: declared inside a function; exists only there.
  - **Global variable**: declared outside all functions; usable everywhere.
  - **Nesting of functions**: one function calling another (nCr calls fact).
  - **Recursive function**: one that calls itself (topic 8).

**Exam tip:** always show all three parts (prototype, call in main, definition). For "categories", the four-row table plus a one-line example each gets full marks.

## 11. Structure vs union (5/8) · Memorise

A structure gives every member its own memory, so all members hold values at once and its size is at least the sum of the members; a union makes all members share one memory area, so only one member holds a valid value at a time and its size is that of the largest member. (Topic 12 covers structures in detail.)

- **A. Structure in one line**: a user-defined type grouping related items of different types, e.g. a student's roll number, name and marks.
- **B. Union in one line**: declared exactly like a structure, but with the keyword `union`; all members share the same memory.
- **C. Declaration side by side**

```c
struct Item          union Item
{                    {
    int   i;             int   i;
    float f;             float f;
    char  c;             char  c;
};                   };
```

- **D. Memory picture** (int and float 4 bytes, char 1 byte)

```
structure: | i i i i | f f f f | c | (padding) |   total 12 bytes (9 + padding)
union:     | i i i i |                              total 4 bytes
             f f f f   <- same 4 bytes
             c         <- first byte of the same 4 bytes
```

- **E. Program showing the difference**

```c
#include <stdio.h>

struct S { int i; float f; char c; };
union  U { int i; float f; char c; };

int main()
{
    struct S s;
    union U u;

    printf("Size of structure = %d bytes\n", (int)sizeof(struct S));
    printf("Size of union     = %d bytes\n", (int)sizeof(union U));

    s.i = 10; s.f = 2.5; s.c = 'A';
    printf("Structure: %d %.1f %c\n", s.i, s.f, s.c);   /* all three correct */

    u.i = 10;
    printf("Union i = %d\n", u.i);      /* 10: correct, i was stored last */
    u.f = 2.5;                          /* overwrites the same memory */
    printf("Union f = %.1f\n", u.f);    /* 2.5: correct */
    printf("Union i = %d\n", u.i);      /* no longer 10: garbage */
    return 0;
}
```

- **E (output on a typical 64-bit compiler).**

```
Size of structure = 12 bytes
Size of union     = 4 bytes
Structure: 10 2.5 A
Union i = 10
Union f = 2.5
Union i = 1075838976
```

- **E (reading it).** The last line is meaningless: writing f destroyed the old i, because they share memory. The structure kept all three values.
- **F. Comparison table (memorise)**

| Point | Structure | Union |
| --- | --- | --- |
| Keyword | struct | union |
| Memory | Each member gets its own space | All members share one space |
| Size | Sum of members (+ padding) | Size of the largest member |
| Values held at once | All members | Only one member (the last one written) |
| Changing one member | Does not affect others | Overwrites the others |
| Initialisation | All members can be initialised: {10, 2.5, 'A'} | Only the first member (C89), e.g. {10} |
| Memory use | More | Less (saves memory) |
| Use when | You need all fields together (student record) | Only one of several fields is needed at a time (a value that may be int OR float) |
| Member access | . and -> | . and -> (same) |

- **G. Similarities (sometimes asked)**: both are user-defined types; both are declared and accessed the same way (. and ->); both can contain arrays, pointers and other structures/unions; both can be passed to functions.

**Exam tip:** draw the memory picture with byte boxes; it explains size, sharing and the "one value at a time" rule in a single diagram.

## 12. Structures: declaration and programs (employee salary, student records) (5/8) · Practise

A structure bundles related data of different types under one name (like a form with fields); you declare the template once, create variables of it, and reach each field with a dot, e.g. s.marks. An array of structures holds many records, which is how the employee-salary and student-record programs work.

- **A. Why structures?**
  - An array holds many items of the **same** type. A student record needs **different** types together: roll (int), name (char array), percentage (float).
  - A structure is a **user-defined data type** that groups them.
- **B. Declaring a structure (the template)**

```c
struct student
{
    int   roll;
    char  name[30];
    float marks;
};                       /* note the semicolon */
```

- **B (meaning).**
  - `struct student` is the new type's name (the **tag**); roll, name, marks are its **members** (fields).
  - This only describes the shape. No memory is used until you create a variable.
- **C. Variables, initialisation and access**
  - Create: `struct student s1, s2;`
  - Initialise: `struct student s1 = {101, "Asha", 88.5};` (in member order)
  - Access with the **dot operator**: `s1.roll = 101;`, `printf("%s", s1.name);`
  - Read input: `scanf("%d %s %f", &s1.roll, s1.name, &s1.marks);` (no & for the name array)
  - Copy a whole structure: `s2 = s1;` (allowed). Compare with == is **not** allowed; compare members one by one.
- **D. Related features**
  - **Array of structures**: `struct student s[50];` then `s[i].roll`.
  - **Nested structure**: a structure inside another.
    - `struct date { int d, m, y; };` and inside employee: `struct date doj;` → access `e.doj.y`.
  - **Pointer to structure** uses the arrow operator: `struct student *p = &s1;` then `p->roll` (same as `(*p).roll`).
  - **typedef** gives a short name: `typedef struct student Student;` then `Student s1;`
  - **Passing to functions**: by value (`void show(struct student s)`) or by address (`void update(struct student *p)`).
- **E. Program 1: employee salary for n employees**
  - Example rules: DA = 40% of basic, HRA = 20% of basic, gross = basic + DA + HRA.

```c
#include <stdio.h>

struct employee
{
    int   id;
    char  name[30];
    float basic, da, hra, gross;
};

int main()
{
    struct employee e[20];
    int n, i;
    printf("How many employees? ");
    scanf("%d", &n);

    for (i = 0; i < n; i++)
    {
        printf("Enter id, name and basic salary of employee %d: ", i + 1);
        scanf("%d %29s %f", &e[i].id, e[i].name, &e[i].basic);
        e[i].da    = 0.40 * e[i].basic;
        e[i].hra   = 0.20 * e[i].basic;
        e[i].gross = e[i].basic + e[i].da + e[i].hra;
    }

    printf("\nID   Name       Basic      DA        HRA       Gross\n");
    for (i = 0; i < n; i++)
        printf("%-4d %-10s %-10.2f %-9.2f %-9.2f %.2f\n",
               e[i].id, e[i].name, e[i].basic, e[i].da, e[i].hra, e[i].gross);
    return 0;
}
```

- **E (sample run).** Input: 2 employees, `1 Ravi 20000` and `2 Meena 30000`

```
ID   Name       Basic      DA        HRA       Gross
1    Ravi       20000.00   8000.00   4000.00   32000.00
2    Meena      30000.00   12000.00  6000.00   48000.00
```

- **F. Program 2: student records with total, percentage and topper**

```c
#include <stdio.h>

struct student
{
    int   roll;
    char  name[30];
    int   m[3];          /* marks in 3 subjects */
    int   total;
    float percent;
};

int main()
{
    struct student s[50];
    int n, i, j, top = 0;
    printf("Number of students: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++)
    {
        printf("Roll, name, marks in 3 subjects: ");
        scanf("%d %29s", &s[i].roll, s[i].name);
        s[i].total = 0;
        for (j = 0; j < 3; j++)
        {
            scanf("%d", &s[i].m[j]);
            s[i].total += s[i].m[j];
        }
        s[i].percent = s[i].total / 3.0;
        if (s[i].total > s[top].total)
            top = i;                     /* remember the highest scorer */
    }

    printf("\nRoll  Name      Total  Percent\n");
    for (i = 0; i < n; i++)
        printf("%-5d %-9s %-6d %.2f\n", s[i].roll, s[i].name, s[i].total, s[i].percent);
    printf("Topper: %s with %d marks\n", s[top].name, s[top].total);
    return 0;
}
```

- **F (sample run).** Input: 2 students, `1 Asha 80 90 85` and `2 Vikram 70 75 80`

```
Roll  Name      Total  Percent
1     Asha      255    85.00
2     Vikram    225    75.00
Topper: Asha with 255 marks
```

- **G. Common mistakes**
  - Forgetting the semicolon after the closing brace of the structure.
  - Writing `&` before a char-array member in scanf.
  - Using `->` with a plain structure variable (use `.`), or `.` with a pointer (use `->`).

**Exam tip:** declare the structure above main, use an array of structures with a loop for input and a loop for output, and print a neat table. Examiners reward the table layout.

## 13. Storage classes: auto, extern, static, register (5/8) · Memorise

A storage class tells C four things about a variable: where it is stored, its default starting value, where in the program it can be used (scope), and how long it lives (lifetime). Learn the four-row table below; static's "keeps its value between calls" is the most-tested idea.

- **A. The four questions every storage class answers**
  - **Storage**: RAM (memory) or a CPU register.
  - **Default value**: what it holds if you do not initialise it (garbage or 0).
  - **Scope**: which part of the program can see it (the block/function, or the whole program).
  - **Lifetime**: how long it exists (until its block ends, or until the program ends).
- **B. The master table (memorise)**

| Storage class | Keyword | Stored in | Default value | Scope | Lifetime |
| --- | --- | --- | --- | --- | --- |
| Automatic | auto | Memory (stack) | Garbage | Local to its block | Until the block ends |
| Register | register | CPU register (if one is free) | Garbage | Local to its block | Until the block ends |
| Static | static | Memory (data area) | 0 | Local to its block (or file, if declared outside functions) | Whole program run |
| External | extern | Memory (data area) | 0 | Global: whole program, even other files | Whole program run |

- **C. auto**
  - The default for every variable declared inside a function: `int x;` is the same as `auto int x;`.
  - Created each time the block starts, destroyed when it ends.
- **D. register**
  - `register int i;` asks the compiler to keep i in a fast CPU register (good for loop counters).
  - Only a request; the compiler may ignore it.
  - You **cannot** take its address: `&i` is not allowed.
- **E. static (local)**
  - Created once, initialised **once**, and **keeps its value between function calls**.

```c
#include <stdio.h>

void counter()
{
    auto   int a = 0;    /* re-created as 0 on every call */
    static int s = 0;    /* initialised only once */
    a++;
    s++;
    printf("auto a = %d, static s = %d\n", a, s);
}

int main()
{
    counter();
    counter();
    counter();
    return 0;
}
```

```
auto a = 1, static s = 1
auto a = 1, static s = 2
auto a = 1, static s = 3
```

- **E (reading it).** a starts again at 0 every call; s remembers its last value. Uses: counting how many times a function is called; remembering state between calls.
  - A **static global** variable or function (declared outside all functions) is visible only inside its own file.
- **F. extern**
  - A **global** variable is declared outside all functions. `extern` says "this variable is defined somewhere else (later in this file or in another file); use that one". It declares without creating new memory.

```c
#include <stdio.h>

extern int total;          /* declaration: defined below */

void add(int x)
{
    total += x;
}

int main()
{
    add(5);
    add(10);
    printf("total = %d\n", total);
    return 0;
}

int total = 0;             /* definition: memory created here */
```

- **F (output).** `total = 15`
  - Main use: sharing one global variable across several .c files of a big program.
- **G. Quick memory hooks**
  - **auto**: "automatic, comes and goes".
  - **register**: "racing car: fast, but no address".
  - **static**: "stays": keeps its value.
  - **extern**: "external: borrowed from elsewhere".
  - Default value: auto and register → garbage; static and extern → 0.

**Exam tip:** reproduce the master table first, then give the static counter program with its output. Those two together answer almost every storage-class question.

## 14. Operators: categories, relational and logical, precedence, sizeof (5/8) · Memorise

Operators are symbols that act on values (operands); C groups them into arithmetic, relational, logical, assignment, increment/decrement, conditional, bitwise and special operators. Precedence decides which operator acts first (\* before +), and associativity breaks ties (mostly left to right).

- **A. Words to know**
  - In `a + b`, + is the **operator**; a and b are **operands**.
  - **Unary** operators take one operand (-x, ++i, !flag). **Binary** take two (a + b). The only **ternary** operator takes three (a ? b : c).
- **B. The eight categories (memorise with one example each)**

| Category | Operators | Example | Result (a = 7, b = 2) |
| --- | --- | --- | --- |
| Arithmetic | + − \* / % | a / b, a % b | 3 (integer division drops .5), 1 (remainder) |
| Relational | < <= > >= == != | a > b | 1 (true) |
| Logical | && \|\| ! | (a > 5) && (b > 5) | 0 (false) |
| Assignment | = += −= \*= /= %= | a += b | a becomes 9 |
| Increment / decrement | ++ −− | a++ | a becomes 8 (topic 23) |
| Conditional (ternary) | ? : | (a > b) ? a : b | 7 (topic 19) |
| Bitwise | & \| ^ \~ << >> | a & b, a << 1 | 2 (0111 & 0010), 14 |
| Special | sizeof, comma, & (address), \* (pointer), . and -> (members) | sizeof(int) | 4 on most systems |

- **C. Arithmetic notes**
  - int / int gives an int: 7 / 2 = 3. For 3.5 write 7.0 / 2 or (float)7 / 2.
  - % works only on integers: 7 % 2 = 1, 10 % 5 = 0. Use it to test even/odd and to pull out digits (n % 10).
- **D. Relational and logical operators**
  - Relational operators compare and give **1 (true)** or **0 (false)**: 5 == 5 → 1, 5 != 5 → 0.
  - Logical operators combine conditions:

| A | B | A && B (AND) | A \|\| B (OR) | !A (NOT) |
| --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 |

- **D (short-circuit).** In A && B, if A is false, B is never checked. In A || B, if A is true, B is never checked.
  - Example: `if (n != 0 && 10 / n > 2)` is safe: the division never runs when n is 0.
  - Do not confuse: = assigns, == compares; & is bitwise AND, && is logical AND.
- **E. Precedence and associativity (high to low)**

| Level | Operators | Associativity |
| --- | --- | --- |
| 1 (highest) | () \[\] -> . | Left to right |
| 2 | Unary: ! \~ ++ −− + − \* & (type) sizeof | Right to left |
| 3 | \* / % | Left to right |
| 4 | + − | Left to right |
| 5 | << >> | Left to right |
| 6 | < <= > >= | Left to right |
| 7 | == != | Left to right |
| 8 | & | Left to right |
| 9 | ^ | Left to right |
| 10 | \| | Left to right |
| 11 | && | Left to right |
| 12 | \|\| | Left to right |
| 13 | ?: | Right to left |
| 14 | = += −= \*= /= %= etc. | Right to left |
| 15 (lowest) | , (comma) | Left to right |

- **E (memory line).** "**U**nary, **A**rithmetic, **S**hift, **R**elational, **E**quality, **B**itwise, **L**ogical, **C**onditional, **A**ssignment, **C**omma".
- **F. Worked expressions**

| Expression | Steps | Value |
| --- | --- | --- |
| 2 + 3 \* 4 | \* first: 2 + 12 | 14 |
| (2 + 3) \* 4 | brackets first: 5 \* 4 | 20 |
| 10 − 4 − 3 | left to right: 6 − 3 | 3 |
| 10 / 3 \* 3 | left to right: 3 \* 3 | 9 |
| 20 % 6 + 2 \* 3 | 2 + 6 | 8 |
| 5 > 3 && 2 > 4 | 1 && 0 | 0 |
| 3 + 4 > 6 \|\| 0 | 7 > 6 is 1; 1 \|\| 0 | 1 |
| !(5 == 5) | !1 | 0 |
| a = b = 5 | right to left: b = 5, then a = 5 | both 5 |

- **G. The sizeof operator**
  - Gives the size **in bytes** of a type or variable. It is an operator, not a function, and is worked out at compile time.

```c
#include <stdio.h>
int main()
{
    int a[10];
    printf("char   : %d\n", (int)sizeof(char));
    printf("int    : %d\n", (int)sizeof(int));
    printf("float  : %d\n", (int)sizeof(float));
    printf("double : %d\n", (int)sizeof(double));
    printf("array a: %d\n", (int)sizeof(a));
    printf("elements in a: %d\n", (int)(sizeof(a) / sizeof(a[0])));
    return 0;
}
```

```
char   : 1
int    : 4
float  : 4
double : 8
array a: 40
elements in a: 10
```

- **G (note).** Sizes can differ by system: old Turbo C gives int = 2, so a would be 20 bytes there. char is always 1.
- **H. Type conversion (often a sub-question)**
  - **Implicit**: C converts automatically to the bigger type in mixed expressions: 5 + 2.5 → 7.5 (int becomes double).
  - **Explicit (type cast)**: you force it: `(float)7 / 2` → 3.5.

**Exam tip:** for a precedence question, rewrite the expression adding brackets in the order C applies them, then evaluate step by step. Always say "1 means true, 0 means false" for relational and logical results.

## 15. Array programs: linear search, largest and smallest, sorting (5/8) · Practise

All array programs follow one pattern: read n values into a\[0\] to a\[n−1\] with a loop, then make one more pass with a loop that compares or swaps. Learn linear search, largest/smallest and bubble sort below; topic 21 explains array declaration itself.

- **A. The reading loop used by every program**

```c
printf("Enter number of elements: ");
scanf("%d", &n);
printf("Enter %d elements: ", n);
for (i = 0; i < n; i++)
    scanf("%d", &a[i]);
```

- **A (remember).** Indexes run from 0 to n − 1, so the loop condition is `i < n`, not `i <= n`.
- **B. Program 1: linear search**
  - Compare the key with each element in turn. Stop when found.

```c
#include <stdio.h>
int main()
{
    int a[100], n, i, key, pos = -1;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements: ", n);
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter element to search: ");
    scanf("%d", &key);

    for (i = 0; i < n; i++)
    {
        if (a[i] == key)
        {
            pos = i;
            break;              /* found: stop searching */
        }
    }

    if (pos == -1)
        printf("%d not found\n", key);
    else
        printf("%d found at position %d\n", key, pos + 1);
    return 0;
}
```

- **B (output).** Elements `7 3 9 1 6`, key `9` → `9 found at position 3`. Key `5` → `5 not found`.
  - Best case 1 comparison (first element); worst case n comparisons (last element or missing).
- **C. Program 2: largest and smallest element**
  - Assume the first element is both largest and smallest, then let every other element challenge it.

```c
#include <stdio.h>
int main()
{
    int a[100], n, i, max, min;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements: ", n);
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    max = min = a[0];
    for (i = 1; i < n; i++)
    {
        if (a[i] > max) max = a[i];
        if (a[i] < min) min = a[i];
    }
    printf("Largest = %d, Smallest = %d\n", max, min);
    return 0;
}
```

- **C (trace for 7 3 9 1 6).** Start max = min = 7. 3: min = 3. 9: max = 9. 1: min = 1. 6: no change. Output `Largest = 9, Smallest = 1`.
  - Why not start max at 0? If all numbers are negative, 0 would wrongly win. Starting from a\[0\] is always safe.
- **D. Program 3: sort in ascending order (bubble sort)**
  - Compare neighbours and swap if the left one is bigger. After each pass the largest remaining value settles at the end.

```c
#include <stdio.h>
int main()
{
    int a[100], n, i, j, temp;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements: ", n);
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    for (i = 0; i < n - 1; i++)            /* passes */
        for (j = 0; j < n - 1 - i; j++)    /* compare neighbours */
            if (a[j] > a[j + 1])
            {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }

    printf("Sorted: ");
    for (i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```

- **D (trace for 5 1 4 2 8).**

| Pass | Array after the pass |
| --- | --- |
| 1 | 1 4 2 5 **8** |
| 2 | 1 2 4 **5 8** |
| 3 | 1 2 **4 5 8** |
| 4 | **1 2 4 5 8** |

- **D (notes).**
  - For **descending** order, change `>` to `<` in the comparison.
  - Comparisons: n(n − 1)/2; time grows as n².
- **E. Program 4 idea: selection sort (alternative)**
  - For each position i, find the smallest element from i to the end and swap it into position i.

```c
for (i = 0; i < n - 1; i++)
{
    int minPos = i;
    for (j = i + 1; j < n; j++)
        if (a[j] < a[minPos]) minPos = j;
    temp = a[i]; a[i] = a[minPos]; a[minPos] = temp;
}
```

- **F. Other quick array programs (same reading loop)**
  - Sum and average: `sum += a[i];` then `avg = (float)sum / n;`
  - Reverse print: `for (i = n - 1; i >= 0; i--) printf("%d ", a[i]);`
  - Count even numbers: `if (a[i] % 2 == 0) count++;`
  - Second largest: track `max` and `second`; when a\[i\] > max, second = max and max = a\[i\]; else if a\[i\] > second and a\[i\] != max, second = a\[i\].

**Exam tip:** always print the result clearly with a label, and mention best/worst case for search or sort if marks allow. Use `i < n` loops consistently.

## 16. Dynamic memory allocation: malloc and friends (4/8) · Understand

Dynamic memory allocation means asking for memory while the program is running, in exactly the amount needed; malloc(bytes) returns a pointer to a new block (or NULL if none is free), and free(pointer) gives it back. calloc also zero-fills, and realloc resizes.

- **A. The problem it solves**
  - `int a[100];` is **static allocation**: the size is fixed when you write the program.
    - Only 5 students? 95 boxes wasted. 150 students? Not enough room.
  - **Dynamic allocation**: ask for exactly n boxes after the user tells you n.
  - Dynamic memory comes from an area called the **heap**. It stays until you free it (ordinary local variables live on the **stack** and vanish when the function ends).
- **B. The four functions (in stdlib.h)**

| Function | Syntax | Does | Initial contents |
| --- | --- | --- | --- |
| malloc | p = (int \*) malloc(n \* sizeof(int)); | Allocates one block of the given bytes | Garbage |
| calloc | p = (int \*) calloc(n, sizeof(int)); | Allocates n blocks of given size | All zero |
| realloc | p = (int \*) realloc(p, newSize); | Grows or shrinks an existing block (keeps old data) | Old data kept, new part garbage |
| free | free(p); | Returns the block to the system | – |

- **B (the malloc line, piece by piece).** `p = (int *) malloc(n * sizeof(int));`
  - `n * sizeof(int)`: how many bytes are needed (n ints).
  - `malloc(...)`: reserves them and returns the starting address as a void pointer.
  - `(int *)`: type-casts it to an int pointer (needed in old C/Turbo C and C++; optional in modern C).
  - Then use p exactly like an array: `p[0]`, `p[1]` … or `*(p + i)`.
  - If memory is not available, malloc returns **NULL**: always check.
- **C. Program: read n numbers into dynamic memory and find their sum**

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int *p, n, i, sum = 0;
    printf("How many numbers? ");
    scanf("%d", &n);

    p = (int *) malloc(n * sizeof(int));     /* ask for n ints */
    if (p == NULL)
    {
        printf("Memory not available\n");
        return 1;
    }

    printf("Enter %d numbers: ", n);
    for (i = 0; i < n; i++)
    {
        scanf("%d", &p[i]);                  /* use like an array */
        sum += p[i];
    }
    printf("Sum = %d\n", sum);

    free(p);                                 /* give memory back */
    p = NULL;                                /* avoid a dangling pointer */
    return 0;
}
```

- **C (output).** Input `4` then `10 20 30 40` → `Sum = 100`.
- **D. Growing with realloc (short example)**

```c
p = (int *) realloc(p, 2 * n * sizeof(int));   /* now room for 2n ints */
if (p == NULL) { printf("Cannot grow\n"); }
```

- **E. malloc vs calloc (asked often)**

| Point | malloc | calloc |
| --- | --- | --- |
| Full name | Memory allocation | Contiguous (cleared) allocation |
| Arguments | One: total bytes | Two: number of items, size of each |
| Initial value | Garbage | Zero |
| Speed | Slightly faster | Slightly slower (clears memory) |
| Example | malloc(5 \* sizeof(int)) | calloc(5, sizeof(int)) |

- **F. Static vs dynamic allocation**

| Point | Static (int a\[100\]) | Dynamic (malloc) |
| --- | --- | --- |
| When size is fixed | At compile time | At run time |
| Memory area | Stack (for local variables) | Heap |
| Resizable? | No | Yes (realloc) |
| Freed | Automatically when scope ends | Manually with free() |
| Waste | Possible (unused boxes) | Minimal |
| Accessed via | Array name | Pointer |

- **G. Mistakes to avoid**
  - **Memory leak**: forgetting free(), so memory stays reserved until the program ends.
  - **Dangling pointer**: using p after free(p). Set p = NULL after freeing.
  - Not checking for NULL.
  - Freeing the same block twice.

**Exam tip:** write the malloc line with sizeof and the type cast, check for NULL, and end with free(p). Add the malloc vs calloc table if the question has more than 3 marks.

## 17. Loops: for vs while vs do-while (4/8) · Understand

A loop repeats a block of code while a condition stays true. for and while check the condition before each round (entry-controlled, may run zero times); do-while checks after each round (exit-controlled, always runs at least once).

- **A. Every loop has three parts**
  1. **Initialisation**: set the counter (i = 1).
  2. **Condition**: keep going while it is true (i <= 5).
  3. **Update**: change the counter (i++), so the loop eventually stops.
  - Forget the update and the condition never becomes false: an **infinite loop**.
- **B. Same job, three loops: print 1 to 5**

```c
/* for: all three parts on one line */
for (i = 1; i <= 5; i++)
    printf("%d ", i);

/* while: condition at the top */
i = 1;
while (i <= 5)
{
    printf("%d ", i);
    i++;
}

/* do-while: condition at the bottom, note the semicolon */
i = 1;
do
{
    printf("%d ", i);
    i++;
} while (i <= 5);
```

- **B (output of each).** `1 2 3 4 5`
- **C. The key difference: do-while runs at least once**

```c
int i = 10;
while (i < 5)  { printf("while ran\n"); }        /* prints nothing */
do { printf("do-while ran\n"); } while (i < 5);   /* prints once */
```

- **C (output).** `do-while ran` (only once; the while loop never ran because 10 < 5 was false at the start).
- **D. Flow pictures**

```
  while / for (entry-controlled)        do-while (exit-controlled)

        +---------+                         +---------+
   +--> |condition|--false--> exit     +--> |  body   |
   |    +---------+                    |    +---------+
   |         | true                    |         |
   |    +---------+                    |    +---------+
   +--- |  body   |                    +true|condition|--false--> exit
        +---------+                         +---------+
```

- **E. When to use which**
  - **for**: you know how many times in advance (print a table, walk an array).
  - **while**: repeat until something happens, count unknown (read digits of a number until it becomes 0).
  - **do-while**: the body must run at least once (show a menu, then ask "continue?").
- **F. Typical do-while program: menu that repeats**

```c
#include <stdio.h>
int main()
{
    int choice;
    do
    {
        printf("1. Say hello\n2. Say bye\n0. Exit\nChoice: ");
        scanf("%d", &choice);
        if (choice == 1) printf("Hello!\n");
        else if (choice == 2) printf("Bye!\n");
    } while (choice != 0);
    return 0;
}
```

- **G. Comparison (memorise)**

| Point | for | while | do-while |
| --- | --- | --- | --- |
| Type | Entry-controlled | Entry-controlled | Exit-controlled |
| Condition checked | Before each round | Before each round | After each round |
| Minimum runs | 0 | 0 | 1 |
| Syntax | for (init; cond; update) { } | while (cond) { } | do { } while (cond); |
| Semicolon after condition? | No | No | **Yes** |
| Where are init and update? | All in the heading | Init before, update inside body | Init before, update inside body |
| Best for | Known number of repetitions | Unknown count, check first | Menus, input validation |

- **H. Nested loops and infinite loops**
  - A loop inside a loop runs the inner loop completely for every round of the outer one (used in patterns, topic 5, and matrices, topic 22).
  - Deliberate infinite loops: `for (;;)` or `while (1)`, stopped with break (topic 18).

**Exam tip:** write the same small program in all three loops, then the comparison table. Underline the semicolon after do-while's condition; it is the most common syntax slip.

## 18. break vs continue (vs goto) (4/8) · Memorise

break leaves the loop (or switch) completely; continue skips the rest of the current round and jumps to the next round; goto jumps to any labelled line in the same function and is best avoided.

- **A. break**
  - Immediately **exits** the nearest loop or switch. The program continues after it.

```c
for (i = 1; i <= 10; i++)
{
    if (i == 5)
        break;           /* leave the loop when i reaches 5 */
    printf("%d ", i);
}
```

- **A (output).** `1 2 3 4`
  - Uses: stop searching once an item is found (topic 15); end each case of a switch (topic 6); escape an infinite loop.
- **B. continue**
  - **Skips** the remaining statements of the current round and goes to the next round. The loop does not end.

```c
for (i = 1; i <= 10; i++)
{
    if (i % 2 == 0)
        continue;        /* skip even numbers */
    printf("%d ", i);
}
```

- **B (output).** `1 3 5 7 9`
  - In a for loop, continue jumps to the update (i++). In while/do-while it jumps to the condition, so make sure the update happens before continue or you get an infinite loop.
  - continue cannot be used in a switch on its own (only inside a loop).
- **C. goto**
  - Jumps unconditionally to a **label** (a name followed by a colon) in the same function.

```c
#include <stdio.h>
int main()
{
    int n;
again:                               /* label */
    printf("Enter a positive number: ");
    scanf("%d", &n);
    if (n <= 0)
        goto again;                  /* jump back to the label */
    printf("You entered %d\n", n);
    return 0;
}
```

- **C (output).** Input `-3` then `8` → asks twice, then `You entered 8`.
  - Why avoid it: jumping around makes code hard to follow ("spaghetti code"). A loop does the same job more clearly.
  - Acceptable use: escaping from deeply nested loops in one step.
- **D. One program showing all three ideas side by side**

| Code inside `for (i = 1; i <= 5; i++) { ... printf("%d ", i); }` | Output |
| --- | --- |
| No jump statement | 1 2 3 4 5 |
| if (i == 3) break; | 1 2 |
| if (i == 3) continue; | 1 2 4 5 |

- **E. Comparison (memorise)**

| Point | break | continue | goto |
| --- | --- | --- | --- |
| Effect | Ends the loop/switch | Skips to the next round | Jumps to a label |
| Loop continues afterwards? | No | Yes | Depends on where it jumps |
| Works in | Loops and switch | Loops only | Anywhere in the same function |
| Needs a label? | No | No | Yes |
| Structured programming | Accepted | Accepted | Discouraged |
| Typical use | Stop when found; end a case | Skip unwanted values | Exit nested loops; rare |

- **F. Related: exit() and return**
  - `return` leaves the current function. `exit(0)` (stdlib.h) ends the whole program at once.

**Exam tip:** show the 1-to-5 loop with break and with continue and give both outputs. That pair answers the difference question in four lines.

## 19. Conditional (ternary) operator (4/8) · Memorise

The conditional operator `condition ? value1 : value2` is a one-line if-else that produces a value: if the condition is true the result is value1, otherwise value2. It is C's only ternary operator (it takes three operands).

- **A. Syntax and meaning**
  - `result = (condition) ? expression1 : expression2;`
  - Read it as: "Is the condition true? If yes, use expression1; if no, use expression2."
  - Same as:

```c
if (condition)
    result = expression1;
else
    result = expression2;
```

- **B. Examples (each one line)**

| Task | Using ?: | Result for the sample |
| --- | --- | --- |
| Larger of a, b | max = (a > b) ? a : b; | a = 4, b = 9 → 9 |
| Even or odd | printf("%s", (n % 2 == 0) ? "Even" : "Odd"); | n = 7 → Odd |
| Absolute value | abs = (x < 0) ? -x : x; | x = −5 → 5 |
| Pass or fail | (marks >= 40) ? printf("Pass") : printf("Fail"); | 55 → Pass |
| Leap year (simple) | leap = (y % 4 == 0) ? 1 : 0; | 2024 → 1 |

- **C. Nested ternary: largest of three numbers**

```c
#include <stdio.h>
int main()
{
    int a, b, c, max;
    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);
    max = (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);
    printf("Largest = %d\n", max);
    return 0;
}
```

- **C (output).** Input `12 45 30` → `Largest = 45`.
  - How to read it: if a > b, the answer is the larger of a and c; otherwise it is the larger of b and c.
- **D. Rules and facts**
  - Precedence is low (just above assignment) and it groups **right to left**: `a ? b : c ? d : e` means `a ? b : (c ? d : e)`.
  - Both result expressions should have compatible types.
  - It is an **expression** (gives a value), so it can sit inside printf or on the right of =. if-else is a **statement** and cannot.
- **E. Ternary vs if-else**

| Point | Conditional operator ?: | if-else |
| --- | --- | --- |
| Kind | Expression (returns a value) | Statement |
| Length | One line | Several lines |
| Can be used inside printf or an assignment | Yes | No |
| Readability | Good for simple choices; poor when nested deeply | Better for complex logic |
| Multiple statements per branch | No (one expression each) | Yes |

**Exam tip:** write the syntax line, one simple example (larger of two), and the nested largest-of-three program with its output.

## 20. Number programs: GCD, Armstrong, sum and reverse of digits, nCr (4/8) · Practise

Most number programs use one trick: n % 10 gives the last digit and n / 10 removes it, repeated in a while loop until n becomes 0. GCD uses Euclid's rule gcd(a, b) = gcd(b, a % b), and nCr uses three factorials.

- **A. The digit trick**
  - `n % 10` → last digit (1234 % 10 = 4).
  - `n / 10` → number without its last digit (1234 / 10 = 123, integer division).
  - Repeat `while (n != 0)` to visit every digit from right to left.
- **B. Program 1: sum of digits and reverse of a number (together)**

```c
#include <stdio.h>
int main()
{
    int n, original, rem, sum = 0, rev = 0;
    printf("Enter a number: ");
    scanf("%d", &n);
    original = n;
    while (n != 0)
    {
        rem = n % 10;            /* last digit */
        sum = sum + rem;         /* add it */
        rev = rev * 10 + rem;    /* append it to rev */
        n = n / 10;              /* drop it */
    }
    printf("Sum of digits = %d\n", sum);
    printf("Reverse = %d\n", rev);
    if (rev == original)
        printf("%d is a palindrome number\n", original);
    return 0;
}
```

- **B (trace for 1234).**

| Round | n | rem = n % 10 | sum | rev = rev × 10 + rem | n / 10 |
| --- | --- | --- | --- | --- | --- |
| 1 | 1234 | 4 | 4 | 4 | 123 |
| 2 | 123 | 3 | 7 | 43 | 12 |
| 3 | 12 | 2 | 9 | 432 | 1 |
| 4 | 1 | 1 | 10 | 4321 | 0 (stop) |

- **B (output).** `Sum of digits = 10`, `Reverse = 4321`. For 121 it also prints `121 is a palindrome number`.
- **C. Program 2: Armstrong number**
  - An Armstrong number equals the sum of its digits each raised to the power of the number of digits.
    - 153 (3 digits): 1³ + 5³ + 3³ = 1 + 125 + 27 = 153 ✔
    - 9474 (4 digits): 9⁴ + 4⁴ + 7⁴ + 4⁴ = 6561 + 256 + 2401 + 256 = 9474 ✔
    - 3-digit Armstrong numbers: 153, 370, 371, 407.

```c
#include <stdio.h>
int main()
{
    int n, temp, digits = 0, rem, sum = 0, p, i;
    printf("Enter a number: ");
    scanf("%d", &n);

    temp = n;
    while (temp != 0)            /* step 1: count digits */
    {
        digits++;
        temp /= 10;
    }

    temp = n;
    while (temp != 0)            /* step 2: add digit^digits */
    {
        rem = temp % 10;
        p = 1;
        for (i = 0; i < digits; i++)
            p = p * rem;
        sum += p;
        temp /= 10;
    }

    if (sum == n)
        printf("%d is an Armstrong number\n", n);
    else
        printf("%d is not an Armstrong number\n", n);
    return 0;
}
```

- **C (output).** `153` → `153 is an Armstrong number`; `123` → `123 is not an Armstrong number` (1 + 8 + 27 = 36).
  - For a 3-digit-only version, replace the inner for loop with `sum += rem * rem * rem;`.
  - Why not pow() from math.h? pow works with decimals and can give 124.9999 instead of 125, which breaks the comparison.
- **D. Program 3: GCD (HCF) and LCM**
  - Euclid's method: replace (a, b) by (b, a % b) until b becomes 0; then a is the GCD.
  - LCM = (a × b) / GCD.

```c
#include <stdio.h>
int main()
{
    int a, b, x, y, r;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    x = a;  y = b;
    while (y != 0)
    {
        r = x % y;
        x = y;
        y = r;
    }
    printf("GCD = %d\n", x);
    printf("LCM = %d\n", (a * b) / x);
    return 0;
}
```

- **D (trace for 48 and 18).** (48, 18) → 48 % 18 = 12 → (18, 12) → 18 % 12 = 6 → (12, 6) → 12 % 6 = 0 → (6, 0). Output `GCD = 6`, `LCM = 144`.
  - Recursive version: `int gcd(int a, int b) { return (b == 0) ? a : gcd(b, a % b); }`
- **E. Program 4: nCr**
  - nCr = n! / ( r! × (n − r)! ). Full program with a factorial function is in topic 10. Example: 6C2 = 720 / (2 × 24) = 15.
  - Related: nPr = n! / (n − r)!. Example: 5P2 = 120 / 6 = 20.
- **F. Other number programs using the same tricks**
  - Count digits: `while (n != 0) { count++; n /= 10; }`
  - Prime check: n is prime if no i from 2 to n/2 (or √n) divides it: `if (n % i == 0) { isPrime = 0; break; }`.
  - Perfect number: sum of its proper divisors equals the number (6 = 1 + 2 + 3).
  - Fibonacci series with a loop: `c = a + b; a = b; b = c;`

**Exam tip:** add a trace table like the one for 1234; it proves the logic even if a small syntax slip creeps in. Always keep a copy of the original number (original = n) before the loop destroys it.

## 21. Arrays: declaration and initialisation (3/8) · Memorise

An array is a fixed-size row of boxes of the same type sharing one name, numbered from 0; you declare it as `type name[size];` and may fill it at declaration with values in braces, where missing values become 0.

- **A. Why arrays?**
  - Storing 50 marks in 50 separate variables (m1, m2 … m50) is hopeless. `int marks[50];` gives 50 boxes under one name, reachable with a loop.
- **B. Declaring a one-dimensional array**
  - Syntax: `data_type array_name[size];`
    - `int marks[5];` → 5 ints: marks\[0\] to marks\[4\].
    - `float price[10];`, `char name[20];`
  - The size must be a positive constant (or a #define name) in classic C.
- **C. Initialisation: the five forms (memorise)**

| Form | Example | Result |
| --- | --- | --- |
| Full | int a\[5\] = {10, 20, 30, 40, 50}; | 10 20 30 40 50 |
| Partial | int a\[5\] = {10, 20}; | 10 20 0 0 0 (rest become 0) |
| All zero | int a\[5\] = {0}; | 0 0 0 0 0 |
| Size left out | int a\[\] = {4, 8, 15}; | Size becomes 3 automatically |
| Character array | char s\[\] = "BCA"; or {'B','C','A','\\0'} | 4 boxes including '\\0' |

- **C (warnings).**
  - More values than the size (`int a[2] = {1, 2, 3};`) is an error.
  - An array declared without initialisation inside a function holds **garbage**.
  - You cannot assign a whole array after declaration: `a = {1, 2};` is not allowed. Assign element by element or use a loop.
- **D. Accessing elements**
  - `a[0]` is the first element, `a[n-1]` the last. `a[2] = 99;` changes the third box.
  - C does **not** check bounds: `a[5]` in a 5-element array silently reads or damages other memory.
- **E. Memory layout**
  - Elements sit **side by side** (contiguously). For `int a[5]` with base address 1000 and 4-byte ints:

| Element | a\[0\] | a\[1\] | a\[2\] | a\[3\] | a\[4\] |
| --- | --- | --- | --- | --- | --- |
| Address | 1000 | 1004 | 1008 | 1012 | 1016 |

- **E (formula).** Address of a\[i\] = base address + i × (size of one element). Example: a\[3\] = 1000 + 3 × 4 = 1012.
  - Total size = number of elements × element size = 5 × 4 = 20 bytes.
- **F. Two-dimensional arrays (tables, matrices)**
  - `int m[2][3];` → 2 rows, 3 columns, 6 elements.
  - Initialisation:
    - `int m[2][3] = { {1, 2, 3}, {4, 5, 6} };` (row by row, clearest)
    - `int m[2][3] = {1, 2, 3, 4, 5, 6};` (same result)
    - `int m[][3] = { {1, 2, 3}, {4, 5, 6} };` (row count may be left out, column count may not)
  - Stored in **row-major order**: the whole of row 0, then row 1 (1 2 3 4 5 6 in memory).
  - Access: `m[1][2]` is row 1, column 2 → 6.
- **G. Program: initialise, read, and print an array**

```c
#include <stdio.h>
int main()
{
    int a[5] = {10, 20};          /* partial: a[2..4] become 0 */
    int i;
    for (i = 0; i < 5; i++)
        printf("a[%d] = %d\n", i, a[i]);
    return 0;
}
```

```
a[0] = 10
a[1] = 20
a[2] = 0
a[3] = 0
a[4] = 0
```

- **H. Passing an array to a function**
  - `int sum(int a[], int n)` — call as `sum(a, n)` (just the name). The function gets the address, so changes it makes affect the original array.
- **I. Characteristics, advantages and limitations**
  - All elements share one data type; indexes start at 0; memory is contiguous; the name is the base address.
  - Advantages: one name for many values; easy looping; fast access to any element by index.
  - Limitations: size fixed in advance (wasted or insufficient space; see malloc in topic 16); inserting or deleting in the middle means shifting elements; no bounds checking.

**Exam tip:** give the syntax, the five initialisation forms in a table, and the address diagram. For 2-D arrays, mention row-major order.

## 22. Matrix programs: addition, multiplication, diagonal (3/8) · Practise

A matrix is a 2-D array handled with two nested loops (i for rows, j for columns); addition adds matching cells, multiplication needs a third loop k and requires columns of A = rows of B, and diagonal programs use the cells where i == j (main diagonal) or i + j == n − 1 (other diagonal).

- **A. Reading and printing a matrix (used by every program)**

```c
for (i = 0; i < r; i++)          /* each row */
    for (j = 0; j < c; j++)      /* each column */
        scanf("%d", &a[i][j]);

for (i = 0; i < r; i++)
{
    for (j = 0; j < c; j++)
        printf("%4d", a[i][j]);
    printf("\n");                /* new line after each row */
}
```

- **B. Program 1: matrix addition**
  - Rule: both matrices must be the **same size**. C\[i\]\[j\] = A\[i\]\[j\] + B\[i\]\[j\].

```c
#include <stdio.h>
int main()
{
    int a[10][10], b[10][10], c[10][10], r, cl, i, j;
    printf("Enter rows and columns: ");
    scanf("%d %d", &r, &cl);
    printf("Enter matrix A:\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < cl; j++)
            scanf("%d", &a[i][j]);
    printf("Enter matrix B:\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < cl; j++)
            scanf("%d", &b[i][j]);

    for (i = 0; i < r; i++)
        for (j = 0; j < cl; j++)
            c[i][j] = a[i][j] + b[i][j];

    printf("Sum matrix:\n");
    for (i = 0; i < r; i++)
    {
        for (j = 0; j < cl; j++)
            printf("%4d", c[i][j]);
        printf("\n");
    }
    return 0;
}
```

- **B (example).** A = \[1 2 ; 3 4\], B = \[5 6 ; 7 8\] → Sum = \[6 8 ; 10 12\].
- **C. Program 2: matrix multiplication**
  - Rule: A is r1 × c1, B is r2 × c2. Multiplication is possible only if **c1 == r2**. The answer is r1 × c2.
  - Each cell: C\[i\]\[j\] = sum over k of A\[i\]\[k\] × B\[k\]\[j\] (row i of A times column j of B).

```c
#include <stdio.h>
int main()
{
    int a[10][10], b[10][10], c[10][10];
    int r1, c1, r2, c2, i, j, k;
    printf("Rows and columns of A: ");
    scanf("%d %d", &r1, &c1);
    printf("Rows and columns of B: ");
    scanf("%d %d", &r2, &c2);
    if (c1 != r2)
    {
        printf("Cannot multiply: columns of A must equal rows of B\n");
        return 1;
    }
    printf("Enter matrix A:\n");
    for (i = 0; i < r1; i++)
        for (j = 0; j < c1; j++)
            scanf("%d", &a[i][j]);
    printf("Enter matrix B:\n");
    for (i = 0; i < r2; i++)
        for (j = 0; j < c2; j++)
            scanf("%d", &b[i][j]);

    for (i = 0; i < r1; i++)
        for (j = 0; j < c2; j++)
        {
            c[i][j] = 0;
            for (k = 0; k < c1; k++)
                c[i][j] += a[i][k] * b[k][j];
        }

    printf("Product matrix:\n");
    for (i = 0; i < r1; i++)
    {
        for (j = 0; j < c2; j++)
            printf("%5d", c[i][j]);
        printf("\n");
    }
    return 0;
}
```

- **C (worked example).** A = \[1 2 ; 3 4\], B = \[5 6 ; 7 8\]

| Cell | Row of A · column of B | Value |
| --- | --- | --- |
| C\[0\]\[0\] | 1×5 + 2×7 | 19 |
| C\[0\]\[1\] | 1×6 + 2×8 | 22 |
| C\[1\]\[0\] | 3×5 + 4×7 | 43 |
| C\[1\]\[1\] | 3×6 + 4×8 | 50 |

- **C (output).** Product = \[19 22 ; 43 50\]. Note A × B is usually not equal to B × A.
- **D. Program 3: sum of diagonals (square matrix only)**
  - **Main (principal) diagonal**: cells where row = column (i == j): top-left to bottom-right.
  - **Secondary diagonal**: cells where i + j == n − 1: top-right to bottom-left.

```c
#include <stdio.h>
int main()
{
    int a[10][10], n, i, j, d1 = 0, d2 = 0;
    printf("Enter order of square matrix: ");
    scanf("%d", &n);
    printf("Enter elements:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &a[i][j]);

    for (i = 0; i < n; i++)
    {
        d1 += a[i][i];            /* main diagonal */
        d2 += a[i][n - 1 - i];    /* secondary diagonal */
    }
    printf("Main diagonal sum = %d\n", d1);
    printf("Secondary diagonal sum = %d\n", d2);
    return 0;
}
```

- **D (example).** For

```
1 2 3
4 5 6
7 8 9
```

- **D (result).** Main diagonal 1 + 5 + 9 = **15**; secondary 3 + 5 + 7 = **15**.
  - Print only diagonal elements: inside the double loop, `if (i == j) printf("%d ", a[i][j]);`
- **E. Bonus: transpose** (rows become columns)
  - `t[j][i] = a[i][j];` inside the double loop. \[1 2 3 ; 4 5 6\] becomes \[1 4 ; 2 5 ; 3 6\].

**Exam tip:** state the size rule first (same size for addition; c1 == r2 for multiplication; square for diagonals), check it in the program, and show one small worked example.

## 23. Pre and post increment/decrement: output tracing (3/8) · Practise

Pre-increment (++a) adds 1 first and then uses the new value; post-increment (a++) uses the old value first and adds 1 afterwards (−− works the same way, subtracting). Trace each line with a small table of variable values and the answer is mechanical.

- **A. The four forms**

| Form | Name | Rule | a = 5; b = (form); | a after | b after |
| --- | --- | --- | --- | --- | --- |
| ++a | Pre-increment | Change, then use | b = ++a; | 6 | 6 |
| a++ | Post-increment | Use, then change | b = a++; | 6 | 5 |
| −−a | Pre-decrement | Change, then use | b = −−a; | 4 | 4 |
| a−− | Post-decrement | Use, then change | b = a−−; | 4 | 5 |

- **A (memory hook).** Read left to right: in **++a** the ++ comes first, so the change comes first. In **a++** the a comes first, so the old value is used first.
  - On a line by itself, `a++;` and `++a;` do exactly the same thing (add 1). The difference only shows inside a bigger expression.
- **B. Tracing method**
  1. Write a table with one column per variable.
  2. For each line, first replace every pre-form with the new value (and update the table), use old values for post-forms.
  3. Compute the expression.
  4. Apply the pending post-form changes. Move to the next line.
- **C. Worked example 1**

```c
#include <stdio.h>
int main()
{
    int a = 5, b = 10, c;
    c = a++ + ++b;            /* line 1 */
    printf("%d %d %d\n", a, b, c);
    c = --a - b--;            /* line 2 */
    printf("%d %d %d\n", a, b, c);
    return 0;
}
```

| Line | Working | a | b | c |
| --- | --- | --- | --- | --- |
| Start | – | 5 | 10 | ? |
| 1 | ++b makes b = 11; a++ gives 5; c = 5 + 11 = 16; then a becomes 6 | 6 | 11 | 16 |
| 2 | −−a makes a = 5; b−− gives 11; c = 5 − 11 = −6; then b becomes 10 | 5 | 10 | −6 |

```
6 11 16
5 10 -6
```

- **D. Worked example 2: more single-line traces**

| Code (fresh values each row) | Result |
| --- | --- |
| int x = 10; int y = x−− + 5; | y = 15, x = 9 |
| int i = 3; int j = ++i \* 2; | i = 4, j = 8 |
| int p = 7; int q = p++ \* 2; | q = 14, p = 8 |
| int m = 4, n = 6; int k = ++m + n−−; | k = 5 + 6 = 11, m = 5, n = 5 |
| int a = 1, b; b = a++ + 10; b = b + a; | after line 1: b = 11, a = 2; after line 2: b = 13 |

- **E. Worked example 3: inside loops**
  - `int n = 3; while (n-- > 0) printf("%d ", n);`
    - Check 3 > 0 (true), n becomes 2, print 2. Check 2 > 0, n → 1, print 1. Check 1 > 0, n → 0, print 0. Check 0 > 0 false, n → −1, stop.
    - Output `2 1 0`; afterwards n = −1.
  - `int n = 3; while (--n > 0) printf("%d ", n);`
    - n → 2, 2 > 0, print 2. n → 1, print 1. n → 0, 0 > 0 false, stop. Output `2 1`.
  - `for (i = 0; i < 5; i++) printf("%d ", i++);`
    - Prints 0 (i → 1), loop update i → 2; prints 2 (i → 3), update i → 4; prints 4 (i → 5), update i → 6; stop. Output `0 2 4`.
- **F. Warning: undefined behaviour**
  - Changing the **same** variable twice in one expression, or changing it and also reading it elsewhere in that expression, has **no fixed answer in standard C**. Examples:
    - `x = i++ + ++i;`
    - `y = a++ * a++;`
    - `printf("%d %d", a, a++);`
  - Different compilers (Turbo C vs GCC) print different results. If such a question appears, write the output your course material expects, and add one line: "strictly, this is undefined behaviour in C, so the result is compiler-dependent."
- **G. Rules worth one mark**
  - ++ and −− work only on variables: `5++` and `(a + b)++` are errors.
  - They are unary operators with high precedence (topic 14).
  - They are faster to write than `a = a + 1`, and common in loops.

**Exam tip:** never guess; draw the variable table and update it step by step, writing "use old value" or "change first" beside each ++/−−.

## Last-minute cheat sheet

One page for the night before the exam: the syntax you must not get wrong, the comparison pairs examiners love, and a checklist for writing any program answer.

- **A. Format specifiers**

| Specifier | Type | Specifier | Type |
| --- | --- | --- | --- |
| %d | int | %c | char |
| %f | float | %s | string |
| %lf | double (in scanf) | %p | address |
| %ld | long | %u | unsigned int |

- **B. Syntax most often written wrongly**
  - `scanf("%d", &x);` → & for ordinary variables, none for string arrays.
  - `do { ... } while (cond);` → semicolon at the end.
  - `struct student { ... };` → semicolon after the brace.
  - `#define SQUARE(x) ((x) * (x))` → no semicolon, brackets everywhere.
  - `if (a == b)` → two equals signs to compare.
  - `fp = fopen("f.txt", "r"); if (fp == NULL) ...` → always check, then fclose(fp).
  - `p = (int *) malloc(n * sizeof(int)); ... free(p);`
  - Strings end with '\\0'; array indexes run 0 to n − 1.
- **C. The comparison pairs (one line each)**

| Pair | The one-line difference |
| --- | --- |
| Macro vs function | Macro is pasted text before compiling (fast, no type check); function is called at run time (type-checked, smaller code) |
| Structure vs union | Structure: separate memory per member, size = sum; union: shared memory, size = largest member |
| Call by value vs reference | Value: copy, original unchanged; reference: address, original can change |
| while vs do-while | while checks first (may run 0 times); do-while checks last (runs at least once) |
| break vs continue | break leaves the loop; continue skips to the next round |
| switch vs else-if | switch: exact int/char values; else-if: any condition or range |
| malloc vs calloc | malloc: 1 argument, garbage; calloc: 2 arguments, zero-filled |
| Sequential vs random file access | Sequential: read in order; random: jump with fseek |
| ++a vs a++ | ++a: change then use; a++: use then change |
| Static vs dynamic allocation | Static: fixed size at compile time; dynamic: chosen at run time, freed with free() |
| Recursion vs iteration | Recursion: function calls itself, uses stack; iteration: loop, faster |

- **D. Storage classes in one breath**: auto (stack, garbage, block, block) · register (CPU, garbage, block, block, no &) · static (memory, 0, block, whole program) · extern (memory, 0, global, whole program).
- **E. Number tricks**: last digit n % 10; drop digit n / 10; GCD loop r = a % b, a = b, b = r; LCM = a × b / GCD; nCr = n! / (r! (n − r)!).
- **F. Checklist for any program answer**
  1. \#include the right headers (stdio.h; string.h only if allowed; stdlib.h for malloc/exit).
  2. Declare variables with sensible names.
  3. Prompt with printf, read with scanf.
  4. The logic (loop/decision), with a short comment on the key line.
  5. Print the result with a label.
  6. Write one sample input and output under the program.
  7. For theory parts: definition → syntax → example → comparison table.

## Sources

- Your past-paper solution playlists, IGNOUverse on YouTube: [June 2024](https://www.youtube.com/playlist?list=PLKzz9hY3xDDWSEIwryaINfVNPPdaaGGz6), [Dec 2023](https://www.youtube.com/playlist?list=PLKzz9hY3xDDWigFm1iHQyYCMwyecj8DY9), [June 2023](https://www.youtube.com/playlist?list=PLKzz9hY3xDDX8w5Q1-EbRnQW3i5J8h1Cv), [Dec 2022](https://www.youtube.com/playlist?list=PLKzz9hY3xDDW5ZqP9Z0QBLBUn4-xmDo9z), [June 2022](https://www.youtube.com/playlist?list=PLKzz9hY3xDDVeMosAxuiP-llEVNYlb3pB).
- The C content follows standard C (as in the ANSI/ISO C standard and IGNOU's MCS-011 course). The programs were written for these notes; sample outputs assume a typical modern 64-bit compiler (int = 4 bytes).
