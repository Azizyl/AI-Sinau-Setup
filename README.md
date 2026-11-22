# AI Sinau Setup

Kumpulan skill AI untuk belajar — disusun untuk mahasiswa statistika, tapi bisa
dipakai siapa saja. *Sinau* (Jawa) = belajar.

A curated collection of AI skills for studying — put together for statistics
students, but useful for anyone. Each skill is a folder with a `SKILL.md` that
any AI agent can read and follow.

## Skills included

| Skill | Untuk apa | Lisensi | Sumber |
|---|---|---|---|
| [sympy](skills/sympy) | Matematika simbolik: aljabar, kalkulus, distribusi peluang (`sympy.stats`) | MIT | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) |
| [matplotlib](skills/matplotlib) | Visualisasi data: histogram, scatter, boxplot, kurva distribusi | MIT | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) |
| [study-atlas](skills/study-atlas) | Ubah slide/PDF kuliah jadi aplikasi belajar interaktif (mind map, flashcard, mock exam) | MIT | [phanthanhdieulinh/study-atlas](https://github.com/phanthanhdieulinh/study-atlas) |
| [anthropic-document-skills](skills/anthropic-document-skills) | Membuat dan menyunting docx, xlsx, pptx, pdf | Apache 2.0 | [anthropics/skills](https://github.com/anthropics/skills) |
| [dotclaude-citations](skills/dotclaude-citations) | Kelola dan verifikasi sitasi (BibTeX, Crossref, OpenAlex) | MIT | [KhaledSaeed18/dotclaude](https://github.com/KhaledSaeed18/dotclaude) |
| [academic-research-skills](skills/academic-research-skills) | Riset mendalam, penulisan paper, peer review, systematic review | CC BY-NC 4.0 | [imbad0202/academic-research-skills](https://github.com/imbad0202/academic-research-skills) |
| [menulis-cep4t](skills/menulis-cep4t) | Penulisan akademik Bahasa Indonesia (EYD V, KBBI) sampai PDF/DOCX | MIT | [FRCHN-GSTN/MenulisCep4t](https://github.com/FRCHN-GSTN/MenulisCep4t) + [nothinx/naskah-id](https://github.com/nothinx/naskah-id) |

Setiap folder skill menyimpan berkas lisensi aslinya dan `PROVENANCE.md` yang
mencatat repo asal, komit, lisensi, dan adaptasi yang dibuat. Beberapa skill
diadaptasi ringan dari upstream-nya (mis. penyesuaian untuk Muse); detailnya
ada di `PROVENANCE.md` masing-masing.

## Cara memakai

1. Clone repo ini.
2. Salin folder skill yang dibutuhkan ke direktori skill AI-mu (mis.
   `~/.claude/skills/`, `~/workspace/custom-skills/`, atau sesuai agen yang
   kamu pakai).
3. Setiap skill punya `SKILL.md` (instruksi untuk agen) dan, bila ada,
   `references/` serta `scripts/` pendukung.

## Tidak dimasukkan — dengan alasan

- **natural-indonesian** — repo asalnya tidak menyatakan lisensi apa pun, jadi
  tidak boleh didistribusikan ulang. Lihat upstream:
  [SandyFauzi/SYNESIS](https://github.com/SandyFauzi/SYNESIS).
- **Skill bawaan Muse** (documents, wide-research, knowledge-organization,
  transcribe-recordings, form-design, translation) — milik produk Muse, bukan
  open source, jadi tidak disertakan sebagai berkas. Tersedia di dalam Muse.

## Lisensi

Tiap skill memakai lisensinya sendiri (lihat berkas `LICENSE` di tiap folder
skill; `academic-research-skills` berlisensi CC BY-NC 4.0 — hanya untuk
penggunaan non-komersial). Berkas asli repo ini (README dan katalog) dirilis
di bawah lisensi MIT — lihat [LICENSE](LICENSE).
