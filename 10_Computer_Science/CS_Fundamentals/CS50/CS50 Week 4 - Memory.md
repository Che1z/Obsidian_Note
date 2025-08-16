為何要用16位數？
- 簡潔性：
    - 相比二進制，十六進制可以更簡潔地表示大數值。
    - 例如：二進制 1111 1111 1111 1111 在十六進制中只需要 FFFF。
- 可讀性：
    - 對於人類來說，閱讀和記憶十六進制數比長串的二進制數更容易。
- 轉換便利性：
    - 十六進制和二進制之間的轉換非常直觀和簡單。
    - 每個十六進制數字總是對應四個二進制位。
- 字節對齊：
    - 兩個十六進制數字正好表示一個byte，這在處理數據時非常有用。
- 常見用途：
    - 在計算機科學中廣泛使用，如：
        - 內存地址表示
        - 顏色代碼（如 Web 中的 #RRGGBB） 

C語法： 
	& (Address of operator, 值去找地址)
	*  (Deference operator, 地址去找值)
``` C
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	int number = get_int("What's the number?");
	// * 在聲明中，代表pointer
	// * 在表達式中，代表Deference operator的一個pointer
	int *p = &number;
	// 印出地址值
	printf("Address : %p \n", p); 
	// 藉由地址值印出數值
	printf("Number: %i \n", *p);
}
```

以前電腦記憶體只能支援到4GB，因為系統為32位元 （`2^32bits`)剛好是4GB

string其實就是 
```C
string s = "Hi";
char *s = "Hi";
```


