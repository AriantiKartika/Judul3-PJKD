# Simulasi Jaringan VIRTUAL LAN

Repository ini berisi tugas simulasi jaringan komputer menggunakan **Cisco Packet Tracer**. Proyek ini mendemonstrasikan konfigurasi VLAN, Trunking, dan implementasi Inter-VLAN Routing menggunakan metode *Router-on-a-Stick*.

## 👤 Identitas Mahasiswa

* **Nama:** Arianti Kartika Dewi
* **NPM:** 2315061047
* **Kelas:** PJK-D

## File Project

* `ta 3.pkt`: File simulasi Cisco Packet Tracer (Source file).
* Tautan video youtube: https://youtu.be/hwpKl1MdQuU 

## 🛠¸ Topologi Jaringan

Simulasi ini terdiri dari perangkat berikut:
* **2 Unit PC:** Berada dalam VLAN 10 (Operations).
* **2 Unit Switch (2960):** Berada dalam VLAN 99 (Management) dan berfungsi sebagai Layer 2 device.
* **1 Unit Router:** Berfungsi sebagai *Gateway* untuk menghubungkan VLAN 10 dan VLAN 99.

## Alur Konfigurasi (Workflow)

Berikut adalah ringkasan langkah-langkah konfigurasi yang dilakukan dalam file `ta 3.pkt`:

1.  **Desain Topologi Fisik**
    * Menghubungkan PC ke Switch dan antar Switch menggunakan kabel Straight/Cross.
    * Menambahkan Router yang terhubung ke Switch 1 (S1).

2.  **Konfigurasi VLAN (Virtual Local Area Network)**
    * Membuat **VLAN 10** (Operations) untuk trafik data pengguna (PC).
    * Membuat **VLAN 99** (Management) untuk manajemen Switch.
    * Mengatur *Port Security* dan memasukkan port PC ke akses VLAN 10.

3.  **Konfigurasi Trunking**
    * Mengaktifkan mode **Trunk** pada port penghubung antar Switch (S1 ↔ S2).
    * Mengaktifkan mode **Trunk** pada port penghubung Switch ke Router (S1 ↔ Router).
    * Hal ini memungkinkan satu kabel fisik membawa trafik dari berbagai VLAN.

4.  **Konfigurasi Inter-VLAN Routing (Router-on-a-Stick)**
    * Mengaktifkan interface fisik pada Router.
    * Membuat **Sub-interface** pada Router (misal: `g0/0.10` dan `g0/0.99`).
    * Melakukan enkapsulasi `dot1Q` agar Router dapat mengenali tag VLAN.
    * Memberikan IP Gateway pada masing-masing sub-interface.

5.  **Pengaturan Gateway**
    * Mengatur *Default Gateway* pada PC agar bisa berkomunikasi ke luar network.
    * Mengatur *IP Default Gateway* pada Switch agar Switch (VLAN 99) bisa di-ping dari PC (VLAN 10).

## Cara Menjalankan

1.  Pastikan kamu memiliki **Cisco Packet Tracer** terinstal di komputer (Disarankan versi terbaru).
2.  Clone repository ini atau download file `ta 3.pkt`.
3.  Buka file `ta 3.pkt` menggunakan Cisco Packet Tracer.
4.  Gunakan fitur *Add Simple PDU (P)* untuk melakukan tes ping antar PC atau dari PC ke Switch untuk memverifikasi konektivitas.

---
*Dibuat untuk memenuhi tugas mata kuliah Praktikum Jaringan Komputer.*
