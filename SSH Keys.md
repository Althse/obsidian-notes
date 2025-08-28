# SSH Keys w Praktyce (Pentesting / Lab)

## 1. Tworzenie pary kluczy SSH

Na swoim komputerze/labie tworzysz **parę kluczy**:

```bash
ssh-keygen -f mykey
```

mykey → Private Key (klucz prywatny, zostaje u Ciebie)
mykey.pub → Public Key (klucz publiczny, który wrzucisz na serwer)

Opcjonalnie: Możesz ustawić passphrase dla klucza, aby zwiększyć bezpieczeństwo.
## 2. Sprawdzenie uprawnień i przygotowanie katalogu .ssh na serwerze

Załóżmy, że zalogowałeś się na serwer jako zwykły użytkownik lub w laboratorium masz dostęp do konta testowego:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

mkdir -p ~/.ssh → tworzy katalog .ssh jeśli go nie ma

chmod 700 ~/.ssh → katalog dostępny tylko dla właściciela

## 3. Dodanie publicznego klucza do authorized_keys

Twój public key (mykey.pub) kopiujesz do pliku authorized_keys użytkownika, którego konto chcesz przejąć lub przetestować:

```bash
cat ~/mykey.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

cat → dodaje klucz publiczny do authorized_keys

chmod 600 → plik czytelny tylko dla właściciela

Ważne: publiczny klucz trafia na serwer. Private key zawsze zostaje u Ciebie.

### 4. Logowanie się za pomocą klucza prywatnego

Na swoim komputerze/labie logujesz się do serwera używając private key:

```bash
ssh user@server -i ~/mykey
```

-i ~/mykey → wskazuje plik z private key

Teraz SSH używa pary kluczy: publiczny na serwerze i private u Ciebie, aby uwierzytelnić dostęp.

## 5. Schemat działania

[Twoja maszyna]                  [Serwer]
----------------                  ----------------
Private key (mykey)      --->     brak (zostaje u Ciebie)
Public key (mykey.pub)   --->     ~/.ssh/authorized_keys
                                  
```bash
Logowanie: ssh user@host -i mykey
```

Jeśli private key pasuje do publicznego klucza w authorized_keys, serwer pozwala na zalogowanie bez hasła.

Jeśli nie, dostęp zostaje odrzucony.

## 6. Realny scenariusz

Typowe w pentestingu:

- Masz ograniczony dostęp do konta użytkownika.

- Sprawdzasz, czy możesz odczytać katalog .ssh innych użytkowników (np. root).

- Jeśli masz write access do authorized_keys, możesz dodać swój public key.

- Następnie logujesz się tym kluczem i przejmujesz konto bez hasła.

- Ważne dla bezpieczeństwa:

- Public key musi być tylko w katalogu właściciela i z odpowiednimi prawami (700 dla .ssh, 600 dla authorized_keys)

- Private key nigdy nie trafia na serwer

## 7. Podsumowanie

1. Tworzysz parę kluczy (private + public).

2. Wrzucasz public key na serwer do authorized_keys.

3. Logujesz się private key.

4. Scenariusz użycia: pentesting, laboratoria bezpieczeństwa, automatyzacja bez haseł.

5. Prawa dostępu muszą być restrykcyjne, inaczej SSH odmówi działania klucza.