# Jarkom_Modul3_Lapres

# Lapres Modul 3 Jarkom - Kelompok B08

Dimas Adhitya 05111840000015

Salim Bin Usman 05111840000104


1. Konfigurasi IP dhcp

*Pada UML setiap client, buka /etc/network/interfaces, isikan
```
auto eth0
iface eth0 inet dhcp
```
Banyuwangi
![alt text]() /etc/network/interfaces

Madiun
![alt text]() /etc/network/interfaces

Gresik
![alt text]() /etc/network/interfaces

Sidoarjo
![alt text]() /etc/network/interfaces


2. Surabaya sebagai DHCP Relay

Pada UML SURABAYA, install dhcp relay

```
apt-get install isc-dhcp-relay
```
Kemudian masukkan IP TUBAN (sebagai DHCP server) dan masukkan interfaces 'eth1 dan eth2'. Untuk mengaktifkan nya, pada UML SURABAYA, ketik :
```
dhcrelay IP TUBAN
```

3. Client pada subnet 1 mendapatkan range IP dari 192.168.0.10 sampai 192.168.0.100 dan
192.168.0.110 sampai 192.168.0.200.

4. Client pada subnet 3 mendapatkan range IP dari 192.168.1.50 sampai 192.168.1.70.

*Pada UML MALANG file /etc/bind/jarkom/83.151.10.in-addr.arpa, tambahkan

5. Client mendapatkan DNS Malang dan DNS 202.46.129.2 dari DHCP

6. Client di subnet 1 mendapatkan peminjaman alamat IP selama 5 menit, sedangkan (6) client
pada subnet 3 mendapatkan peminjaman IP selama 10 menit.

Pada UML TUBAN sebagai DHCP server, install isc-dhcp-server
```
apt-get install isc-dhcp-server
```
Kemudian, buka nano /etc/dhcp/dhcpd.conf dan untuk konfigurasi nya ialah seperti di gambar:

![alt text]() isc-dhcp-server TUBAN

Jangan lupa untuk uncomment, dan ubah IP menjadi SUBNET 2 agar isc-dhcp-server dapat di start

![alt text]() isc-dhcp-server TUBAN

Kemudian jalankan isc-dhcp-server
```
service isc-dhcp-server restart
```

Pada UML MALANG, untuk mendapatkan DNS install bind9 terlebih dahulu
```
apt-get install bind9
```
Lalu buka /etc/bind/named.conf.options dan tambahkan
```
forwarders {
   202.46.129.2;
};
```
Kemduian uncomment
```
// dnssec-validation auto;
```
Dan tambahkan
```
allow-query{any;};
```

![alt text]() /etc/bind/named.conf.options MALANG
