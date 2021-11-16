#define _CRT_SECURE_NO_WARNINGS

#include<stdio.h>

int main()

{

	//左移操作符:左边丢弃，右边补0；
	//右移操作符:1.算术右移:右边丢弃，左边补原符号位 2.逻辑右移:右边丢弃，左边补0；
             //针对负数，正整数原码反码补码相同
	int a = -1;//原码:10000000000000000000000000000001  
	           //反码:11111111111111111111111111111110
	           //补码:11111111111111111111111111111111
	int b = a >> 1;//不改变a的值
	printf("%d\n", b);//-1,当前平台采用算术右移
  
	return 0;
  
}

 //^ 按（2进制）位异或，相同为0，相异为1

int main()

{

	int a = 3;//011
	int b = 5;//101
	printf("a=%d b=%d\n", a, b);
	a = a ^ b;//110 1.
	b = a ^ b;//011 b和新的a异或，得出原来的a
	a = a ^ b;//101 新的a再和b(a)异或，得出原来的b
	//1.相当于产生了一个新的临时变量
	printf("a=%d b=%d\n", a, b);
  
	return 0;
  
}


int main()

{

	int a = 13;
	//把a的二进制中的第5位置成1
	a = a | (1 << 4);
	printf("a=%d\n", a);
	//把a的二进制中的第5位置成0
	a = a & ~(1 << 4);
	printf("a=%d\n", a);
	//00000000000000000000000000001101
	//00000000000000000000000000000001
	//& >>
  
	return 0;
  
}


struct Book

{

	char name[20];
	char id[20];
	int price;

};
int main()
{

	int num = 0;
	struct Book b = { "C语言","C20210509",55 };
	struct Book * pb = &b;

	//1.
	//结构体指针->成员名
	//printf("书名：%s\n", pb->name);
    //printf("书号：%s\n", pb->id);
    //printf("定价：%d\n", pb->price);
	//2.
	//printf("书名：%s\n", (*pb).name);
    //printf("书号：%s\n", (*pb).id);
    //printf("定价：%d\n", (*pb).price);
	//3.
	//printf("书名：%s\n", b.name);
	//printf("书号：%s\n", b.id);
	//printf("定价：%d\n", b.price);
  
	return 0;
  
}

int main()

{

	char a = 3;
	//00000000000000000000000000000011
	//00000011 - a

	char b = 127;
	//00000000000000000000000001111111
	//01111111 - b

	char c = a + b;
	//00000000000000000000000010000010
	//100000010 - c

	//发现a和b都是char类型的，都没有达到一个int的大小
	//这里就会发生整型提升
	//整型提升是按照变量的数据类型的符号位来提升的
	//无符号补0


	//11111111111111111111111110000010-补码
	//11111111111111111111111110000001-反码
	//10000000000000000000000001111110-原码
	printf("%d\n", c);//126

	return 0;
  
}

int main()

{

	char c = 1;
	printf("%u\n", sizeof(c));
	printf("%u\n", sizeof(+c));
	printf("%u\n", sizeof(!c));//应该为4
  
	return 0;
  
}



//实现init() 初始化数组为全0
//实现print() 打印数组的每个元素
//实现reverse() 函数完成数组元素的逆置
void init(int *arr, int sz)

{
	int i = 0;
	for (i = 0; i < sz; i++)
	{
		arr[i] = 0;
	}
}
void print(int *arr, int sz)

{

	int i = 0;
	for (i = 0; i < sz; i++)
	{
		printf("%d ", arr[i]);
	}
	printf("\n");
}
void reverse(int* arr, int sz)

{

	int tmp = 0;
	int left = 0;
	int right = sz - 1;
	while (left<right)
	{
		tmp = arr[left];
		arr[left] = arr[right];
		arr[right] = tmp;
		left++;
		right--;
    
	}
	
}

int main()

{

	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	int sz = sizeof(arr) / sizeof(arr[0]);
	print(arr, sz);
	reverse(arr, sz);
	print(arr, sz);
	init(arr, sz);
	print(arr, sz);

	return 0;
  
}


int main()

{

	int arr1[] = { 1,3,5,7,9 };
	int arr2[] = { 2,4,6,8,10 };
	int sz = sizeof(arr1) / sizeof(arr1[0]);
	int i = 0;
	for (i = 0; i < sz; i++)
	{
		int tmp = arr1[i];
		arr1[i] = arr2[i];
		arr2[i] = tmp;
	}
	for (int a = 0; a < sz; a++)
	{
		printf("%d ", arr1[a]);
	}
	printf("\n");
	for (int a = 0; a < sz; a++)
	{
		printf("%d ", arr2[a]);
	}

	return 0;
  
}
