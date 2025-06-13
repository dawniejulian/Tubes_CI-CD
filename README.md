```markdown
🚀 Tugas Besar CI/CD - Java Maven Project

Repositori ini merupakan implementasi dari **CI/CD (Continuous Integration, Testing, Inspection, Deployment)** menggunakan **GitHub Actions** untuk tugas besar mata kuliah [NAMA MATA KULIAH ANDA].

Kami adalah kelompok yang terdiri dari 2 orang, sehingga fokus CI/CD kami adalah:
- Continuous Testing ✅
- Continuous Inspection ✅
- Continuous Deployment ✅

---

## 👥 Anggota Kelompok

| Nama Lengkap           | NIM            | Tugas                          |
|--------------------    |----------------|--------------------------------|
| Dawnie Julian Nugroho  | 2211104064     | Continuous Testing & Deployment|
| Mohammad Fathurrohman  | 2211104070     | Continuous Inspection          |

---

## 📦 Teknologi dan Tools

- Bahasa: **Java 17**
- Build Tool: **Maven**
- Test Framework: **JUnit 5**
- Code Inspection: **Checkstyle**
- CI/CD Orchestrator: **GitHub Actions**

---

## 🧾 Tujuan Pipeline CI/CD

1. **Continuous Testing:** Menjalankan unit test otomatis setiap kali ada perubahan kode.
2. **Continuous Inspection:** Menjalankan pengecekan kualitas kode (style/linting).
3. **Continuous Deployment:** Menjalankan simulasi deploy bila semua tahap berhasil.

---

## 📁 Struktur Folder & File Penting

```

.
├── .github/
│   └── workflows/
│       └── ci-cd.yml        # Konfigurasi GitHub Actions
├── pom.xml                  # Konfigurasi project Maven & plugin Checkstyle
├── src/
│   ├── main/java/com/example/App.java        # Kode utama
│   └── test/java/com/example/AppTest.java    # Unit test
└── README.md                # Laporan dan panduan proyek

````

---

⚙️ Cara Kerja Pipeline (GitHub Actions)

Workflow pipeline otomatis berjalan saat terjadi **push** ke branch `main`.

### 1. `test` - Continuous Testing
- Menjalankan perintah `mvn test`
- Mengeksekusi semua unit test JUnit yang tersedia
- Jika gagal, pipeline berhenti

### 2. `inspection` - Continuous Inspection
- Menjalankan `mvn checkstyle:check`
- Mengecek standar penulisan kode (coding style)
- Hanya dijalankan jika `test` berhasil

### 3. `deploy` - Continuous Deployment
- Menjalankan `echo "Deploying to production..."`
- Sebagai simulasi deploy (dummy)
- Hanya dijalankan jika inspection berhasil

---

## 💻 Menjalankan Manual di Lokal

### 1. Cek Java & Maven
```bash
java -version
mvn -v
````

### 2. Jalankan Unit Test

```bash
mvn test
```

### 3. Jalankan Code Inspection

```bash
mvn checkstyle:check
```

### 4. Simulasi Deploy

```bash
echo "Deploying to production..."
```

---

## 📄 Isi File `.github/workflows/ci-cd.yml`

```yaml
name: Java CI/CD Pipeline

on:
  push:
    branches: [ "main" ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      - name: Run Tests
        run: mvn test

  inspection:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      - name: Run Checkstyle
        run: mvn checkstyle:check

  deploy:
    needs: inspection
    runs-on: ubuntu-latest
    steps:
      - name: Dummy Deploy
        run: echo "Deploying to production..."
```

## ✅ Status Pipeline GitHub Actions

![CI/CD Status](https://github.com/dawniejulian/Tubes_CI-CD/actions/workflows/ci-cd.yml/badge.svg)

---
