# BCA (Bank Central Asia)

Native PHP library untuk keperluan BCA REST API

# EXAMPLES

### SETTING DAN CONSTRUCTOR

```php
    $options = array(
        'scheme'        => 'https',
        'port'          => 443,
        'host'          => 'sandbox.bca.co.id',
        'timezone'      => 'Asia/Jakarta',
        'timeout'       => 30,
        'debug'         => true,
        'development'   => true
    );

	// Setting default timezone Anda
	BcaHttp::setTimeZone('Asia/Jakarta');

	//Or
	//BcaHttp::setTimeZone('Asia/Singapore');

	$corp_id = "BCAAPI2016";
	$client_key = "NILAI-CLIENT-KEY-ANDA";
	$client_secret = "NILAI-CLIENT-SECRET-ANDA";
	$apikey = "NILAI-APIKEY-ANDA";
	$secret = "SECRETKEY-ANDA";

	$bca = new BcaHttp($corp_id, $client_key, $client_secret, $apikey, $secret);

	//or

	$bca = new BcaHttp($corp_id, $client_key, $client_secret, $apikey, $secret, $options);
```

### LOGIN KE BCA

```php
	$corp_id = "BCAAPI2016";
	$client_key = "NILAI-CLIENT-KEY-ANDA";
	$client_secret = "NILAI-CLIENT-SECRET-ANDA";
	$apikey = "NILAI-APIKEY-ANDA";
	$secret = "SECRETKEY-ANDA";

	$bca = new BcaHttp($corp_id, $client_key, $client_secret, $apikey, $secret);

	// Request Login dan dapatkan nilai OAUTH
	$response = $bca->httpAuth();

	// LIHAT HASIL OUTPUT
	echo json_encode($response);
```

### BALANCE INFORMATION

```php
	// Nilai token yang dihasilkan saat login
	$token = "MvXPqa5bQs5U09Bbn8uejBE79BjI3NNCwXrtMnjdu52heeZmw9oXgB";

	//Nomor akun yang akan di ambil informasi saldonya
	//Saat ini hanya bisa satu nomor aku saja
	$arrayAccNumber = array('0063001004');

	$response = $bca->getBalanceInfo($token, $arrayAccNumber);
	
	// LIHAT HASIL OUTPUT
	echo json_encode($response);
```

### FUND TRANSFER

```php
	// Nilai token yang dihasilkan saat login
	$token = "MvXPqa5bQs5U09Bbn8uejBE79BjI3NNCwXrtMnjdu52heeZmw9oXgB";

	$amount = '50000.00';

	// Nilai akun bank anda
	$nomorakun = '0201245680';

	// Nilai akun bank yang akan ditransfer
	$nomordestinasi = '0201245681';

	// Nomor PO, silahkan sesuaikan
	$nomorPO = '12345/PO/2017';

	// Nomor Transaksi anda, Silahkan generate sesuai kebutuhan anda
	$nomorTransaksiID = '00000001;

	$response = $bca->fundTransfers($token, 
						$amount,
						$nomorakun,
						$nomordestinasi,
						$nomorPO,
						'Testing Saja Ko',
						'Online Saja Ko',
						$nomorTransaksiID);
```

... MORE ... Calm Down Beeb

# LICENSE

MIT License

Copyright (c) 2017 odenktools

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.