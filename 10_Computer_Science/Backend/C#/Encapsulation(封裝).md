將`Data`和操作`Data的Method`綁定在同一個`Class`中。
為了保護`Class`內的`field`安全，不讓外部能直接存取`field`，需要將類別`field`保護起來。
``` C#
public class UserData 
{ // 資料成員 
	private string username; private string email; 
	// 屬性 (Properties) 用來訪問資料成員 
	public string Username { 
		get { return username; } 
		set { username = value; } 
	} 
	public string Email { 
		get { return email; } 
		set { email = value; } 
	} // 方法 (Methods) 用來操作資料 
	public void DisplayUserData() { 
		Console.WriteLine("Username: " + username);
		Console.WriteLine("Email: " + email); } 
}
```
為何要有封裝性？
Ans: 
1. `Class`本身應該就要包含方法
2. 一些基本方法（如`Rectangle class`要有計算面積方法），若沒有會導致有許多種寫法，最終造成閱讀混亂
3. 若將方法寫在其他`Class`，意味著`Field`要設為`Public`