# Rails

## Apa itu Ruby on Rails ?

- Rangka Kerja Web ( Framework )
- Ditulis dalam bahasa pengaturcaraan Ruby
- Dicipta oleh David Heinemeier Hansson pada tahun 2003
- Berada di bawah Sumber Terbuka pada Julai 2004
- Berkonsepkan kepada MVC ( Model, View, Controller )
  Ruby on Rails is a full stack web framework optimized for programmer
  happiness and sustainable productivity. It encourages beautiful code by
  favoring convention over configuration http://www.rubyonrails.org

## Sistem Operasi

- Microsoft Windows Linux
- Mac Os X BSD most flavors of Unix

## Database

- MySQL SQL Server
- PostgreSQL
- Oracle
- SQLite
- DB2
- Informix
- Firebird
- SybaseASA
- MongoDB Cassandra
- dan lain-lain

## Pemasangan Ruby On Rails di Windows

Kaedah yang paling mudah untuk anda memasang applikasi Ruby on Rails adalah dengan menggunakan package railsinstaller. Package railsinstaller ini boleh dimuat turun di alamat berikut :

http://railsinstaller.org/

Selesai muat turun sila pasangkan package railsintaller di komputer anda. Railsinstaller akan memasang applikasi seperti berikut : 

Ruby 2.2.6
Rails 5.0
Bundler
Git
Sqlite
TinyTDS
SQL Server Support
DevKit

## Bagaimana memastikan Rails telah sedia dipasang

Untuk memastikan package ruby on rails telah benar benar dipasang, sila buka terminal / command prompt dan jalankan arahan berikut :- 

rails -v  

Sekiranya version rails terpapar contoh seperti di atas Rails 5.0.1 maka komputer anda telahpun tersedia dipasang dengan applikasi Ruby On Rails.


## Mari Membuat Applikasi PermohonanKursus

### Langkah 1

Buka satu ‘Windows Terminal’ / Command Prompt dan jalankan arahan seperti di bawah :

```
C: presentation>rails new mylatihan skip bundle
```

### Langkah 2

Masuk ke dalam folder mylatihan yang dicipta oleh rails dan jalankan arahan berikut untuk mencipta pengkalan data mylatihan_development yang menggunakan sqlite 

```
C: presentation >cd mylatihan/

C: presentation mylatihan>bundle exec rake db:create
```

### Langkah 3

Jalankan arahan di bawah untuk memulakan ‘Web Server’ 

```
C: presentation mylatihan>rails server
```

### Langkah 4

Buka satu lagi ‘Windows Terminal’ / Command Prompt dan jalankan arahan seperti di bawah :-

```
C: presentation mylatihan>rails generate scaffold Permohonan nama:string kad_pengenalan:string no_pekerja:string email:string telefon:string jabatan:string latihan_id:integer

C: presentation mylatihan>bundle exec rake db:migrate

```

### Langkah 5

Buka ‘Web Browser’ kesukaan anda dan pergi ke alamat http://localhost:3000/permohonans.

Apabila anda klik pada link ‘New Permohonan’, paparan ‘form’ seperti di bawah

### Langkah 6

C: presentation mylatihan>rails generate scaffold Latihan tajuk:string maklumat:text kod:string tempat:string tarikh_mula:date tarikh_tamat:date tarikh_tutup:date

C: presentation mylatihan>bundle exec rake db:migrate

### Langkah 7

Buka ‘Web Browser’ kesukaan anda dan pergi ke alamat http://localhost:3000/latihans

Apabila anda klik pada link ‘New Latihan’, paparan ‘form’ seperti di bawah kelihatan dan anda boleh terus mengisi maklumat

### Langkah 8

Di dalam form permohonan latihan , untuk membolehkan pemohon memilih senarai latihan menggunakan ‘drop down menu’, sila ubah code seperti berikut 

Sunting file C: presentation mylatihan app controllers permohonans_controller.rb menggunakan editor kesukaan anda. Tambahkan kod yang dihitamkan ke dalam kod asal seperti di bawah dan simpan file tersebut :

``` ruby
# GET /permohonans/new
# GET /permohonans/new.json

def new
    @permohonan = Permohonan.new
    @latihans = Latihan.all
    respond_to do |format|
        format.html # new.html.erb
        format.json { render json: @permohonan }
    end
end
```

file : presentation mylatihan app controllers permohonans_controller.rb

### Langkah 9

Sunting file C: presentation mylatihan app views _form.html.erb menggunakan editor kesukaan anda. Tukarkan kod yang dihitamkan seperti di bawah 

```
tukar

<div class="field">
    <%= f.label :latihan_id %>
    <%= f.number_field :latihan_id %>
</div>

kepada :-

<div class="field">
    <%= f.label :latihan_id %>
    <%= collection_select :permohonan,:latihan_id, @latihans, :id, :tajuk %>
</div>
```

### Langkah 10

Buka ‘Web Browser’ kesukaan anda dan pergi ke alamat http://localhost:3000/permohonans/new dan anda akan melihat ‘drop down menu’ untuk pilihan latihan telah terpapar.








