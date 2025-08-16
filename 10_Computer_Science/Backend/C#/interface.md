Interface可視為『合約』，作為base class，derived class需遵守合約的規範(return type、parameter數量等)去定義method

命名以大寫『Ｉ』為開頭
``` C#
interface IFlyable{ //預設是public，因此可以不另外撰寫
	void Fly();
	string FlyDistance { get; set; }
}
```

Interface本身有幾點和abstract相同：
	不可實例化、implicit virtual

和[[Abstract keyword]]不同的點：
1. 內容預設都是`public`,不能有`access modifier`
2. `Interface`只可以繼承`Interface`，而`Abstract`則可繼承`Abstract或Interface`
3. `Class`不能繼承多個`Class`，但可繼承多個`Interface`
4. `Interface`裡頭只有`declaration`沒有`implemantation
5. `Interface`不能含有`field` (過於<mark style="background: #FFF3A3A6;">具體</mark>)

建議interface只包含：property以及method declaration

| 特性    | Abstract class                          | Interface                |
| ----- | --------------------------------------- | ------------------------ |
| 存取修飾詞 | 使用不同的存取修飾詞，如 public、protected、private 等 | 所有成員預設為 public，不可添加存取修飾詞 |
| 多重繼承  | 不支援多重繼承                                 | 允許多重繼承                   |
| 靜態成員  | 可以有靜態成員                                 | 不能有靜態成員                  |

[[IEnumerable]]