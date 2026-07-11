# 🚀 KROK 1: MIESIĄC LINUXA DLA ADMINA WINDOWSA

Notatki i cheat-sheet z laboratoriów inżynieryjnych. Wszystkie komendy przetestowane i wdrożone w środowisku VS Code + UTM.

---

## 🕵️‍♂️ BLOK 1: DETEKTYWISTYKA SYSTEMOWA (ZWIAD)
* `whoami` - Sprawdza aktualny kontekst bezpieczeństwa (użytkownika). Zawsze weryfikuj, czy nie stoisz na `root`.
* `pwd` - Print Working Directory. Pokazuje pełną ścieżkę katalogu, w którym się znajdujesz.
* `uname -a` - Wypluwa architekturę procesora (np. aarch64/arm64) oraz wersję kernela Linuxa.
* `free -m` - Odpowiednik zakładki Wydajność w Menedżerze Zadań Windows. Pokazuje RAM w MB.
* `df -h` - Odpowiednik zarządzania dyskami. Pokazuje zużycie dysków w czytelnej formie (GB). Szukaj `/`.

---

## 📝 BLOK 2: MANIPULACJA PLIKAMI I POTOKAMI
* `mkdir -p folder/podfolder && cd folder/podfolder` - Tworzy strukturę katalogów i od razu do niej wchodzi.
* `echo "tekst" > plik.txt` - Tworzy plik i wpisuje do niego zawartość (nadpisuje stary plik).
* `echo "tekst" >> plik.txt` - Dopisuje tekst na sam koniec istniejącego pliku.
* `cat plik.txt` - Wyświetla zawartość pliku tekstowego bezpośrednio w terminalu.
* `grep "fraza" plik.txt` - Przeszukuje plik i wyciąga linie zawierające frazę. Przydatne do filtrowania logów pod kątem `ERROR`.

---

## 🔒 BLOK 3: UPRAWNIENIA CHMOD (BEZPIECZEŃSTWO)
> 💡 Uprawnienia to sumy cyfr dla: Właściciela | Grupy | Świata. (4 = Read, 2 = Write, 1 = Execute).
* `ls -l plik.txt` - Wyświetla szczegółowe uprawnienia pliku (np. `-rw-r--r--`).
* `chmod 600 plik.txt` - Daje odczyt i zapis TYLKO właścicielowi. Blokuje grupę i świat (kluczowe dla kluczy `.pem` w AWS).
* `chmod +x skrypt.sh` - Nadaje plikowi flagę wykonywalności (Execute). Pozwala odpalić skrypt przez `./skrypt.sh`.

---

## 🛠️ BLOK 4: DIAGNOSTYKA SIECI I USŁUGI
* `sudo apt update && sudo apt install pakiet -y` - Odpowiednik Windows Update / instalacji MSI. Pobiera programy z repozytorium.
* `htop` - Interaktywny menedżer zadań. Wyjście klawiszem `q`.
* `sudo ss -tulpn` - Nowoczesny zamiennik `netstat`. Pokazuje porty TCP/UDP, które aktualnie słuchają, oraz ich PID.
* `sudo systemctl status usługa` - Odpowiednik `Get-Service`. Pokazuje czy usługa (np. `ssh`, `nginx`) działa (zielone `active`).
* `sudo systemctl disable usługa` - Wyłącza automatyczny start usługi przy boocie systemu.

---

## 🪵 BLOK 5 & 6: MONITORING I PROCESY (3. LINIA WSPARCIA)
* `cd /var/log && ls -la` - Główne archiwum logów systemowych (odpowiednik Windows Event Viewer).
* `sudo tail -f /var/log/nginx/access.log` - Strumieniuje logi w czasie rzeczywistym. Widzisz każdy ruch na serwerze na żywo. Wyjście: `Ctrl + C`.
* `ps aux | grep nazwa` - Pokazuje procesy systemowe przefiltrowane po nazwie wraz z ich numerami PID.
* `sudo kill -9 PID` - Bezwzględne ubicie procesu przez jądro systemu (odpowiednik End Task).

---

## 🔑 BLOK 9: MOSTEK DO CHMURY (GIT + GITHUB SSH)
> 💡 Klucze SSH pozwalają na bezpieczną komunikację z GitHubem/AWS bez ciągłego wpisywania haseł.
* `ssh-keygen -t ed25519 -C "Krzysztof.jankowski94@gmail.com"` - Generuje nową, bezpieczną parę kluczy kryptograficznych (publiczny i prywatny).
* `code ~/.ssh/id_ed25519.pub` - Otwiera plik z kluczem publicznym bezpośrednio w edytorze VS Code, umożliwiając bezpieczne skopiowanie czystego tekstu do schowka.
* `ssh -T git@github.com` - Testuje i weryfikuje połączenie SSH z GitHubem. Prawidłowy wynik to: *Hi! You've successfully authenticated...*
* `git branch -M main` - Ustala nazwę głównej gałęzi kodu jako `main` (standard branżowy).
* `git remote add origin git@github.com:LOGIN/REPO.git` - Podpina lokalny folder pod zdalne repozytorium w chmurze GitHuba.
* `git push -u origin main` - Wypycha (wysyła) wszystkie lokalne zapisy (commity) bezpośrednio do chmury GitHuba.