display：flex是一種inner display type。
變動的子元素相較於設定的parent element來說算是inner。

任何定義display : flex的元素皆為：[[flex container]]
而此元素內部的HTML元素皆為：[[flex item]]。

1. flex item本身可再定義{display：flex}變成flex container(此時會有雙重身分，同時為flex container以及flex item)。對於HTML元素來說，outer display type是flex item，inner display type是flex
2. inline element放在flex container底下，會變成flex element！！