# Webhook Autoreply

Template autoreply dapat menggunakan shortcode. Yang akan diubah menjadi texts tertentu.
Contohnya `name` dan `phone`, yang akan diubah menjadi nama dan nomor telepon.

```
Hai {name}, Nomor anda {phone}
```
Isi pesan yang diterima tujuan
```
Hai John Snow, Nomor anda 628120000001
```

Shortcode yang tersedia ada 4:

Shortcode | nilai
---|---
{jid}| 628120000001@s.whatsapp.net
{user_id}| 628120000001@s.whatsapp.net
{phone}| 628120000001
{name}| John Snow


## Fungsi webhook

Webhook berfungsi untuk preprocessing pesan dan menambahkan shortcode dari data yang tersedia di website.
Sebagai contoh, ingin menambahkan data transaksi yang tersedia di website.

Maka endpoint webhook harus menghasilkan response data sebagagai berikut.
```
{
	"success": true,
	"data": {
		"shortcodes": {
			"nama": "John",
			"age": "25",
		},
		"no_reply": true
	}
}
````

Field | Tipe data | Keterangan
---|---
success| boolean | nilai `true` atau `false`. Jika false, tidak diproses.
data| object | data payload response


Field `data` memiliki dua buah field: `shortcodes` dan `no_reply`

Field | Tipe data | Keterangan
---|---
shortcodes| object | kombinasi key dan value. Tipe data value berupa string.
no_reply| boolean | true: memerintahkan autoreply untuk abort pengiriman pesan ke tujuan. Default value: false

