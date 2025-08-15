Q：查詢每個部門的平均工資

```SQL
SELECT j.job_desc, AVG(j.max_lvl) AS avg_max_salary
FROM jobs j
GROUP BY j.job_desc
```

Ｑ：查詢在 1991 年出版的所有書名、作者和出版日期。
``` SQL
Select t.title,a.au_lname, a.au_fname, t.pubdate
From titles t 
Inner Join titleauthor ta on ta.title_id = t.title_id
Inner join authors a on a.au_id = ta.au_id
Where Year(t.pubdate) = 1991
```

Ｑ：查詢每本書收取的最高版稅。
```SQL
Select t.title_id, Max(r.royalty) As 最高版稅
From titles t 
Inner Join roysched r on r.title_id = t.title_id
Group By t.title_id
```

Q : 查詢著有多本書的作者姓名 (Group By後再篩選)

``` SQL
Select a.au_lname, a.au_fname, Count(ta.title_id)
From authors a
Inner Join titleauthor ta on ta.au_id = a.au_id
Inner Join titles t on t.title_id = ta.title_id
Group by a.au_lname, a.au_fname
Having Count(ta.title_id) > 1
```

Q : 查詢每本書的全部版稅信息。
``` SQL
Select t.title, r.*
From titles t 
Inner Join roysched r on r.title_id =t.title_id
```

Q :  查詢各個城市的書店名稱。
``` SQL
Select  s.city, s.stor_name
From stores s
Group by s.stor_name, s.city
```

Q : 查詢各部門的員工人數。
``` SQL
SELECT p.pub_name, COUNT(e.emp_id) AS emp_count
FROM employee e
INNER JOIN publishers p ON e.pub_id = p.pub_id
GROUP BY p.pub_name
```


