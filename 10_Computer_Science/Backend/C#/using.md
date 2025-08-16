using主要用於引入特定的名稱或整個命名空間，以方便在程式碼中使用。
``` C#
using testNameSpace;

class AnotherClass
{
    void SomeMethod()
    {
        // 在這裡可以直接使用 testNameSpace 命名空間中的 MyClass
        MyClass instance = new MyClass();
    }
}
	```
若是使用global using則不需重複在不同檔案使用using匯入 (C# 10.0新增功能)
``` C#
// 在專案的任何檔案中，只需使用一次 global using
global using testNameSpace;

class AnotherClass
{
    void SomeMethod()
    {
        // 在這裡可以直接使用 testNameSpace 命名空間中的 MyClass
        MyClass instance = new MyClass();
    }
}

```