ㄨ2024/11/23


抽象資料類別：

1. queue: 
	- FIFO
2. stacks:
	- LIFO : 情境`gamil` 最新的放在最上方
		- push & pop
3. linked list:
	- 透過記憶體中**不連續的區塊**，利用指標（或引用）將這些區塊連結起來，形成一個有序的數據結構。

``` C
typedef struct node
{
	int number;
	struct node *next;
} node;

// node是一種資料型態，包含data和data pointer
// *則是指向下一個node的記憶體位址
```
   
dictionary  : store key & value

Hasing實質上是一個function
任意數的input得到固定長度的output

Hash table : Array of linked list
	**理想情況：** Hash Table 每個 key 都有獨立的 bucket，像 Dictionary 一樣高效運作。
	當多個 key 經過 Hash 函數後映射到同一個 bucket 時（collision 發生），需要方式來存放這些元素。
	Linked List 的特性非常適合解決這個問題

Tries : Tree of arrays

為何大多系統都使用hash table而非tries，因為tries會指數型花費空間，過多的閒置空間




