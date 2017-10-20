---
title: Penjelasan isu google.com.my DNS hijacking.
layout: content
date: '2013-10-11 00:00:00'
categories: blogs
---

Salam,

Baru saja habis mengajar "DNSSEC Training" yang dianjurkan oleh syarikat saya Localhost S/B. DNSSEC adalah teknologi untuk memastikan keselamatan DNS secara menyeluruh, ia mampu menahan serangan dari "Cache poisoning", "DNS MITM dan lain-lain. 

Pagi ini 11-10-2013 kita digemparkan dengan domain google.com.my telah di hijack dan ini menarik perhatian saya untuk membuat sedikit analysis. Jika anda membuka laman web google.com.my pada masa kejadian ia akan memberi content yang salah seperti contoh di bawah:

 <img src="" alt="image not found"/>


Di sini ada 2 kemungkinan:

1. Data DNS telah ditukar kepada rekod lain (A, NS atau CNAME)  atau
2. Server google.com.my telah diceroboh

Langkah seterusnya memeriksa data pada DNS dengan menggunakan tool DNS. Dalam langkah ini saya menggunakan dig command.

 <img src="" alt="image not found"/>
 
Daripada data di atas kita dapat melihat cache server 8.8.8.8 (google DNS) telah memberi jawapan yang mana google.com.my telah dipetakan kepada 142.4.211.228. 

Kemudian kita periksa data untuk NS rekod:

 <img src="" alt="image not found"/> 

Ini amat mengejutkan kerana jawapan dari 8.8.8.8 (google DNS) telah memberi maklumat nameserver google.com.my seperti berikut:

sdns1.ovh.ca
ks4003824.ip-142-4-211.net

Sepatutnya google.com.my menggunakan nameserver mereka sendiri. (nameserver adalah server yang digunakan untuk menghost data DNS). Pemeriksaan diteruskan dengan menggunakan cache server lain (cth: OpenDNS - 208.67.222.222 ) dan ia memberi jawapan yang sama. 

Saya beruntung kerana mempunyai akses kepada database DNS seluruh dunia. Untuk mengesahkan apa yang berlaku, saya telah menggunakan akses saya ini. Sistem ini menunjukkan perubahan setiap data pada DNS secara global (keseluruhan data DNS di dalam root(.) tree):

 

Daripada informasi di atas, kita dapati google.com.my telah dipetakan kepada IP penggodam pada 2013-10-10 13:44:57 (UTC) dan telah dibuang dari rekod DNS pada 2013-10-10 21:51:02 (UTC). Peringatan walaupun telah dibuang, data akan berada di dalam cache DNS mengikut TTL.

 
Seterusnya untuk data NS (name server). Data mula dilihat pada 2013-10-10 13:44:57 (UTC) dan telah dilihat kali terakhir pada 2013-10-10 21:49:37 (UTC). Data ini boleh di analysis secara detail lagi, tapi untuk penulisan ini ia sudah cukup untuk memberi hint kepada kita apakah yang telah berlaku. 

Di bawah adalah domain-domain yang telah dipetakan kepada IP penggodam 142.4.211.228. Di sini telah mengukuhkan lagi bahawa IP tersebut bukan kepunyaan GOOGLE.

 

Persoalan kenapa bukan google.com? tetapi google.com.my :) dan bukan .com.my, net.my, .my, org.my? Jadi entry point boleh berlaku pada:

1. Reseller domain yang menjaga google.com.my yang menghantar data kemaskini (unauthorize update dari attacker) atau
2. Registry (kebarangkalian adalah rendah)

Oleh demikian masih awal untuk membuat andaian. Jawapan punca bagaimana kejadian ini berlaku perlu dibincangkan secara berhemah, saya yakin tahap sistem keselamatan MYNIC (.my) adalah dalam keadaan baik.

Sebagai rumusan, pengodam telah menukar data DNS (mungkin melalui aplikasi reseller dan kemudian dikemaskini pada MYNIC melalui EPP) kepada data yang salah (tiada server Google yang terlibat). Setiap data DNS akan disimpan di dalam DNS cache server, ini akan memberi impact kepada pengguna internet lain, kerana data salah yang disimpan di dalam cache DNS akan berada disitu untuk seketika (bergantung kepada TTL). Oleh demikian pengguna akan dipetakan kepada server penggodam dengan menggunakan data yang salah ini. Dari pemerhatian di atas ini bukan DNS cache poisoning tapi data modification di bahagian atas dan menyebabkan data yang diterima oleh cache server adalah data yang salah. Lantaran itu DNS hijacking ini mungkin melibatkan DNS cache server utama dan impactnya adalah amat besar (kerana semua pengguna akan terkesan). DNSSEC adalah salah satu cara untuk menahan data dari dilencongkan ke server penyerang (dengan syarat).  

TTL - Time to live (masa yang digunakan oleh cache server untuk menyimpan data DNS. Jika TTL adalah 1 hari , maka data itu akan disimpan selama satu hari)
EPP - Extensible Provisioning Protocol (ialah protocol yang digunakan di antara registrar/reseller dengan registry (MYNIC) untuk berkomunikasi antara satu sama lain dalam urusan mentadbir pendaftaran/perubahan pada maklumat domain).

Kemaskini: Punca perkara ini berlaku adalah dari account reseller yang telah digodam. Dari akaun reseller data telah diubah dan kemudian dikemaskini ke dalam sistem registry. Kenyataan MYNIC telah diceroboh adalah TIDAK BENAR dan kenyataan DNS cache poisoning juga agak tidak tepat. Method serangan adalah NS delegation modification in reseller apps (unauthorize modification + social engineering). 

Sekian, Terima Kasih.

Disclaimer: This information is for educational purpose only.

Amir Haris Ahmad

Certified DNS/BIND Associates (DNS/CA), GSEC, GCIH.