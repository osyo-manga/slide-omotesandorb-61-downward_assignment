## Omotesando.rb #61

- - -

## Ruby に下代入が実装された

---

#### 自己紹介
- - -

* 名前：osyo
* Twitter : [@pink_bangbi](https://twitter.com/pink_bangbi)
* github  : [osyo-manga](https://github.com/osyo-manga)
* ブログ  : [Secret Garden(Instrumental)](http://secret-garden.hatenablog.com)
* [趣味で気になった bugs.ruby のチケットをブログにまとめてる](https://secret-garden.hatenablog.com/archive/category/bugs.ruby)               <!-- .element: class="fragment" -->
* 最近はるりまにめっちゃ PR 投げてる                   <!-- .element: class="fragment" -->
    * [ここ1ヶ月で 15個ぐらい PR 投げてる](https://github.com/rurema/doctree/pulls?q=is%3Apr+author%3Aosyo-manga)
* Kaigi on Rails                 <!-- .element: class="fragment" -->
    * [ActiveRecord の歩み方](https://speakerdeck.com/osyo/activerecord-falsebu-mifang)
* 銀座Rails                   <!-- .element: class="fragment" -->
    * [これからの Ruby と今の Ruby について](https://speakerdeck.com/osyo/korekarafalse-ruby-tojin-false-ruby-nituite)
    * [12月25日にリリースされる Ruby 3.0 に備えよう！](https://speakerdeck.com/osyo/12yue-25ri-niririsusareru-ruby-3-dot-0-nibei-eyou)
* BuriKaigi2021                 <!-- .element: class="fragment" -->
    * [Ruby 2.0 から Ruby 3.0 を駆け足で振り返る](https://speakerdeck.com/osyo/ruby-2-dot-0-kara-ruby-3-dot-0-woqu-kezu-dezhen-rifan-ru)

---

## Ruby に下代入が実装された

---

#### 下代入とは
- - -

* ^^ で選択した範囲を変数に定義する構文       <!-- .element: class="fragment" -->
    * [[Feature #17768] Proposal: Downward assignments](https://bugs.ruby-lang.org/issues/17768)
* 任意の式を選択して代入できる       <!-- .element: class="fragment" -->

```ruby
# var = 42 と同じ
42
^^var

# 中間の式も代入できる
p(2 * 3 * 7)  #=> 42
  ^^^^^var

p var         #=> 6
```
<!-- .element: class="fragment" -->

>>>

#### ユースケース
- - -

```ruby
while (line = gets) != nil
  p line
end
```

```ruby
while gets != nil
      ^^^^line
  p line
end
```
<!-- .element: class="fragment" -->

>>>

```ruby
ary = [1, 2, 3, 4, 5]

ary.each {|elem| found = elem if elem.even? }

p found  #=> 4
```

```ruby
ary = [1, 2, 3, 4, 5]

ary.each {|elem| elem if elem.even? }
                 ^^^^found

p found  #=> 4
```
<!-- .element: class="fragment" -->

>>>

```ruby
class C
  def initialize(foo, bar)
    @foo = foo
    @bar = bar
  end
end
```

```ruby
class C
  def initialize(foo,    bar)
                 ^^^@foo ^^^@bar
end
```
<!-- .element: class="fragment" -->

---

## ちょーべんり！！！

---

### デモ

---

#### おまけ
- - -

* 2 * x を 2x とかけるようになったぞい
    * 2(x + 1) ともかける

```ruby
irb(main):001:0> x = 3
 => 3
irb(main):002:0> 2x
 => 6
irb(main):003:0> def pi = Math::PI
 => :pi
irb(main):004:0> 2pi
 => 6.283185307179586
```

---


#### まとめ
- - -

* めちゃくちゃ便利なので早くほしい！！！！       <!-- .element: class="fragment" -->
* なお、これはエイプリルフールネタです       <!-- .element: class="fragment" -->

---

### ご清聴
### ありがとうございました

