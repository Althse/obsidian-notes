### Examples
#### These exercises will use the `/etc/ssh/sshd_config` file

|     |                                                                        |
| --- | ---------------------------------------------------------------------- |
| 1   | Show all lines that do not contain the `#` character.                  |
| 2   | Search for all lines that contain a word that starts with `Permit`.    |
| 3   | Search for all lines that contain a word ending with `Authentication`. |
| 4   | Search for all lines containing the word `Key`.                        |
| 5   | Search for all lines beginning with `Password` and containing `yes`.   |
| 6   | Search for all lines that end with `yes`.                              |
## 1.
```bash
grep -Ev "#|^$" /etc/ssh/sshd_config
```

- `|^$` → dodaje pustą linię do dopasowania, więc `-v` je odrzuca
## 2.
```bash
grep -E "\bPermit\w*" /etc/ssh/sshd_config
```
### Wyjaśnienie:

- `-E` → Extended Regular Expressions, pozwala używać `\w*` i innych rozszerzeń.
- `\b` → granica słowa, czyli `Permit` musi być początkiem słowa.
- `Permit` → ciąg znaków, od którego ma się zaczynać słowo.
- `\w*` → dowolna liczba znaków alfanumerycznych po `Permit`.

## 3.
```bash
grep -E "\b\w*Authentication\b" /etc/ssh/sshd_config
```
### Wyjaśnienie krok po kroku:

- `-E` → Extended Regular Expressions (umożliwia użycie `+`, `*`, `|` bez backslashy).
- `\b` → granica słowa (word boundary).
- `\w*` → dowolna liczba znaków alfanumerycznych przed `Authentication`.
- `Authentication` → końcówka słowa, którą chcemy dopasować.
- `\b` → końcowa granica słowa.

## 4.
```bash
grep "Key" /etc/ssh/sshd_config
```
To jednak wyświetla wszystkie słowa których część składowa to Key, gdybym chciał tylko słowo "Key" należałoby użyć:
```bash
grep -w "Key" /etc/ssh/sshd_config
```
### Wyjaśnienie:

- `grep` → przeszukuje plik linia po linii.
- `-w` → dopasowuje **całe słowa**, czyli `Key` nie zostanie dopasowane np. w `KeyFile`.
- `"Key"` → szukane słowo.

## 5.

Genaralnie powinno być:
```bash
grep -E "^Password\s+.*yes" /etc/ssh/sshd_config
```
### Wyjaśnienie krok po kroku:

- `-E` → Extended Regular Expressions (możesz używać `+`, `|` bez backslashy)
- `^Password` → linia zaczyna się od `Password`
- `\s+` → co najmniej jedna spacja lub tabulator po `Password`
- `.*` → dowolne znaki po spacji (np. komentarze, inne dyrektywy)
- `yes` → musi zawierać słowo `yes` w linii

Ale w moim pliku /etc/ssh/sshd_config ta linia jest zakomentowana poprzez "#" na początku, aby ją wydobyć należy wpisać:

```bash
rep -i "Password" /etc/ssh/sshd_config | grep -i "yes"
```

## 6.

```bash
grep "yes$" /etc/ssh/sshd_config
```

### Wyjaśnienie:

- `yes` → szukany ciąg znaków
- `$` → koniec linii
- grep dopasowuje linie, w których **ostatnie znaki to `yes`**

Lub:

```bash
grep -Ei "yes$" nazwa_pliku
```

- `-i` → ignoruje wielkość liter