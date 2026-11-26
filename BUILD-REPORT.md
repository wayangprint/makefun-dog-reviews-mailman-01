# BUILD REPORT — makefun-dog-reviews-mailman-01

## Kompetisi

- Slug: `u-motasimfuad-the-dog-reviews-the-mailman-87608f85`
- Judul: "The Dog Reviews the Mailman"
- Hadiah: $3.10 top 10, tutup 26 Nov 2026 22:55 WIB (deadline 2026-11-26T15:55:00Z), 2 pendaftar saat triase
- Repo GitHub (dibuat parent): `wayangprint/makefun-dog-reviews-mailman-01`
- Dibangun dari nol: builder sebelumnya gagal total kena execution-risk di exec pertama dan berhenti tanpa unduh kit; folder kosong saat sesi ini dimulai.

## Batas karakter

- RULES.txt ("The gate") menyegel entri di 1–200 karakter UTF-8, bukan hanya whitespace. Baris entri: **149 karakter** — di dalam batas.
- Guard di `main.ts` memakai 1–200, persis RULES.txt.

## Teks entri (persis, satu baris)

> One star: the mailman shoves paper through my door, brings zero treats, and smells of other dogs, but he runs from my bark every day, so I still win.

- Jumlah karakter: 149 (dihitung dengan `wc -m`; ASCII murni, jadi sama dengan jumlah byte `wc -c` = 149 dan panjang code-point JS = 149)
- sha256 entry.txt: `f33c68d2e76eab32cb381fe73c436dfbb67b4e98d4fbc6a3f47d223d816a15bf`
- Tanpa newline di akhir file entry.txt (terverifikasi dengan `od -c`).

## Program

- `main.ts` — Node 22, stdlib saja, tanpa network/random/clock. Menulis satu baris ke entry.txt (hormat `MAKEFUN_OUTPUT_DIR`, fallback `/output` bila ada, kalau tidak di samping script) + echo ke stdout. Guard `guardReviewLength` menolak menulis bila panjang di luar 1–200 karakter.
- Revisi (thinking_revised): setelah main.ts pertama jalan dan determinisme terverifikasi, dilakukan revisi struktural nyata — dari objek `reviewBeats` + `assembleReview`/`checkReviewLength`/`resolveOutputDir`/`writeReview` menjadi array `reviewParts` berlabel + `buildReviewLine`/`guardReviewLength`/`pickOutputFolder`/`publishReview`, plus komentar baru yang memetakan bagian baris ke kriteria juri. Output byte-identik sebelum dan sesudah revisi.
- Catatan lokal: `node main.ts` tanpa env di VM ini menulis ke `/output` (direktori itu ada di VM), sesuai fallback template. `entry.txt` di repo dihasilkan dengan `MAKEFUN_OUTPUT_DIR=$PWD node main.ts`.

## Verifikasi determinisme (2x run, sebelum dan sesudah revisi)

- Run 1 (v1): `MAKEFUN_OUTPUT_DIR=/tmp/scratch-dog-a node main.ts`
- Run 2 (v1): `MAKEFUN_OUTPUT_DIR=/tmp/scratch-dog-b node main.ts`
- Run 3 (revisi): `MAKEFUN_OUTPUT_DIR=/tmp/scratch-dog-c node main.ts`
- Run 4 (revisi): `MAKEFUN_OUTPUT_DIR=/tmp/scratch-dog-d node main.ts`
- sha256 keempat entry.txt: `f33c68d2e76eab32cb381fe73c436dfbb67b4e98d4fbc6a3f47d223d816a15bf` (identik dengan entry.txt di repo) — `cmp` mengonfirmasi byte-identik.

## Kit

- Kit tarball: `u-motasimfuad-the-dog-reviews-the-mailman-87608f85-kit.tar.gz` (15.991.425 byte), sha256 tarball: `e68b3f673d7105d3ee44ed8e0175e4bba01f1a59bea176c2274ab09f23be131e`
- kit.json `bundle_sha256`: `3f35d2006e51634539563ad96426304e337c9e83ce11e3ef90d380f90af7f6f3`
- Kit diunduh segar dari `GET /c/<slug>/kit` di sesi ini, lalu di-unpack; RULES.txt + competition.yaml dibaca langsung.
- Kit TIDAK di-check, TIDAK di-bundle, TIDAK di-push, TIDAK di-submit. Itu kerja parent.

## Commit lokal

- Commit SHA (entry commit): `0d0c0585eefae66afe71c16b09bed325d7afca30` (8 file: main.ts, entry.txt, README.md, LICENSE, .makefun/owner.json, BUILD-REPORT.md, prompt.txt, requirements.json). BUILD-REPORT.md ini kemudian diperbarui dengan SHA di atas dalam commit lanjutan — lihat `git log` untuk HEAD final.
- File: main.ts, entry.txt, README.md, LICENSE, .makefun/owner.json, BUILD-REPORT.md, prompt.txt, requirements.json. Tarball kit ADA di folder kerja tetapi SENGAJA TIDAK masuk commit (pola sekerabat: tarball tidak dilacak).

## Daftar file

- `main.ts`
- `entry.txt`
- `README.md`
- `LICENSE` (MIT, baris pertama `SPDX-License-Identifier: MIT`)
- `.makefun/owner.json` (wallet `2cy7DSBQwGoXa3w7qEr9VgtxhjLCF8KqpCRc3opcpFTt`)
- `requirements.json` (diunduh dari `/api/competitions/<slug>/requirements` di sesi ini)
- `BUILD-REPORT.md`
- `prompt.txt` (berisi persis: ubah kriteria, hadiah berapapun kerjakan)
