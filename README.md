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

## fmt套件

幫助顯示輸出的內建套件

### fmt.Printf

格式化(format)，常用format如下:

```golang
package main

import "fmt"

var a int = 10
var b string = "Hello"

func main() {

	fmt.Printf("a = %d\n", a)    // a = 10
	fmt.Printf("b = %s\n", b)    // b = Hello
	fmt.Printf("c = %c\n", b[0]) // c = H
}
```

```golang
package main

import "fmt"

type foo struct {
	A string
	B bool
	C int
}

func main() {

	fmt.Printf("foo = %v\n", foo{})  // foo = { false 0}
	fmt.Printf("foo = %+v\n", foo{}) // foo = {A: B:false C:0}
	fmt.Printf("foo = %#v\n", foo{}) // foo = main.foo{A:"", B:false, C:0}
}
```

```v```專門用來查看物件結構

### fmt.Print, fmt.Println

有無換行的差別:

```golang
package main

import "fmt"

var foo string = "Hi"

func main() {

	fmt.Print(foo)
	fmt.Println(foo)
	fmt.Print(foo)

	// HiHi
	// Hi
}

```

### `` vs ""

```golang
package main

import "fmt"

func main() {

	fmt.Print("\n")
	fmt.Print(`\n`)

	//
	// \n
}
```

``` `` ```內會保留原始字串

## fmt.Scanf, fmt.Scan, fmt.Scanln

讀取使用者輸入:

```golang
package main

import "fmt"

func main() {
	var foo int
	fmt.Print("Input a number: ")
	fmt.Scanf("%d", &foo)

	fmt.Printf("Your number is %d", foo)
}
```

## fmt.Sprint, fmt.Sprintln, fmt.Sprintf

```golang
package main

import "fmt"

func main() {
	foo := "Hello,"
	bar := "World!"
	a := fmt.Sprint(foo, bar)
	b := fmt.Sprintln(foo, bar)
	c := fmt.Sprintf("%s/%s", foo, bar)

	fmt.Println(a) // Hello,World!
	fmt.Println(b) // Hello, World!
	               //
	fmt.Println(c) // Hello,/World!
}
```

## if statement

```golang
package main

import "fmt"

func main() {
	foo := 10
	if foo < 10 {
		fmt.Println("To small")
	} else if foo == 10 {
		fmt.Println("Perfect!")
	} else {
		fmt.Println("To big")
	}
	// Perfect!
}

```

## switch statement

```golang
package main

import "fmt"

func main() {
	foo := 1
	switch {
	case foo == 1:
		fmt.Println("Perfect!")
	case foo == 2:
		fmt.Println("Too big")
	case foo == 0:
		fmt.Println("To small")
	}
	// Perfect!
	foo = 0
	switch foo {
	case 1:
		fmt.Println("Perfect!")
	case 2:
		fmt.Println("Too big")
	case 0:
		fmt.Println("To small")
	}
	// To small
}

```