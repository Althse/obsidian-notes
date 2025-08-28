# Plan praktyczny – Tom 1 „Wprowadzenie do bezpieczeństwa IT” + Laby

**Cel:** Szybkie połączenie teorii z książki z praktyką w labach.  
**Czas:** ok. 3 godziny dziennie w tygodniu, weekendy więcej.  
**Priorytet:** Red Team / Pentesting.  
**Środowisko:** Hack The Box, TryHackMe, Kali Linux (VM), ewentualnie własne maszyny testowe.

---

## 1. Wstęp, etyka, modele zagrożeń
**Książka:** Wstęp + rozdział Gynvaela Coldwinda o etyce, rozdział o modelach zagrożeń.  
**Cele:**
- Poznać podstawowe pojęcia i zasady etyczne w security.
- Zrozumieć, czym jest modelowanie zagrożeń.

**Praktyka:**
- Stwórz model zagrożeń dla swojej domowej sieci.
- OSINT: Zbierz informacje o swojej sieci, usługach, domenach (legalnie).
- Narzędzia: Google Dorking, `whois`, `shodan` (wersja darmowa).

---

## 2. OSINT
**Książka:** Rozdział o OSINT.  
**Cele:**
- Umieć wyszukiwać informacje o celach ataku.
- Poznać podstawowe narzędzia OSINT.

**Praktyka:**
- TryHackMe: *OSINT Fundamentals*, *Mr. Robot OSINT*.
- Narzędzia: `theHarvester`, `Maltego`, Google Dorking.
- Własne zadanie: znajdź wszystkie publiczne informacje o swojej domenie/mailach.

---

## 3. Podstawy sieci i rekonesans
**Książka:** Rozdziały o TCP/IP, sieciach, narzędziach skanujących.  
**Cele:**
- Zrozumieć działanie sieci i protokołów.
- Umieć wykrywać hosty i usługi.

**Praktyka:**
- HackTheBox: *Nmap Starting Point*.
- Kali: `nmap` + `netdiscover` na lokalnej sieci.
- Zadanie: znaleźć wszystkie urządzenia w domowej sieci + ich porty.

---

## 4. Podstawy Linux/Windows w security
**Książka:** Rozdział o Linuksie dla pentestera, PowerShell w security.  
**Cele:**
- Opanować podstawowe komendy i administrację.
- Umieć wykonywać proste akcje w PowerShell i Bash.

**Praktyka:**
- TryHackMe: *Linux Fundamentals 1–3*.
- PowerShell: lista procesów, użytkowników, usług.
- Mini-scenariusz: przejmij pliki innego użytkownika w testowej VM.

---

## 5. Testy penetracyjne – metodologia
**Książka:** Rozdział o przebiegu pentestu.  
**Cele:**
- Zrozumieć pełny cykl pentestu.
- Umieć dokumentować wyniki.

**Praktyka:**
- TryHackMe: *Intro to Pentesting*.
- HackTheBox: proste maszyny z *Starting Point*.
- Utwórz raport pentestu na podstawie zrobionej maszyny.

---

## 6. Ataki na usługi i web
**Książka:** Rozdział o atakach na aplikacje webowe.  
**Cele:**
- Poznać OWASP Top 10.
- Umieć wykrywać i wykorzystywać luki webowe.

**Praktyka:**
- TryHackMe: *OWASP Top 10*, *Juice Shop*.
- Narzędzia: `burpsuite`, `sqlmap`.
- Zadanie: Znajdź i wykorzystaj SQL Injection lub XSS w testowym środowisku.

---

## 7. Hasła i ataki na uwierzytelnianie
**Książka:** Rozdział o łamaniu haseł.  
**Cele:**
- Zrozumieć metody uwierzytelniania i ataków.
- Umieć łamać hasła z hashów.

**Praktyka:**
- TryHackMe: *Password Attacks*.
- Kali: `hydra`, `john`, `hashcat` na własnych hashach.
- Zadanie: przeprowadzić brute force na własnym serwisie logowania.

---

## 8. Podstawy kryptografii
**Książka:** Rozdział o podstawach kryptografii.  
**Cele:**
- Zrozumieć różnice między szyfrowaniem symetrycznym i asymetrycznym.
- Umieć szyfrować i deszyfrować dane.

**Praktyka:**
- TryHackMe: *Crypto 101*.
- Własne ćwiczenie: zaszyfruj i odszyfruj plik kluczem symetrycznym i asymetrycznym (np. `openssl`).

---

## 9. ICS/OT, bezpieczeństwo aplikacji mobilnych (opcjonalnie)
**Książka:** Rozdziały o ICS/OT, bezpieczeństwie mobilnym.  
**Cele:**
- Poznać specyfikę ICS/OT.
- Zrozumieć podstawy testowania aplikacji mobilnych.

**Praktyka:**
- Mobile: *DIVA Android App* w emulatorze.
- ICS: tylko teoria (brak łatwego legalnego środowiska).

---

## 10. Podsumowanie i utrwalenie
**Książka:** Powtórka z notatek, wybrane rozdziały do pogłębienia.  
**Cele:**
- Utrwalić wiedzę.
- Zrobić kilka scenariuszy od A do Z.

**Praktyka:**
- HackTheBox: 2–3 maszyny różnej trudności.
- TryHackMe: ścieżka *Jr Penetration Tester*.
- Aktualizacja portfolio (screeny, raporty, write-upy).

---

# Efekt po ukończeniu planu
- Masz ogarniętą mapę całego bezpieczeństwa IT.
- Umiesz korzystać z podstawowych narzędzi pentestera.
- Potrafisz udokumentować wyniki pracy.
- Wiesz, w czym chcesz się specjalizować.

---

# Kolejny krok po tym planie
1. Przejście trudniejszych maszyn HTB i THM.
2. Nauka Active Directory, zaawansowane exploity.
3. Budowa portfolio z write-upów i projektów.
4. Pierwsze aplikacje na Junior SOC / Junior Pentester.

# Tom 1 „Wprowadzenie do bezpieczeństwa IT” – Praktyczny przewodnik

**Cel:** Połączenie teorii z książki z praktyką w labach, aby szybko zdobyć umiejętności pentestera/red teamera.  
**Czas:** ~3 godziny dziennie w tygodniu, więcej w weekendy.  
**Środowisko:** Hack The Box, TryHackMe, Kali Linux VM, własne maszyny testowe.

| Rozdział | Przykłady praktyk | Narzędzia / Lab |
|----------|-----------------|----------------|
| **1. Wstęp, etyka, modele zagrożeń** | - Stwórz model zagrożeń dla swojej domowej sieci (router, PC, NAS, smart home).<br>- Symulacja ataku „papierowego”: jak ktoś mógłby uzyskać dostęp do Twojej sieci i jak się obronić.<br>- Mini-OSINT własnej sieci / domeny. | - Diagramy w draw.io / Lucidchart<br>- Google Dorking<br>- whois, shodan (darmowa wersja) |
| **2. OSINT** | - TryHackMe: *OSINT Fundamentals*.<br>- Mr. Robot OSINT.<br>- TheHarvester do zbierania maili i domen.<br>- Maltego (wersja Community) do wizualizacji powiązań.<br>- Własny mini-report z publicznych informacji o domenie/testowym serwerze. | - TryHackMe, TheHarvester, Maltego, Google Dorks |
| **3. Podstawy sieci i rekonesans** | - Nmap skan hostów i portów w LAN (`nmap -sC -sV <IP>`).<br>- `netdiscover` lub `arp-scan` – wykrywanie urządzeń.<br>- HackTheBox: *Nmap Starting Point*.<br>- Tworzenie listy otwartych portów, wersji usług i OS.<br>- Analiza protokołów TCP/UDP w ruchu sieciowym. | - Nmap, Netdiscover, arp-scan, Wireshark, HTB Starting Point |
| **4. Linux / Windows w security** | - TryHackMe: *Linux Fundamentals 1–3*.<br>- Bash: listowanie plików, procesów, uprawnień.<br>- PowerShell: `Get-Process`, `Get-Service`, `Get-LocalUser`.<br>- Mini-scenariusz: dostęp do plików innego użytkownika w VM.<br>- Pisanie prostych skryptów automatyzujących zadania. | - Kali Linux, TryHackMe, PowerShell, VM Windows |
| **5. Testy penetracyjne – metodologia** | - TryHackMe: *Intro to Pentesting*.<br>- HTB Starting Point: pełny cykl pentestu (rekonesans → exploit → eskalacja → raport).<br>- Tworzenie pierwszego prostego raportu z pentestu.<br>- Praktyczne planowanie ataku: cele, narzędzia, etapy. | - TryHackMe, HTB, Notatki/Word |
| **6. Ataki na web** | - TryHackMe: *OWASP Top 10*, *Juice Shop*.<br>- Burp Suite: przechwytywanie i manipulacja ruchu HTTP.<br>- SQLi / XSS w DVWA / Juice Shop.<br>- Testowanie formularzy logowania i uploadu plików.<br>- Analiza ciasteczek, sesji, nagłówków HTTP. | - Burp Suite, DVWA, Juice Shop, TryHackMe OWASP Labs |
| **7. Hasła i uwierzytelnianie** | - Kali: `hydra` – brute force na własnym serwisie testowym.<br>- `john` i `hashcat` – łamanie hashów lokalnych plików.<br>- TryHackMe: *Password Attacks*.<br>- Symulacja ataku słownikowego i brute force.<br>- Analiza polityki haseł (siła, złożoność). | - Hydra, John the Ripper, Hashcat, TryHackMe Password Attacks |
| **8. Kryptografia** | - TryHackMe: *Crypto 101*.<br>- Szyfrowanie plików symetrycznie: `openssl enc -aes-256-cbc -in secret.txt -out secret.enc`.<br>- Szyfrowanie asymetryczne: generowanie kluczy RSA, szyfrowanie/odszyfrowanie wiadomości.<br>- Podstawowe łamanie szyfrów prostych (Cezar, Vigenère).<br>- Analiza bezpieczeństwa różnych algorytmów. | - OpenSSL, TryHackMe Crypto 101, Python (pycryptodome) |
| **9. ICS/OT i bezpieczeństwo mobilne** | - Mobile: DIVA Android App w emulatorze – analiza aplikacji, logi, reverse engineering.<br>- ICS: symulatory online, analiza protokołów ICS (Modbus, OPC-UA).<br>- Analiza konfiguracji urządzeń IoT w domu. | - DIVA Android, CODESYS Web, Wireshark (protok. ICS) |
| **10. Podsumowanie i utrwalenie** | - HackTheBox: 2–3 maszyny różnej trudności.<br>- TryHackMe: *Jr Pentester* lub AttackBox.<br>- Tworzenie portfolio write-upów z labów: screenshoty, opis kroków, wnioski.<br>- Powtórka wszystkich narzędzi i metod. | - HTB, THM, Notatki, Word/Markdown, screenshoty |

---

### 💡 Wskazówki
- Każdy rozdział przerabiaj **czytając teorię, a następnie od razu praktykując**.  
- Notuj **skróty komend, wyniki labów, wnioski** – będą później częścią portfolio.  
- Niektóre rozdziały można łączyć w jeden dzień (np. OSINT + rekonesans sieci).  
- Portfolio z write-upów i notatek będzie Twoim **dowodem praktyki na CV**.  
- Laby w THM i HTB są legalne i bezpieczne – zawsze używaj własnych środowisk do testów.  
