# 🧵 TextileSpace: Ecosystem Textile Retail & WMS

TextileSpace adalah purwarupa Sistem Informasi Manajemen (*Management Information System*) untuk toko tekstil modern. Sistem ini mengintegrasikan perangkat keras pemindai warna digital (*Digital Color Reader*) dengan Warehouse Management System (WMS) dan Point of Sale (POS) terpadu.

## 🚀 Fitur Inovasi Utama (Value Added)
1. **Hardware-Integrated Workstation:** Menggabungkan meja potong fisik, alat ukur digital, dan terminal kasir (POS) dalam satu stasiun untuk mencapai *Lean Overhead Cost*.
2. **HEX Color Matching Service:** Pemindaian sampel fisik pembeli yang dikonversi menjadi kode HEX 6 digit untuk pencarian stok di *database* dalam hitungan detik. Mengatasi masalah pencocokan manual dan *color blindness*.
3. **Dye-Lot Indexing:** Pelacakan *batch* produksi pabrik untuk memastikan pelanggan mendapat gulungan kain dengan *tone* warna yang 100% sama (bebas belang).
4. **Zero-Waste Scrap Management:** Pencatatan otomatis sisa potongan meteran kain (*deadstock*) ke dalam katalog *upcycling* khusus kerajinan.

## 🗄️ Skema Basis Data (Database Schema Concept)

Sistem beroperasi pada 3 tabel relasional utama:

**1. Tabel `inventory_kain`**
| Kolom | Tipe Data | Deskripsi |
|---|---|---|
| id_kain | VARCHAR | ID unik (SKU) gulungan kain |
| nama_kain | VARCHAR | Jenis kain (cth: Katun Toyobo) |
| hex_code | VARCHAR(7) | Kode warna (cth: #8F9E8B) |
| dye_lot | VARCHAR | Kode batch produksi pabrik |
| stok_meter | DECIMAL | Ketersediaan panjang di rak |

**2. Tabel `scrap_upcycle`** (Untuk kain sisa/Zero-Waste)
| Kolom | Tipe Data | Deskripsi |
|---|---|---|
| id_scrap | VARCHAR | ID unik potongan sisa |
| id_kain | VARCHAR | Referensi ke tabel `inventory_kain` |
| panjang_sisa| DECIMAL | Sisa potongan (di bawah 1 meter) |
| harga_paket | DECIMAL | Harga diskon untuk kerajinan |

## ⚙️ Alur Sistem Operasional (System Flow)
1. **Inbound:** Kain baru tiba $\rightarrow$ dipindai alat Color Reader $\rightarrow$ Sistem WMS menyimpan kode HEX dan Dye-Lot.
2. **Outbound:** Pelanggan bawa sampel $\rightarrow$ dipindai di toko $\rightarrow$ Komputer kasir menampilkan lokasi rak barang (*Smart Shelf Indexing*).
3. **Checkout:** Dipotong di stasiun terpadu $\rightarrow$ Sisa potongan terdata otomatis $\rightarrow$ Transaksi selesai.
