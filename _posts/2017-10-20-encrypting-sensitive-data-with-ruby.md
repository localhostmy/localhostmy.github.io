---
title: Encrypting Sensitive Data With Ruby
layout: content
date: '2011-02-26 00:00:00'
categories: BLOG
---

In Encrypting Sensitive Data with Perl I wrote about how to use public key encryption to automatically and securely encrypt information with Perl. This allows you encryption things like credit card numbers, bank routing information, or that winning PowerBall number in a unattended fashion. Typically, you would use this in a situation where a user needs to enter sensitive information into a form which need to be stored in a secure manner. We can do this with Ruby (on Rails) as well, and it’s even easier.

First we need to generate a key pair. This creates two keys, a public key which will only be used to encrypt data, and a private key, which will only be used to decrypt data. The private key is protected by a password know only to us. When it comes to choosing strong passwords, I suggest using Diceware. 2048 is the key size in bits. Bigger is better, but also slower; 2048 is considered a good trade off between speed and encryption strength. We are also limited by this to encrypting as most 2048 bits, more on this below.

<i style="color: orange;">% openssl genrsa -des3 -out private.pem 2048
Generating RSA private key, 2048 bit long modulus
......+++
.+++
e is 65537 (0x10001)
Enter pass phrase for private.pem:
Verifying - Enter pass phrase for private.pem:</i>

Then we extract the public key:


<i style="color: orange;">openssl rsa -in private.pem -out public.pem -outform PEM -pubout
Enter pass phrase for private.pem:
writing RSA key</i>

Once we have the keys, we can encrypt data using the following:

<i style="color: orange;">#!/usr/bin/env ruby</i>

require 'openssl'
require 'base64'

publickeyfile = 'public.pem';
string = 'Hello World!';

publickey =
   OpenSSL::PKey::RSA.new(File.read(publickeyfile))
encryptedstring =
   Base64.encode64(publickey.publicencrypt(string))

print encryptedstring, "\n"

Simply, public_key_file is path to the file containing the public key, and string is the string to encrypt. We open the public key and then use public_encrypt to encrypt it. Because the encrypted string is binary I have converted to text using <a href ="https://en.wikipedia.org/wiki/Base64">Base64</a>. If your are storing the encrypted string in a database that can hold binary data, you could change:

<i style="color: orange;">encryptedstring = Base64.encode64(publickey.publicencrypt(string))*</i>

to:

<i style="color: orange;">encryptedstring = publickey.publicencrypt(string)</i>

Now that we have encrypted data, we’ll want to be able to get it back.

<i style="color: orange;">
#!/usr/bin/env ruby</i>

require 'openssl'
require 'base64'

privatekeyfile = 'private.pem';
password = 'boost facile'

encryptedstring = %Q{
qBF3gjF8iKhDh+g+TOvAzBkJA/1d2lD8RUyz2Ol+s1OpLB5aA3RA7EHm0KGL
XaP3upvJ7I5rN1yO9Qat9kyRQu9OMqAUmFvwUaiW/1NPjxnpmcFn9mhkttP9
qfO6iIfyxErUqKIxHYqavyPmivre9eEcXiBdtIK6NJJKG3WmSfIFgpZ6eBWI
wxlZg+x0fI4L2JsODMGx5Khn7CUt0bTkH6HMHwxEG24NbsmrqtC2zn8Hm/87
UyN5ZCDyJ/mtIHAjzPry6vbVPTF0QCR4lZ7uSt/W7JZ0tNgX7eQQwoPCgbqU
/uwRCwww/c407jw7YEE5Lgpx20/jyLXJwvZHxNEcxA==
}

privatekey =
  OpenSSL::PKey::RSA.new(File.read(privatekeyfile),password)

string =
  privatekey.privatedecrypt(Base64.decode64(encryptedstring))

print string, "\n"

Here private_key_file is path to the file containing the private key, password andencrypted_string is the string to decrypt. In a real application you would not want to hard-code the password, rather you should prompt for it in some way.

Again we are using Base64 to make the encrypted string human readable. If this is not necessary, change:

<i style="color: orange;">string = privatekey.privatedecrypt(Base64.decode64(encryptedstring))</i>

to:

<i style="color: orange;">string = privatekey.privatedecrypt(encryptedstring)</i>

As noted above, you can not use this method to encrypt anything larger than the key size minus 11 bytes of overhead <a href="https://en.wikipedia.org/wiki/Padding_%28cryptography%29"> (padding)</a>. In this case we have a 2048 bit key which gives 256 – 11 = 245 bytes. The temptation is to increase the key size to accommodate more data, but this quickly become to slow to be useful. The correct way to accomplish this is to use public key encryption to encrypt random password, which, in turn is used to encrypt the data using <a href="https://en.wikipedia.org/wiki/Symmetric-key_algorithm">symmetric-key encryption</a>. I’ll cover this next time.