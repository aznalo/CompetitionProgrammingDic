#Methods for competition programming used in Scala

#基本形

## 標準入力

~~~ruby
gets
~~~

## 変数
Rubyは動的型付けなので数値を入れた変数にそのまま文字列を
入れて上書きすることも可能です

~~~ruby
hoge = 0 
#=> 0
hoge = "fuga"
#=> fuga
~~~

## 配列の作成

~~~ruby
ary = Array.new(10)
#=> [nil, nil, nil, nil, nil, nil, nil, nil, nil, nil]
ary = []
#=> []
ary = [1, 2, 3]
#=> [1, 2, 3]
~~~

## 配列への代入
数値と一緒に文字列も扱えます

~~~ruby
ary = Array.new(10)
ary[0] = 1
#=> [1, nil, nil, nil, nil, nil, nil, nil, nil, nil]
ary[1] = "Int"
#=> [1, "Int", nil, nil, nil, nil, nil, nil, nil, nil]
~~~

#よくつかうメソッド集

##文字列の分割
~~~ruby
"123".split("")
#=>["1", "2", "3"]
"1,2,3".split(",")
#=>["1", "2", "3"]
"1 2 3".split(" ")
#=>["1", "2", "3"]
~~~

##配列の中身をすべてInt型に

~~~ruby
["1", "2", "3].map(&:to_i)
#=>[1, 2, 3]
~~~

## 配列の連結

~~~ruby
[1, 2, 3].join(",")
#=> 1,2,3
[1, 2, 3].join(" ")
#=> 1 2 3
~~~

##文字列の変換

~~~ruby
"1234".to_i
#=>1234
~~~

##数値配列の最大値or最小値を持ってくる

~~~ruby
[10, 1, 50, 30, 2, 66].min #=> 1
[10, 1, 50, 30, 2, 66].max #=> 66
~~~

##配列を逆向きに

~~~ruby
[1, 2, 3].reverse
#=>[3, 2, 1]
~~~

# ループ処理

## times
他の言語なら指定した回数文ループさせるなら
for文を使いますがRubyならtimesメソッドで充分です

~~~ruby
10.times{ |i| puts i }
#=>1
#=>2
#=>...
#=>9
#=>10
~~~

## each
配列の中身だけ取り出したい場合はeachメソッドを使います

~~~ruby
["a", "b", "c"].each { |v| puts v }
#=>a
#=>b
#=>c
~~~

#分岐処理

##  if

~~~ruby
if 条件式
  値1
else
  値2
end
~~~

#elseとかいらない場合

~~~ruby
puts "Yafo" if 条件式
#条件が満たされれば左側が実行される
~~~

##三項演算子

~~~ruby
v = 条件式 ? 値1 : 値2
v #=> 値1
~~~

## Case
3つ以上の複雑な条件分岐はif elsif
ではなくcase文を使いましょう

~~~ruby
case 値
when 条件1
  値
when 条件2
  値
when 条件3
  値
when 条件4
  値
end
~~~

#応用
可読性を失う代わりに短くなるコード

###カンマで変数を区切ると各変数に値が入る
~~~ruby
x = (a, b, c = 1, 2, 3)

a #=>1
b #=>2
c #=>3
x => [1, 2, 3]
~~~

###上記の応用でわざわざ変数にいちいち入れなくてもそのまま配列を扱える例

~~~ruby
(a, b = 10, 20)[0] #=> 10
a #=> 10
b #=> 20
####
(a, b = 10, 20)[0] + b #=> 30
~~~

### splitで分けた値を各変数に与える
~~~ruby
a, b = "10 20".split(" ").map(&:to_i)
a #=> 10
b #=> 20
~~~


###文字列に数値をかけると文字列が増える
~~~ruby
"#" * 3
#=> ###
~~~