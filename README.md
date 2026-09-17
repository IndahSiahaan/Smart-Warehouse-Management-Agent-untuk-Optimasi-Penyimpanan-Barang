# Smart Warehouse Management Agent untuk Optimasi Penyimpanan Barang

Proyek Milestone Terpadu — Mata Kuliah Kecerdasan Buatan (10S3001)
Institut Teknologi Del, Program Studi Sarjana Sistem Informasi

**Anggota Tim:** Nicolas J Grace Butarbutar, Indah, Swasti
**Dosen Pengampu:** Samuel Indra Gunawan Situmeang

## Deskripsi Proyek

Repositori ini berisi implementasi baseline untuk **Smart Warehouse Management
Agent**, sebuah agen cerdas yang membantu menentukan lokasi penyimpanan optimal
(*put-away*) dan rute pengambilan barang optimal (*retrieval*) pada gudang
fulfillment e-commerce.

Gudang dimodelkan sebagai graf berbobot, di mana:
- **Node** merepresentasikan titik pada peta gudang (dock penerimaan,
  persimpangan lorong, slot rak).
- **Edge** merepresentasikan jarak/waktu tempuh riil antar-titik.

Modul pencarian mengimplementasikan **Uniform Cost Search (UCS)** dan
**A\* Search** (dengan heuristik Manhattan distance) untuk menemukan
lintasan berbiaya minimum dari dock penerimaan menuju slot rak tujuan.

Dokumen lengkap Problem Framing dan spesifikasi PEAS tersedia pada berkas
laporan Milestone 1 (`Laporan_Milestone1_SmartWarehouseAgent.docx` /
`GrupXX-Tugas01.pdf`).

## Struktur Direktori

```
smart-warehouse-agent/
├── README.md
├── LICENSE
├── .gitignore
├── pyproject.toml
├── requirements.txt
└── src/
    └── warehouse_search.py
```

## Instalasi & Menjalankan Proyek

Proyek ini menggunakan [uv](https://docs.astral.sh/uv/) (Astral) sebagai
manajer paket dan lingkungan Python.

### Opsi 1 — menggunakan uv (direkomendasikan)

```bash
# instal uv jika belum ada
curl -LsSf https://astral.sh/uv/install.sh | sh

# sinkronisasi environment sesuai pyproject.toml
uv sync

# jalankan skrip baseline search
uv run src/warehouse_search.py
```

### Opsi 2 — menggunakan pip + requirements.txt

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python src/warehouse_search.py
```

## Contoh Output

```
=== Uniform Cost Search: DOCK -> R5 ===
Path: DOCK -> J1 -> J2 -> J3 -> J4 -> R5
Total cost: 21.00
...

=== A* Search: DOCK -> R5 ===
Path: DOCK -> J1 -> J2 -> J3 -> J4 -> R5
Total cost: 21.00
...
```

## Kontribusi Tim

| Anggota | Peran |
|---|---|
| Indah | Business Analyst / Problem Framer |
| Swasti | PEAS Specialist & Dokumentasi |
| Nicolas | Algorithm Engineer & Repo Setup |

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).
