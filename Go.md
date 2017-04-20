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

## 配列同士の比較

~~~go
import "reflect"
a := []byte{1, 2, 3}
b := []byte{1, 2, 3, 4}

fmt.Println(reflect.DeepEqual(a, b))             //=> false
fmt.Println(reflect.DeepEqual(a, b[0:3]))        //=> true
fmt.Println(reflect.DeepEqual(a, []byte{1,2,3})) //=> true
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

## 切り上げ・切り捨て

~~~go
import "math"

13/2 //=> 6

//切り上げ
math.Ceil(floot(float64(13)/2)) //=> 7.000000

//切り捨て
math.Floor(floot(float64(13)/2)) //=> 6.000000

//float -> Int型に
int(6.000000) //=> 6
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

# アルゴリズムテンプレート

## 二分検索

~~~go
func binarySearch(list []int, num int) int {
    var index = -1
        var head = 0
        var tail = len(list)

        for head <= tail {
            var center = int(math.Floor(float64((head + tail) / 2)))
                var centerVal = list[center]

                if centerVal == num {
                    index = center
                        break
                }
            if centerVal < num {
                head = center + 1
            } else {
                tail = center - 1
            }
        }
    return index
}
~~~

## バブルソート

~~~go
func bubbleSort(a []int) []int {
    for i := 0; i < len(a)-1; i++ {
            for j := 0; j < len(a)-i-1; j++ {
                        if a[j] > a[j+1] {
                                        a[j], a[j+1] = a[j+1], a[j]
                                    }
                    }
        }
    return a
}
~~~

## マージソート

~~~go
func main() {
    values := []int{3, 6, 1, 4, 5, 2, 9, 8, 7, 10}
    sortedValues := Sort(values)
    fmt.Println(sortedValues)
}

func merge(left, right []int) (ret []int) {
    ret = []int{}
    for len(left) > 0 && len(right) > 0 {
            var x int
            if right[0] > left[0] {
                        x, left = left[0], left[1:]
                    } else {
                                x, right = right[0], right[1:]
                            }
            ret = append(ret, x)
        }
    ret = append(ret, left...)
    ret = append(ret, right...)
    return
}

func sort(left, right []int) (ret []int) {
    if len(left) > 1 {
            l, r := split(left)
            left = sort(l, r)
        }
    if len(right) > 1 {
            l, r := split(right)
            right = sort(l, r)
        }

    ret = merge(left, right)
    return
}

func split(values []int) (left, right []int) {
    left = values[:len(values)/2]
    right = values[len(values)/2:]
    return
}

func Sort(values []int) (ret []int) { //マージソートのメイン関数
    left, right := split(values)
    ret = sort(left, right)
    return
}
~~~
