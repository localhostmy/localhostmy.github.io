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

Penentuan Kelas di Ruby:
Melaksanakan pengaturcaraan berorientasikan objek dengan menggunakan Ruby, anda perlu terlebih dahulu belajar bagaimana untuk mencipta objek dan kelas di Ruby.

Satu kelas di Ruby selalu bermula dengan 'class' kata kunci yang sejajar dengan nama kelas. Nama ini perlu sentiasa dalam huruf awal. Kelas Pelanggan boleh dipaparkan sebagai

```
class Customer
end
```
Anda menamatkan kelas dengan menggunakan 'end' kata kunci. Semua ahli data dalam kelas adalah di antara definisi kelas dan kata kunci akhir.


##Variables

Pembolehubah dalam Kelas Ruby:
Ruby menyediakan empat jenis pembolehubah:

Pembolehubah tempatan: pembolehubah tempatan pembolehubah yang ditakrifkan dalam kaedah. pembolehubah tempatan tidak boleh didapati di luar kaedah. Anda akan melihat lebih banyak butiran mengenai kaedah dalam bab berikutnya. pembolehubah tempatan bermula dengan huruf kecil atau _.


Pembolehubah instance: Pembolehubah instance kaedah seluruh tersedia untuk apa-apa keadaan atau objek tertentu. Ini bermakna bahawa pembolehubah contoh perubahan dari objek untuk membantah. pembolehubah contoh didahului oleh pada tanda (@) diikuti dengan nama yang berubah-ubah.

```
#!/usr/bin/ruby

class Customer
   def initialize(id, name, addr)
      @cust_id=id
      @cust_name=name
      @cust_addr=addr
   end
   def display_details()
      puts "Customer id #@cust_id"
      puts "Customer name #@cust_name"
      puts "Customer address #@cust_addr"
    end
end

# Create Objects
cust1=Customer.new("1", "John", "Wisdom Apartments, Ludhiya")
cust2=Customer.new("2", "Poul", "New Empire road, Khandala")

# Call Methods
cust1.display_details()
cust2.display_details()
```
Pembolehubah Kelas: pembolehubah kelas boleh didapati di seluruh objek yang berbeza. Pemboleh ubah kelas tergolong dalam kelas dan merupakan ciri-ciri kelas. Mereka didahului oleh tanda @@ dan diikuti oleh nama yang berubah-ubah.

```

#!/usr/bin/ruby

class Customer
   @@no_of_customers=0
   def initialize(id, name, addr)
      @cust_id=id
      @cust_name=name
      @cust_addr=addr
      @@no_of_customers += 1
   end
   def display_details()
      puts "Customer id #@cust_id"
      puts "Customer name #@cust_name"
      puts "Customer address #@cust_addr"
    end
    def total_no_of_customers()
       puts "Total number of customers: #@@no_of_customers"
    end
end
```

# Create Objects
cust1=Customer.new("1", "John", "Wisdom Apartments, Ludhiya")
cust2=Customer.new("2", "Poul", "New Empire road, Khandala")

# Call Methods
cust1.total_no_of_customers()
cust2.total_no_of_customers()

Pembolehubah Global: pembolehubah Kelas tidak tersedia di seluruh kelas. Jika anda ingin mempunyai pembolehubah tunggal, yang boleh didapati di seluruh kelas, anda perlu menentukan pembolehubah global. Pembolehubah global sentiasa didahului dengan tanda dolar ($).

```
#!/usr/bin/ruby

$global_variable = 10
class Class1
  def print_global
     puts "Global variable in Class1 is #$global_variable"
  end
end
class Class2
  def print_global
     puts "Global variable in Class2 is #$global_variable"
  end
end

class1obj = Class1.new
class1obj.print_global
class2obj = Class2.new
class2obj.print_global
```


##Operators

###Operator aritmetik Ruby:

<table class="table table-bordered">
<tbody>
<tr>
<th style="width:10%">Operator</th><th style="width:45%">Description</th><th>Example</th>
</tr>
<tr>
<td>+</td><td>Addition - Adds values on either side of the operator</td><td> a + b will give 30</td>
</tr>
<tr>
<td>-</td><td>Subtraction - Subtracts right hand operand from left hand operand</td><td> a - b will give -10</td>
</tr>
<tr>
<td>*</td><td>Multiplication - Multiplies values on either side of the operator</td><td> a * b will give 200</td>
</tr>
<tr>
<td>/</td><td>Division - Divides left hand operand by right hand operand</td><td> b / a will give 2</td>
</tr>
<tr>
<td>%</td><td>Modulus - Divides left hand operand by right hand operand and returns remainder</td><td> b % a will give 0</td>
</tr>
<tr>
<td>**</td><td>Exponent - Performs exponential (power) calculation on operators</td><td> a**b will give 10 to the power 20</td>
</tr>
</tbody>
</table>

###Operators Perbandingan Ruby:

Andaikan pembolehubah memegang 10 dan b berubah memegang 20, maka:

<table class="table table-bordered">
<tbody>
<tr>
<th style="width:10%">Operator</th><th style="width:45%">Description</th><th>Example</th>
</tr>
<tr>
<td>==</td><td> Checks if the value of two operands are equal or not, if yes then condition becomes true.</td><td> (a == b) is not true. </td>
</tr>
<tr>
<td>!=</td><td> Checks if the value of two operands are equal or not, if values are not equal then condition becomes true.</td><td> (a != b) is true. </td>
</tr>
<tr>
<td>&gt;</td><td> Checks if the value of left  operand is greater than the value of right operand, if yes then condition becomes true.</td><td> (a &gt; b) is not true. </td>
</tr>
<tr>
<td>&lt;</td><td> Checks if the value of left  operand is less than the value of right operand, if yes then condition becomes true.</td><td> (a &lt; b) is true. </td>
</tr>
<tr>
<td>&gt;=</td><td> Checks if the value of left  operand is greater than or equal to the value of right operand, if yes then condition becomes true.</td><td> (a &gt;= b) is not true. </td>
</tr>
<tr>
<td>&lt;=</td><td> Checks if the value of left  operand is less than or equal to the value of right operand, if yes then condition becomes true.</td><td> (a &lt;= b) is true. </td>
</tr>
<tr>
<td>&lt;=&gt;</td><td> Combined comparison operator. Returns 0 if first operand equals second, 1 if first operand is greater than the second and -1 if first operand is less than the second.</td><td> (a &lt;=&gt; b)  returns -1. </td>
</tr>
<tr>
<td>===</td><td> Used to test equality within a when clause of a <i>case</i> statement.</td><td> (1...10) === 5 returns true. </td>
</tr>
<tr>
<td><b>.eql?</b></td><td>True if the receiver and argument have both the same type and equal values.</td><td> 1
== 1.0 returns true, but 1<b>.eql?</b>(1.0) is false.</td>
</tr>
<tr>
<td><b>equal?</b></td><td>True if the receiver and argument have the same object id.</td><td>if aObj is duplicate of  bObj then aObj == bObj is true, a<b>.equal?</b>bObj is false but a<b>.equal?</b>aObj is true.</td>
</tr>
</tbody>
</table>

###Operators Tugasan Ruby:

Andaikan pembolehubah memegang 10 dan b berubah memegang 20, maka:

<table class="table table-bordered">
<tbody>
<tr>
<th style="width:10%">Operator</th><th style="width:40%">Description</th><th>Example</th>
</tr>
<tr>
<td>=</td><td>Simple assignment operator, Assigns values from right side operands to left side operand</td><td> c = a + b will assigne value of a + b into c</td>
</tr>
<tr>
<td>+=</td><td>Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand</td><td> c += a is equivalent to c = c + a</td>
</tr>
<tr>
<td>-=</td><td>Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand</td><td> c -= a is equivalent to c = c - a</td>
</tr>
<tr>
<td>*=</td><td>Multiply AND assignment operator, It multiplies right operand with the left operand and assign the result to left operand</td><td> c *= a is equivalent to c = c * a</td>
</tr>
<tr>
<td>/=</td><td>Divide AND assignment operator, It divides left operand with the right operand and assign the result to left operand</td><td> c /= a is equivalent to c = c / a</td>
</tr>
<tr>
<td>%=</td><td>Modulus AND assignment operator, It takes modulus using two operands and assign the result to  left operand</td><td> c %= a is equivalent to c = c % a</td>
</tr>
<tr>
<td>**=</td><td>Exponent AND assignment operator, Performs exponential (power) calculation on operators and assign value to the left operand</td><td> c **= a is equivalent to c = c ** a</td>
</tr>
</tbody>
</table>


##Comments

Anda boleh memberi komen banyak baris menggunakan = bermula dan sintaks = akhir seperti berikut:

``` ruby
#!/usr/bin/ruby -w

puts "Hello, Ruby!"

=begin
This is a multiline comment and con spwan as many lines as you
like. But =begin and =end should come in the first line only. 
=end

```

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
