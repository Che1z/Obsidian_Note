型別：可分為實質型別和參考型別
- 實質型別（Value types）：記憶體空間存放實際的值
	整數數值類型：
		sbyte, byte, short, ushort, int, uint, long, ulong, nint, nuint
	浮點數值類型：
		float, double, decimal
	bool
	char
	enum（列舉）
	struct（結構）
	ref（結構類別，引數傳遞的一個修飾符）
	Tuple型別
- 參考型別（Reference types）：記憶體空間存放的是值的記憶體位置
	class
	object
	array
	string (string interning)

Numbers： 可再區分成兩種類型
1. Integer types：整數，儲存非小數點數值 （主要使用型別有:int、long，兩者差在數值範圍）
		int( -2,147,483,648 to 2,147,483,647)
		long(-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807，為了確保程式碼的清晰性，可在末端加上 Ｌ)
	 其他型別：sbyte、byte、short、ushort、uint、ulong、nint、nuint

2. Floating point types：包含小數點數值（主要使用型別：float、double）
		float和double比較：兩者差在精度、範圍、記憶體佔用
		
		精度：double較準
		- float：佔32位，提供7位有效數字
		- double：佔64位，提供15位有效數字（精度較高）
		範圍：double較廣
		- float範圍 ±1.5 x 10^(-45) 到 ±3.4 x 10^(38)
		- double範圍±5.0 x 10^(-324) 到 ±1.7 x 10^(308)
		記憶體佔用：double佔用較多
		其他型別：decimal，精度達小數點後第28位，建議用於財務金融上計算

Booleans：代表true或false（預設為false）

文字：可區分成char和string
1. Char（Value type）：用來儲存單一字元資料，資料必須使用''包住(像是：'A')，預設值為( `\0`)，
	Note：由於Char屬於特殊字符，因此都需要用`\`轉義

2. Strings（Reference type）：用來儲存一系列的字元，使用""包住資料("Hello world")
Note：為何string會是Reference type？
由於String的資料可能很大（一段字元），因此設計為Reference type，並且藉由String interning機制達到優化記憶體空間的需求

日期(DateTime)：
物件(Object)：