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

![alt text](https://lh4.googleusercontent.com/zOuyXOpGZUwjOiqdgyABK-5cO0QZZdYqllIVm1LCdEmcVvPDS7azyvJxKP76oifriCvPytWq9Ln_dqGCszT5SbMgyGfjc6d0pznIAnQ)

Madiun

![alt text](https://lh5.googleusercontent.com/TAkMt-Ky37paIrEXvyPbPu0vBeGi6JTTsCraTH6vIC1r29Y8B3EqWDB9Bil-G3PaR4I6MQHVIz7npMD2fzAIa-gDCiFKG7ps0AguRuSmHNQ0krrXDaA7t6d0uM4iyiOmSNGkUlQL)

Gresik

![alt text](https://lh5.googleusercontent.com/EcY7wR8PKf3JLKd6vf3wYtjWa6m5IoVh9kq5rSIWLEYyPN-QDwgmiGEp-YpQf1sJYh8f25U_vvB0bVw46Xdn9DFBlSH_KNiKQkPbFC981TeafYy2ygsexXLYMRESD2WiSPfpXp6J)

Sidoarjo

![alt text](https://lh5.googleusercontent.com/EWStb-yUTuEVeAAKnBrP5TztHY3guF4rkYtVd-K3LRS6xpBbNffl7Q_mT7LH6UT-cGfjVwJnRRFgPGpWPo4fUy9W9PFLQndHiuHsgVyAWeAlFMO2XlXZCbA6DDRCyjfkNiv7Fc7z) 


2. Surabaya sebagai DHCP Relay

Pada UML SURABAYA, install dhcp relay

```
apt-get install isc-dhcp-relay
```
Kemudian masukkan IP TUBAN (sebagai DHCP server) dan masukkan interfaces 'eth1 dan eth2'. Untuk mengaktifkan nya, pada UML SURABAYA, ketik :
```
dhcrelay IP TUBAN
```

![alt text](https://lh4.googleusercontent.com/WiS5lYFJGnJSo5dcerqd4VN4IEzf0-MNdIXgJ_R_2GP2gn4-HYHYticqgZDwsyovSYexnhb7WnLrGXIQd-IKeljNHUCtpYD4FfqTxb9OKjaVymjNNoF8cvTmCs7Kd0_-Et52Pwe3)


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

![alt text](https://lh4.googleusercontent.com/HluuIhpo63S0IgkKihXizUBJQcKBV0UwGUQqNtg_N_Z_U_aYwZEiBigkrIrpMooqZeYtYy2FQwCxISeKiNQyiIOYZgr9sB2IVI9v-lMCotr7MqsV5KEX6s7DcqqD5LavPKDWk4oy)

Jangan lupa untuk uncomment, dan ubah IP menjadi SUBNET 2 agar isc-dhcp-server dapat di start

![alt text](https://lh4.googleusercontent.com/rB7YtnvcWS6ajtFqfl_yQYpEBQ9AFC00E7_J-PmhpiEOBSJNrs2pdtPARu_y7SWgw-awrofCt0TV7h6zUBmxvJJ9iFJrofejMQjt_K5Gwld5rA_9Z3xKntdHyjpWDQ7oyXsbQtjI)

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

![alt text](https://lh4.googleusercontent.com/dOebQnYHMxMSH0fK-SKciYKwbzx7rHu3I2u7KA3QYFgfszvhULApuJY2RIxNJewmSr3LutTpRy8eydP6-xX1tjSrB90aQYjUs0DlER_BTH4rs8wFfbUURQePfn4W2uIGAgeccumR)

## Hasil DHCP Client :

Banyuwangi :

![alt text](https://lh4.googleusercontent.com/mro82rVEMz3TDS6ib8DlEk-vvsIxgHtch8Ln8XqncSK8Mlf9PBpV6kvs40tLceiJTkKlJ0HnVQl3L2BiNMHoX5IUYi9LhlPiV25o6IU)

![alt text](https://lh4.googleusercontent.com/eNIr0wJUgmIGQD5AqLcpGZFNajtr-IC70IA0QzNqNogw0OLmyEjbvI_2YPsS6I1ALKLDaUshm-W0g_3r4Hvdp9zq1XaJN54K7FJwP00UQEvoOcmrDWNuv8Uk2kN-wwTeNKLMBp2K)


Madiun :

![alt text](https://lh6.googleusercontent.com/TTOLhPkXApfczQBWca7DKLEVRTLeBdQkNxsXoOzN8jlO_hzS3-4SnAa1qOeNuELfqJynOQ6lxfxRD4mJvFU4JB8P3ACAEN8YU-j6HxyfFgyr-nGsuA3kjIeiY2J1UF66J4I-smmD)

![alt text](https://lh3.googleusercontent.com/4Be8cr-jLXvWmK2F6Fjozk-etYh-q_HdedF12sMfkZ3rVAOYzieX4IUTtcw20dAmlxR0RLZ36iPr6pd52Y6PQjSxemGvhB2_EXCxNTmjkf47c8bg4FBNZZOO-XD7YwQ0FFKnXm7A)


Gresik :

![alt text](https://lh5.googleusercontent.com/geaJ6pnxWva89In9wGZw47dIcOxJHpi_X-6pflBnYG1Uq8JTNnXuYr-rLpbwPoDvxB-d4htUgcrEsgQobDxEDn4GUIVhwDkPdVBVtR8dabWNi08mUXMzTAqJYSzwFL3WoH-zQX_m)

![alt text](https://lh5.googleusercontent.com/py2_z3UVpQ7GyDiXex8FN_Oppj1KGOVrSJG3QD-b1E-l0_R5En5kOgIgrok2CIOB028yPUjkHwWeQla0uA2MqmDB8iOARoDFBRK1gc2yDrWDrSBlvl5nodcOHE_8jjNf3jsUzTG3)


Sidoarjo :

![alt text](https://lh5.googleusercontent.com/-rcaShV5GrPSu9XJlS3fUaVAI1lXNg2Xu0qhpE2wi9Da9q2Weh4aPzWSp3U6CKTUO_sev33v_SZMokMk3BsZWv9i-NMjisgkYRaDnymNoDIllgZ8ZUFXmNJ47nPjVNe4i5rp7Z3Y)

![alt text](https://lh5.googleusercontent.com/pONqJCkcneucSSs-90l8ZgoLUxjXhy6eqZUJWhw5E3hnLOQ6ExkQuQRJZTQmyai1Ug2zp2YQaj7IDivtSFWIdxxo8ulTKRK7DMyezN8ngPGM_zqmntyRmSFaqtud4Ohq3n_PkuqM)


