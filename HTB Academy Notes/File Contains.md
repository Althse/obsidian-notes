###  1. How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)

```bash
netstat -tuln4 | grep -v "127.0.0.*" | grep "LISTEN" | wc -l

```
## Wyjaśnienie:
### 1️⃣ `netstat -tuln4`

- `netstat` → pokazuje aktywne połączenia sieciowe i nasłuchujące porty.
    
- `-t` → **TCP** (połączenia TCP).
    
- `-u` → **UDP** (połączenia UDP).
    
- `-l` → **listening** → tylko porty, które nasłuchują na przychodzące połączenia.
    
- `-n` → **numerycznie** → nie rozwiązuje nazw hostów ani nazw usług (pokazuje numery IP i portów).
    
- `-4` → **IPv4** → ignoruje IPv6.
    

✅ Czyli razem: pokaż wszystkie TCP i UDP porty nasłuchujące na IPv4 w formie numerycznej.
### 2️⃣ `grep -v "127.0.0.*"`

- `grep` → filtruje linie.
    
- `-v` → **negacja** → usuwa linie pasujące do wzorca.
    
- `"127.0.0.*"` → wzorzec dla **localhost (127.0.0.1)**.
    

✅ Efekt: usuwa wszystkie porty nasłuchujące wyłącznie na localhost, zostawiając tylko te dostępne na innych interfejsach (np. 0.0.0.0).
### 3️⃣ `grep "LISTEN"`

- `grep` → filtruje linie pasujące do wzorca `"LISTEN"`.
    
- `LISTEN` to stan TCP dla portów nasłuchujących.
    

⚠️ UDP **nie ma stanu LISTEN**, więc ten filtr zostawia tylko TCP nasłuchujące.
### 4️⃣ `wc -l`

- `wc` → word count, czyli liczy linie, słowa lub znaki.
    
- `-l` → **liczba linii**.
    

✅ Efekt końcowy: liczba linii w wyniku, czyli **liczba usług TCP nasłuchujących na wszystkich interfejsach IPv4, bez localhost**.

### 2. Determine what user the ProFTPd server is running under. Submit the username as the answer.

```bash
ps aux | head -n 1; ps aux | grep proftpd

```

## Wyjaśnienie:
- `head -n 1` → wyświetla nagłówki
    
- `ps aux | grep proftpd` → pokazuje tylko linie z proftpd
    
- Efekt: nagłówki + procesy ProFTPd
## Opcjonalnie:
```bash
cat /etc/proftpd/proftpd.conf | grep -i "^User"

```
- `-i` → ignoruje wielkość liter (User lub user)
    
- `^User` → szuka linii zaczynających się od `User`
    
- Przykładowy wynik:
	```sql
	User proftpd

	```

### 3. Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths (https://www.inlanefreight.com/directory" or "/another/directory") of that domain. Submit the number of these paths as the answer.
