# Methods for competition programming used in Ruby
# 基本形

## 標準入力

~~~go
import "os"
import "bufio"

var sc = bufio.NewScanner(os.Stdin)
if sc.Scan(){
  sc.Text()
}
~~~

## 変数
var 変数名 型 = 値
~~~go
var value int = 16
//=>16
value := 16
//=>16
~~~

## 配列の作成

~~~go
ary := []int{1,2,3,4}
//[]には配列の要素数を入れる
//=> [1,2,3,4]

arr := make([]int, 5)
//=> [0,0,0,0,0]
~~~

## 配列への代入
数値と一緒に文字列も扱えます

~~~go
ary := []int{1, 2, 3, 4}
ary = append(ary, 99)
// => [1, 2, 3, 4, 99]
~~~

# よくつかうメソッド集

## 文字列の分割
~~~go
import "strings"

strings.Split("123", "")
//=>["1", "2", "3"]
strings.Split("1 2 3", " ")
//=>["1", "2", "3"]
strings.Split("1,2,3", " ")
//=>["1", "2", "3"]
~~~

## 配列の連結

~~~go
import "strings"
strings.Join([1, 2, 3], ",")
//=> 1,2,3
strings.Join([1, 2, 3], " ")
//=> 1 2 3
~~~

## 文字列の変換

~~~go
import "strconv"

strconv.Atoi("1234") //string -> int
//=>1234

//変数に入れる場合
value, _ = strconv.Atoi("123")
value //=> 123
~~~

# ループ処理

## for

~~~go
for (i := 1; i <= 10; i ++){
    fmt.Println(i)
}
//=>1
//=>2
//=>...
//=>9
//=>10
~~~

## each
配列の中身だけ取り出したい場合はeachメソッドを使います

~~~go
for _, v := range ["a", "b", "c"]{
    fmt.Println(v)
}
//=>a
//=>b
//=>c
~~~

# 分岐処理

## if
if 条件式 {
    値1
} else {
    値2
}

~~~go
if 10 > 1 {
    fmt.Println("10は1より大きい")
} else {
    fmt.Println("10は1より小さい")
}
//=> 10は1より大きい
~~~

## Case
3つ以上の複雑な条件分岐はif elsif
ではなくcase文を使いましょう

~~~go
i := 5
switch i {
    case 4: fmt.Println("number 4")
    case 5:fmt.Println("number 5")
    case 6: fmt.Println("number 6")
    default: fmt.Println("default")
}
//=> number 5
~~~
