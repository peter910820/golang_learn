# map

類似於其他語言的字典，是一種映射(鍵對鍵值)的資料結構:

## create map

```golang
func main() {
	var foobar = map[int]string{
		1: "一",
		2: "二",
		3: "三",
	}
}

```

## 更改, 新增

```golang
foobar[1] = "壹"
foobar[4] = "四"
fmt.Println(foobar[1], foobar[4]) //壹 四

```

## for range迭代

```golang
package main

import "fmt"

func main() {
	var foobar = map[int]string{
		1: "一",
		2: "二",
		3: "三",
	}
	for keys, values := range foobar {
		fmt.Println(keys, values)
		//1 一
		//2 二
		//3 三
	}

}

```