# Asal tiap bagian skill ini

Skill ini menggabungkan dua repo upstream menjadi satu skill Muse. Salinan repo
lengkap tersimpan di `~/workspace/research/menulis-cep4t-upstream` dan
`~/workspace/research/naskah-id-upstream`.

## Repo sumber

- MenulisCep4t di `https://github.com/FRCHN-GSTN/MenulisCep4t`, komit
  `ba5389f` tanggal 2026-10-26. Fork dari `muadzhdz/laporan-generator`.
  Versi 3.0.0 menggabungkan tiga repo menjadi satu, yaitu engine dokumen
  laporan-generator, penyunting naskah-id, dan pola tulisan AI humanizer.
- naskah-id di `https://github.com/nothinx/naskah-id`, komit `e18d574`
  tanggal 2026-10-23. Upstream komponen penyunting.

## Bagian yang identik di kedua repo

Berkas berikut sama persis byte demi byte di kedua komit di atas, jadi hanya
disimpan sekali di skill ini. Asal pertamanya adalah naskah-id.

- `KONTRAK.md`
- `references/` kecuali `pola-ai-inggris.md`, yaitu alat-riset, bagian-naskah,
  ejaan-eyd-v, istilah, kalimat-efektif, kata-baku, pertahankan, pola-ai,
  singkatan, dan sitasi
- `scripts/periksa.py` dan `scripts/openalex.py`
- `contoh/` beserta korpusnya
- `evals/` yaitu banding.py, cases.json, dan jalankan.py

## Bagian yang hanya datang dari naskah-id

- Panduan penyuntingan lengkap di `SKILL.md` naskah-id yang diringkas atau
  dihapus saat MenulisCep4t mengadaptasinya. Skill ini memulihkannya ke dalam
  `SKILL.md`, yaitu aturan tiga tingkat penandaan K, G, dan AI beserta kapan
  tiap tingkat diperbaiki, larangan menebak gaya sitasi, alur naskah panjang
  per bab dengan daftar istilah dan laporan per bab, butir periksa konsistensi
  istilah teknis, kewajiban menjelaskan setiap baris laporan `--banding`
  sebelum penyerahan, urutan pencarian rujukan dengan penawaran penyambungan
  alat sekali per sesi, seluruh bagian ciri prosa yang natural, dan batas
  cakupan naskah berbahasa Inggris.
- Hasil eval di `CHANGELOG.md` naskah-id, yaitu eval 25 kasus dengan agen
  Claude Haiku yang naik dari 56 ke 70 dari 76 kriteria penilai saat memakai
  skill, serta temuan `periksa.py` per 100 kata yang turun pada tiap tingkat.

## Bagian yang hanya datang dari MenulisCep4t

- Mesin bangun dokumen di `resources/`, yaitu template.typ, docx.lua,
  build.sh, build-docx.sh, Makefile, laporan, reference.docx, apa.csl,
  metadata.yml, cover.md, chapters, dan references.bib.
- `presets/` dengan 14 preset kampus, yaitu standard, skripsi-4433,
  ui-skripsi, itb-ta, ugm-skripsi, its-skripsi, unpad-skripsi, ub-skripsi,
  undip-skripsi, unair-skripsi, ipb-ppki, telkom-ta, gunadarma-skripsi, dan
  paper-ilmiah.
- `docs/` dengan enam panduan, yaitu campus-guide, metadata-schema,
  preset-schema, syntax-cheatsheet, template-guide, dan troubleshooting.
- `references/pola-ai-inggris.md` dengan 26 pola tulisan AI berbahasa Inggris,
  dari penggabungan humanizer.
- `scripts/` di skill ini juga memuat skrip pipa build dari MenulisCep4t,
  yaitu bundle, docx-pagenum, finalize-docx, make-reference-docx,
  report-doctor, report-stats, dan test_scripts, karena `build-docx.sh`,
  `Makefile`, dan `laporan` memanggilnya dari folder proyek. Skrip
  `setup-deps` sengaja tidak disalin karena mengubah instalasi sistem.
- Lapisan MCP dan CLI di `lib/` dan `bin/` pada salinan repo, termasuk
  perintah init, doctor, stats, preset, dan build. Lapisan ini tidak disalin
  ke skill, dan perintah `sync-hosts` tidak pernah dijalankan karena mengubah
  konfigurasi host lain.

## Perbedaan yang dicatat

- `periksa.py --tes` lulus penuh 108 dari 108 kasus di naskah-id. Di
  MenulisCep4t, 108 kasus deteksi yang sama lulus, tetapi cek metadata
  bawaannya melaporkan 2 galat karena fork mengubah nama skill menjadi
  laporan-generator dan mengubah panjang deskripsi. Logika pemeriksa di kedua
  repo identik.
- `presets/` tidak ada di akar repo MenulisCep4t. Preset tersimpan di
  `.agents/skills/laporan-generator/resources/presets/` dan disalin ke skill
  dari sana.
- Berkas `laporan` membawa BOM UTF-8 sehingga mencetak peringatan baris
  pertama saat dijalankan, tetapi tetap berjalan. Jalankan lewat `bash`
  secara eksplisit.
