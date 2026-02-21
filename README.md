# README

James Booth\
2/20/2026

## Lab 02

### Description

For this lab, we simply got use to the Linux environment, using commands
like cd to move through directories, mv to move documents, and cat in
order to have a document print its contents for us. We also went through
several different challenges that required us to make new directories,
Home variables, etc.

### Usage Instructions

There really is not much to say here in terms of usage since it's just
Linux, but here are some helpful commands to know:

-   `cd 'filename'` -- Move to a different directory\
-   `ls` -- List all files in the current directory\
-   `cd ..` -- Move back out of a directory\
-   `sudo` -- Execute commands requiring admin permission\
-   `tree` -- View the file hierarchy\
-   `nano` -- Edit the contents of a file\
-   `mkdir` -- Create a new directory

------------------------------------------------------------------------

## Lab 03

### Description

For this lab, we learned how to compile a C program using the `gcc`
command in Linux. We also learned basic C syntax and how to format our
programs so they run smoothly and without error. Additionally, we
learned about the many different data types C has and created a simple
program that allows us to experiment with several of them.

### Usage Instructions

There are not many usage instructions beyond compiling and running the
program:

Compile using:

``` bash
gcc -Werror program.c -o program
```

Then run with:

``` bash
./program
```

------------------------------------------------------------------------

## Lab 04

### Description

We continued working with C programming, becoming familiar with the data
types included in `stdint.h`. We used strings in various ways and
performed mathematical operations without using loops or the math
library. We also learned how to use `printf` statements to debug our
programs.

### Usage Instructions

Example of multiplying by base 2 using bit shifting:

``` c
uint32_t multiplyByBase2(uint32_t num, uint32_t power)
{
    return num << power;
}
```

We use the left shift operator to multiply by powers of 2 without using
the math library or loops.

Example from `custom_strings.c` using a `toUpper` function:

``` c
void toUpper(char output[], char input[])
{
    int i = 0;

    while (input[i] != '\0') {
        if (input[i] >= 97 && input[i] <= 122) {
            output[i] = input[i] - 32;
        } else {
            output[i] = input[i];
        }
        i++;
    }

    output[i] = '\0';
}
```

Compile with:

``` bash
gcc -Werror file.c -o file
```

------------------------------------------------------------------------

## Lab 05

### Description

For this lab, we used an image library in C to manipulate the RGB pixels
of a `.bmp` file. We removed individual color channels, converted the
image to grayscale, and applied a deep-fry style OR filter.

### Usage Instructions

To use the program:

1.  Place your image in the project folder.
2.  Update the `Bitmap original_image;` reference to match your image
    filename.
3.  Compile and run.

Removing a color channel:

``` c
void remove_color_channel(Color color, Bitmap *bmp) {
    switch (color) {
    case BLUE_CHANNEL:
        for (int i = 0; i < bmp->pxl_data_size; i += 3) {
            bmp->pxl_data[i] = 0;
        }
        break;
    }
}
```

Grayscale conversion:

``` c
void grayscale(Bitmap *bmp) {
    for (uint32_t i = 0; i < bmp->pxl_data_size; i += 3) {
        uint8_t gray = (bmp->pxl_data[i] + bmp->pxl_data[i + 1] + bmp->pxl_data[i + 2]) / 3;

        bmp->pxl_data[i] = gray;
        bmp->pxl_data[i + 1] = gray;
        bmp->pxl_data[i + 2] = gray;
    }
}
```

OR filter example:

``` c
if (row > 0) {
    uint32_t above = (row - 1) * row_bytes + col * 3;

    bmp->pxl_data[i] |= bmp->pxl_data_cpy[above];
    bmp->pxl_data[i + 1] |= bmp->pxl_data_cpy[above + 1];
    bmp->pxl_data[i + 2] |= bmp->pxl_data_cpy[above + 2];
}
```
