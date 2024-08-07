# golang_learn

## 執行go程式碼:

```bash
$ go run {code.go}
```

也可以使用build:

```bash
$ go build {code.go}
```

使用build會產生一個執行檔，與run差別在使用run執行檔會存在電腦的暫存區下

## 變數宣告

* 全域變數用```var```，區域變數用```:=```短變數宣告(Short variable declarations):

```golang
package main

import "fmt"

var a int = 10

func main() {

	b, c := 11, 12
	fmt.Println(a, b, c) // 10 11 12

}
```

## 常數宣告

* 使用```const```，全大寫

```golang
package main

import "fmt"

const PI float64 = 3.14159

func main() {

	fmt.Println(PI) // 3.14159

}
```

## iota

數字遞增的方便功能，從0開始:

```golang
package main

import "fmt"

const (
	A = iota + 10 //iota為0
	B             //iota為1
	C             //iota為2
	D             //iota為3
	E = iota * 10 //會接續前面的數字, iota為4
	F             //iota為5
	G             //iota為6
)

func main() {

	fmt.Println(A, B, C, D, E, F, G) // 10 11 12 13 40 50 60

}
```

## 用iota做左移右移(Shift Bit)運算

### 左移

```golang
package main

import "fmt"

const (
	A = 1 << iota //向1右邊塞入0(iota為0)個bit(左移)
	B
	C
	D
	E
	F
	G
)

func main() {

	fmt.Println(A, B, C, D, E, F, G) // 1 2 4 8 16 32 64

}
```
### 右移

```golang
package main

import "fmt"

const (
	A = 10 >> iota //向1左邊塞入0(iota為0)個bit(右移)
	B
	C
	D
	E
	F
)

func main() {

	fmt.Println(A, B, C, D, E, F) // 10 5 2 1 0 0
}
```