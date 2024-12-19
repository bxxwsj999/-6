# 实验6 函数
##一、实验目的
1、掌握定义函数的方法。
2、掌握函数实参与形参的对应关系，以及“值传递”的方式。3、掌握函数的嵌套调用和递归调用的方法。
##二、实验准备
1、复习函数调用的基本理论知识。 
2、复习函数的嵌套调用和递归调用的方法。
3、复习全局变量、局部变量:静态变量、动态变量:外部变量等概念和具体实用方法。
##三、实验内容
#include <stdio.h>

// 1. 自定义函数求字符串长度
int myStrlen(char *str) {
    int len = 0;
    while (*str!= '\0') {
        len++;
        str++;
    }
    return len;
}

// 2. 函数将数组元素按反序存放
void invert(int arr[], int n) {
    int i, temp;
    for (i = 0; i < n / 2; i++) {
        temp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = temp;
    }
}

// 3. 函数实现求两数之和
int add(int a, int b) {
    return a + b;
}

// 3. 函数实现求两数之差
int sub(int a, int b) {
    return a - b;
}

// 3. 函数实现求两数之积
int mul(int a, int b) {
    return a * b;
}

// 3. 函数调用其他函数实现不同功能
void process(int a, int b) {
    printf("两数之和为：%d\n", add(a, b));
    printf("两数之差为：%d\n", sub(a, b));
    printf("两数之积为：%d\n", mul(a, b));
}

int main() {
    // 1. 求字符串长度测试
    char str[100];
    printf("请输入一个字符串：\n");
    scanf("%s", str);
    int length = myStrlen(str);
    printf("该字符串的长度为：%d\n", length);

    // 2. 数组元素反序存放测试
    int arr[10];
    printf("请输入10个数：\n");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }
    invert(arr, 10);
    printf("反序后的数组为：\n");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // 3. 实现不同功能测试
    int a, b;
    printf("请输入两个数：\n");
    scanf("%d %d", &a, &b);
    process(a, b);

    return 0;
}
代码分析:
1. 求字符串长度部分
myStrlen 函数通过一个指针遍历输入的字符串，只要指针所指向的字符不是字符串结束标志 '\0'，就将长度计数器 len 加 1，并将指针向后移动一位，直到遇到 '\0'，最后返回字符串的长度值。
2. 数组元素反序存放部分
invert 函数使用循环来交换数组元素，循环次数为数组长度的一半（因为每次交换涉及两个元素）。通过一个临时变量 temp，将数组中对称位置的元素进行交换，从而实现数组元素的反序存放。
3. 实现不同功能部分
add、sub、mul 这三个函数分别实现了求两数之和、差、积的简单功能，直接返回对应运算的结果。
process 函数则在内部调用了 add、sub、mul 这三个函数，在 main 函数中输入两个数后，调用 process 函数就能依次输出这两个数的和、差、积。
在 main 函数中，分别按照题目要求进行了相应功能的测试，提示用户输入必要的数据，并调用对应的函数完成操作，最后输出相应的结果。
