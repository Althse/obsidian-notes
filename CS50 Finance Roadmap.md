## 🗓 Plan na 7 dni – CS50 Finance

### ✅ Dzień 1 – Przygotowanie fundamentów

- Zainstaluj / upewnij się, że działa `cs50`, Flask i SQLite.
    
- Utwórz projekt, odpal Flask (`flask run`) i sprawdź, że strona się otwiera.
    
- Zrób strukturę katalogów:
```bash
/templates
/static
app.py
finance.db
```
- Utwórz pustą bazę `finance.db`.
    

🎯 **Cel dnia:** Masz działający Flask + pustą bazę.

### ✅ Dzień 2 – Użytkownicy

- Utwórz tabelę `users` z kolumnami: `id, username, hash, cash`.
    
- Zaimplementuj **register** (hashowanie hasła `generate_password_hash`).
    
- Zaimplementuj **login** (sprawdzanie hasła `check_password_hash`, sesje).
    
- Dodaj **logout**.
    

🎯 **Cel dnia:** Rejestracja/logowanie działa. Możesz założyć konto i się logować.

---

### ✅ Dzień 3 – Wyświetlanie portfela

- Po zalogowaniu użytkownik widzi stronę **index**.
    
- Wyświetl listę posiadanych akcji (na razie na sztywno, bez kupna).
    
- Dodaj wyświetlanie **gotówki** użytkownika.
    

🎯 **Cel dnia:** Index działa jako „dashboard”.

---

### ✅ Dzień 4 – Kupno akcji

- Utwórz tabelę `transactions` (`id, user_id, symbol, shares, price, type, time`).
    
- Zaimplementuj formularz do wpisania symbolu i liczby akcji.
    
- Użyj `lookup(symbol)`, aby sprawdzić cenę (API).
    
- Sprawdź, czy użytkownik ma wystarczająco gotówki.
    
- Dodaj wpis w `transactions`, zaktualizuj cash w `users`.
    

🎯 **Cel dnia:** Możesz kupować akcje i baza się aktualizuje.

---

### ✅ Dzień 5 – Sprzedaż akcji

- Na podstawie posiadanych akcji daj możliwość ich sprzedaży.
    
- Sprawdź, czy user ma tyle akcji, ile chce sprzedać.
    
- Zaktualizuj bazę i cash.
    

🎯 **Cel dnia:** Kupno i sprzedaż działają.

---

### ✅ Dzień 6 – Historia i wykończeniówka

- Zaimplementuj stronę **history** – lista wszystkich transakcji.
    
- Dodaj stronę **quote** – wyszukiwarka ceny akcji.
    
- Dodaj stronę **add cash** (bonus).
    

🎯 **Cel dnia:** Aplikacja jest kompletna, masz wszystkie funkcjonalności.

---

### ✅ Dzień 7 – Styl i testy

- Uporządkuj HTML + Jinja.
    
- Dodaj Bootstrap dla wyglądu.
    
- Przetestuj każdy przypadek:
    
    - brak środków,
        
    - próba sprzedaży akcji, których nie ma,
        
    - rejestracja użytkownika o tym samym loginie.
        

🎯 **Cel dnia:** Aplikacja działa i wygląda schludnie – możesz oddać.