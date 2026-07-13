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

---

## 🐳 BLOK 10 & 11: ENGINE DEPLOYMENT & CONTAINER LIFECYCLE
> 💡 Docker pozwala na izolację aplikacji od systemu operacyjnego hosta za pomocą lekkich kontenerów.
* `sudo apt install docker.io -y` - Instalacja oficjalnego silnika Docker Engine w systemie Ubuntu Server.
* `sudo usermod -aG docker $USER` - Dodanie bieżącego użytkownika do grupy systemowej `docker` (nadanie uprawnień do zarządzania kontenerami bez użycia `sudo`).
* `newgrp docker` - Natychmiastowe odświeżenie grup systemowych w bieżącej sesji terminala (eliminuje błąd *Permission Denied*).
* `docker run -d -p 8080:80 --name ecommerce-landing-page nginx` - Pobranie obrazu Nginx i uruchomienie go w tle (`-d`) z mapowaniem portu zewnętrznego hosta `8080` na wewnętrzny port kontenera `80`.
* `docker ps` - Listowanie aktywnych kontenerów wraz z ich identyfikatorami PID/ID, portami i statusem.
* `docker logs [container_name]` - Ekstrakcja logów aplikacyjnych bezpośrednio ze strumienia kontenera (kluczowe do integracji z systemami monitoringu).
* `docker stop [container_name]` - Wysłanie sygnału SIGTERM do aplikacji wewnątrz kontenera i bezpieczne jej zatrzymanie.
* `docker rm [container_name]` - Całkowite usunięcie zasobów kontenera z dysku systemowego.