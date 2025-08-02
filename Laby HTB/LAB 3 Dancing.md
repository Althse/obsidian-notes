# 🧪 THM – Lab SMB (Dancing)

## 📡 Ping do hosta

```bash
ping 10.129.174.30
```

Wynik:

```
64 bytes from 10.129.174.30: icmp_seq=1 ttl=127 time=28.8 ms
64 bytes from 10.129.174.30: icmp_seq=2 ttl=127 time=149 ms
64 bytes from 10.129.174.30: icmp_seq=3 ttl=127 time=28.9 ms
```

## 🔍 Skanowanie portów nmap

```
nmap 10.129.174.30
```

Otwarty porty:

    135/tcp → msrpc

    139/tcp → netbios-ssn

    445/tcp → microsoft-ds

## 📂 Sprawdzanie udziałów SMB

```
smbclient -N -L \\10.129.174.30
```

Dostępne udziały:

    ADMIN$

    C$

    IPC$

    WorkShares ✅

## 🔐 Próba połączenia z udziałami
### ❌ Próby nieudane:

```
smbclient \\\\10.129.174.30\\ADMIN$
smbclient \\\\10.129.174.30\\C$
```

Wynik:

```
tree connect failed: NT_STATUS_ACCESS_DENIED
```

## ✅ Połączenie do WorkShares

```
smbclient \\\\10.129.174.30\\WorkShares
```

📁 Struktura katalogów:

    Amy.J

    James.P

## 📥 Pobranie pliku flag.txt z James.P

```
cd James.P\
ls
get flag.txt
```

Zawartość:

```
5f61c10dffbc77a704d76016a22f1664
```

## 📥 Pobranie pliku worknotes.txt z Amy.J

```
cd Amy.J\
ls
get worknotes.txt
```

Zawartość:

- start apache server on the linux machine
- secure the ftp server
- setup winrm on dancing

## 📝 Zapis całej sesji tmux do pliku:

```
tmux capture-pane -pS -1000 > zapis.txt
```