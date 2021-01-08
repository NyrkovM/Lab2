#include "stdio.h";
#include "stdlib.h";
#include "time.h";

unsigned short int a[1000][1000], b[1000][1000], c[10000][10000];
int main(void)
{
	setvbuf(stdin, NULL, _IONBF, 0);
	setvbuf(stdout, NULL, _IONBF, 0); 
	int i = 0, j = 0, r;

	srand(time(NULL)); // инициализируем параметры генератора случайных чисел
	short int start_time = clock();

	int elem_c;
	while (i < 1000)
	{
		while (j < 1000)
		{
			a[i][j] = rand() % 100 + 1; // заполняем массив случайными числами
			j++;
		}
		i++;
	}
	srand(time(NULL)); // инициализируем параметры генератора случайных чисел
	i = 0; j = 0;
	while (i < 1000)
	{
		while (j < 1000)
		{
			b[i][j] = rand() % 100 + 1; // заполняем массив случайными числами
			j++;
		}
		i++;
	}
	for (i = 0;i < 1000;i++)
	{
		for (j = 0;j < 1000;j++)
		{
			elem_c = 0;
			for (r = 0;r < 1000;r++)
			{
				elem_c = elem_c + a[i][r] * b[r][j];
				c[i][j] = elem_c;
			}
		}
	}
	short int end_time = clock(); // конечное время

	short int search_time = end_time - start_time;
	
//	printf("Затраченное время:");
	printf("%f\n", search_time / 1000.0);
	return(search_time);
}
