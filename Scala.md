# Methods for competition programming used in Scala

# 基本構文

~~~scala
object Main extends App{ }
~~~

## 標準入力

~~~scala
readLine()
~~~

## 変数

~~~scala
var hgoe = 0
//Int = 0
val hoge = 0
//定数を作ることができる
~~~~~

## 配列

~~~scala
var ary = new Array[Int](10) //空のInt配列を作る(String配列も作れる)
// Array[Int] = Array(0, 0, 0, 0, 0, 0, 0, 0, 0, 0)
var ary = Array(1, 2, 3) //値をあらかじめ入れて配列を作る
// Array[Int] = Array(1, 2, 3)
~~~

## 関数

~~~scala
def methodName(引数:型):返り値の型={
return(返り値)
}
~~~

# よくつかうメソッド集

## 文字列の分割

~~~scala
"a b c".split(" ")
//Array[String] = Array(a, b, c)
~~~

## 配列の中身をすべてInt型に

~~~scala
Array("1", "2", "3").map(_.toInt)
//Array[Int] = Array(1, 2, 3)
~~~

## 配列を連結する+a

~~~scala
val ary = Array(1, 2, 3)
ary.mkString(",")
//1,2,3

"asdfg".mkString(",")
//a,s,d,f,g
~~~

## 文字列の変換

~~~scala
"1234".toInt
//Int = 1234
~~~

## 切り上げ/切り捨て/四捨五入

~~~scala
import scala.math.ceil //切り上げ
ceil(4.3) //5.0
ceil(5.1) //6.0

import scala.math.floor //切り捨て
floor(4.3) //4.0
floor(5.9) //5.0

import scala.math.round //四捨五入
round(5.4) //5
round(4.5) //5
~~~

# ループ処理

## for文

~~~scala
for( i <- 1 to 10 ){
    println(i)
} //10回ループする
//1
//2
//...
//9
//10
~~~

## for逆順
~~~scala
for( i <- 10 to 1 by -1 ){
    println(i)
} //10回ループする
//10
//9
//...
//2
//1
~~~

## each的なの

~~~scala
val list = List("a", "b", "c")
for(i <- list){
    println(i)
}
//a
//b
//c
~~~

## while
条件式にはBoolean型しかつかえない

~~~scala
while(条件式){}
~~~


# 分岐処理

## if

~~~scala
if (条件式) {
    値1 
} else {
    値2
}
//or 
if (条件式) 値1 else  値2
~~~

## Case

~~~scala
値 match{
    case 条件1 => 値 
    case 条件2 => 値 
    case 条件3 => 値 
    case 条件4 => 値 
}
~~~

# 応用

## 変数をすべて初期化する

~~~scala
val a, b, c = 1
//a => 1
//b => 1
//c => 1
~~~

## パターンマッチ

~~~scala
val (x,y) = (123,456)
//x => 123
//y => 456
~~~
