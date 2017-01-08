#Ruby Basics
##Home
##Overview

* Bahasa pengaturcaraan Berorientasikan Objek ‘Object Oriented’ di bawah Sumber Terbuka ( Open Source )
* Bahasa Pengaturcaraan berasaskan skrip ( scripting language )
* Dicipta oleh Yukihiro Matsumoto pada tahun 1995 !
* Digunakan bukan sahaja untuk Applikasi Web. Cth : 
  Google Sketchup macro scripting API, dll.
  Dynamic, open source programming language with a focus on simplicity
  and productivity. It has an elegant syntax that is natural to read and easy to write. from http:// www.ruby lang.com

##Environment

Sila layari laman web http://tryruby.org untuk mencuba ruby secara ‘online’.

##Syntax

Marilah kita menulis program yang mudah dalam ruby. Semua fail ruby ​​akan mempunyai sambungan .rb. Jadi, letakkan kod sumber berikut dalam fail test.rb.
``` ruby
#!/usr/bin/ruby -w

puts "Hello, Ruby!";
```
Sekarang, cuba untuk menjalankan program ini seperti berikut:
```
$ ruby test.rb
```
Ini akan menghasilkan keputusan seperti berikut:
```
Hello, Ruby!
```

### Whitespace
Aksara ruang kosong seperti ruang dan tab biasanya diabaikan kod Ruby, kecuali apabila mereka muncul dalam string. Tafsiran seperti ini menghasilkan amaran apabila pilihan w dinyatakan.

```
a + b is interpreted as a+b ( Here a is a local variable)
a  +b is interpreted as a(+b) ( Here a is a method call)

```

###Line Endings dalam Program Ruby:

Ruby menafsirkan koma bertitik (;) dan newline character sebagai pengakhiran satu kenyataan. Walau bagaimanapun, jika Ruby menghadapi operator, seperti +, -, atau 'backslash'(\) di akhir garisan, mereka menunjukkan penerusan satu kenyataan.

###Ruby Identifier

Pengenal pasti adalah nama-nama pembolehubah, pemalar, dan kaedah. Ruby pengenalan adalah sensitif huruf. Ia bermakna Ram dan RAM dua idendifiers berbeza dalam Ruby.

Ruby nama pengecam boleh terdiri daripada huruf dan aksara garis bawah (_).

Perkataan Cipta Terpelihara:
Senarai berikut menunjukkan perkataan reserved dalam Ruby. Ini terpelihara kata-kata tidak boleh digunakan sebagai nama malar atau berubah-ubah. Mereka boleh, bagaimanapun, digunakan sebagai nama kaedah.

<table class="table table-bordered">
<tbody><tr><td>BEGIN</td><td>do</td><td>next</td><td>then</td></tr>
<tr><td>END</td><td>else</td><td>nil</td><td>true</td></tr>
<tr><td>alias</td><td>elsif</td><td>not</td><td>undef</td></tr>
<tr><td>and</td><td>end</td><td>or</td><td>unless</td></tr>
<tr><td>begin</td><td>ensure</td><td>redo</td><td>until</td></tr>
<tr><td>break</td><td>false</td><td>rescue</td><td>when</td></tr>
<tr><td>case</td><td>for</td><td>retry</td><td>while</td></tr>
<tr><td>class</td><td>if</td><td>return</td><td>yield</td></tr>
<tr><td>def</td><td>in</td><td>self</td><td>__FILE__</td></tr>
<tr><td>defined?</td><td>module</td><td>super</td><td>__LINE__</td></tr>
</tbody></table>

##Classes
##Variables
##Operators
##Comments
##IF...ELSE
##Loops
##Methods
##Blocks
##Modules
##Strings
##Arrays
##Hashes
##Date & Time
##Ranges
##Iterators
##File I/O
##Exceptions
