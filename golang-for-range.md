---
title: golang for range 只有一个迭代变量?
date: 2020-06-05
---

题目, 下面的代码输出


```golang

package main

import (
	"fmt"
)

func rangeAppend() {
	v := []int{1, 2, 3}
	for i := range v {
		v = append(v, i)
	}
	fmt.Printf("%v", v)
}

func main() {
	rangeAppend()
}
```

golang playground https://play.golang.org/p/MxP3tpCGiSH

为什么上面的程序输出 
```
[1 2 3 0 1 2]
```

对于不同种类的range表达式结果值，for语句的迭代变量的数量可以有所不同, 代码中只有一个迭代变量的情况意味着什么呢？这意味着，该迭代变量只会代表当次迭代对应的元素值的索引值

下面代码中的i 是索引值,  0 1 2
```
	for i := range v {
		v = append(v, i)
	}
```

for语句的迭代变量是两个, 第一个是索引值, 第二个是迭代的值

```
package main

import (
	"fmt"
)

func rangeAppend() {
	v := []int{1, 2, 3}
	for _, i := range v {
		v = append(v, i)
	}
	fmt.Printf("%v", v)
}

func main() {
	rangeAppend()
}
```

上面输出

```
[1 2 3 1 2 3]
```
