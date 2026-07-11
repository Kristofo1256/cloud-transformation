Komenda 1: whoami
Co robi: Pokazuje Twój aktualny kontekst bezpieczeństwa. Zobaczysz krzysztof. W chmurze zawsze upewniasz się, czy nie działasz z konta administratora (root), co jest błędem w sztuce.
Komenda 2: pwd
Co robi: Print Working Directory – pokazuje dokładnie, w którym miejscu drzewa katalogów się znajdujesz.
Komenda 3: uname -a
Co robi: Wypluwa architekturę procesora i wersję jądra Linuxa. Zobaczysz tam flagę aarch64 lub arm64, co potwierdza, że Ubuntu idealnie gada z procesorem Twojego Maka.
Komenda 4: free -m
Co robi: Pokazuje zużycie pamięci RAM w megabajtach (-m). Zobaczenie kolumn total, used i free to odpowiednik zakładki "Wydajność" z Menedżera Zadań Windows.
Komenda 5: df -h
Co robi: Pokazuje stan dysków w czytelnej formie (w GB, a nie bajtach – flaga -h). Szukasz wiersza z samym ukośnikiem / w kolumnie Mounted on. To Twój główny dysk (odpowiednik dysku C:).

ip a ->> sprawdza adres IP


Komenda 1: echo "Serwer produkcyjny Windows przestał mi wystarczać" > motywacja.txt
Co robi: Operator > przekierowuje tekst i tworzy nowy plik motywacja.txt.
Komenda 2: echo "Dlatego wchodzę w Cloud i zgarniam stawki w EUR!" >> motywacja.txt
Co robi: Operator >> (podwójny) dopisuje tekst na końcu pliku, nie niszcząc poprzedniej zawartości.
Komenda 3: cat motywacja.txt
Co robi: Wyświetla zawartość pliku bezpośrednio pod komendą w terminalu.
Komenda 4: grep "EUR" motywacja.txt
Co robi: Przeszukuje plik i wyciąga tylko linie zawierające słowo "EUR". Za chwilę będziesz tym filtrował logi systemowe o rozmiarze 5 GB w poszukiwaniu słowa ERROR.

Komenda 6: chmod +x skrypt.sh
Co robi: Dodaje flagę wykonywalności (+x) do skryptu.


Komenda 4: echo -e "#!/bin/bash\necho 'Automatyzacja DevOps odpala sie...'" > skrypt.sh
Co robi: Tworzy prosty plik, który jest skryptem powłoki (odpowiednik pliku .ps1 lub .bat).

Komenda 2: htop
Co robi: Odpala genialny, interaktywny menedżer zadań w terminalu. Widzisz zużycie rdzeni procesora, pamięć RAM i procesy. Wyjdź z niego, wciskając klawisz q.

Bash
sudo ss -tulpn
Szybki cheat-sheet, co oznaczają te flagi (warto wpisać do NOTATKI.md):
-t – pokrój tylko połączenia TCP (odpowiednik Twoich Windowsowych nasłuchiwań HTTP/SQL)  
PDF
-u – pokrój połączenia UDP (np. DNS)
-l – filtruj tylko porty, które aktualnie słuchają (listening)
-p – pokaż proces/program (PID), który ten port zajął (wymaga sudo)
-n – pokazuj porty jako liczby (np. 22), a nie nazwy usług (np. ssh)
Wbijaj sudo ss -tulpn. Powinieneś zobaczyć tabelę, a w niej m.in. linię z portem *:22 i procesem sshd.


instalacja nginx:

sudo apt install nginx -y

check czy nginx dziala:

sudo systemctl status nginx

Bash
cd /var/log && ls -la
Co robi: Przechodzi do centralnego repozytorium logów systemowych i listuje pliki. Zobaczysz tu pliki takie jak syslog (logi ogólne), auth.log (logi logowania/SSH) oraz katalog nginx (logi Twojego serwera WWW).

