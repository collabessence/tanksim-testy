# TankIST — wersje testowe

**TankIST** (Tank Immersive Simulator Together) to kooperacyjna gra sieciowa: załoga czołgu (Tiger I kontra T-34-85) w pełnej obsadzie — kierowca, działonowy, dowódca, ładowniczy, radiooperator. To wczesna, testowa wersja: wiele rzeczy nie jest skończonych, a Twoje uwagi są po to, żeby to zmienić.

Aktualne wydania: zakładka **Releases** po prawej. Lista zmian: [WERSJE.md](WERSJE.md).

## Co jest w tej wersji
- Tiger I (nr 131) z modelem 1:1 i dwoma malowaniami (Tunezja 1943, Bovington 2017) wybieranymi w lobby.
- T-34-85 jeszcze bez docelowego modelu (zastępcza bryła).
- Tryby: PvP i trening, do 11 osób (host + 10 klientów), uzupełnianie załogi botem („Auto-załoga”).

## Wymagania
- 64-bitowy Linux lub Windows 10/11, karta z obsługą Vulkan (bez niej gra się nie uruchomi).
- ok. 1 GB wolnego miejsca (zip ma ~150 MB, po rozpakowaniu ~350 MB).
- Do gry z kimś: host musi być osiągalny po sieci (patrz niżej).

## Pobranie i uruchomienie
1. Wejdź w **Releases**, pobierz zip dla swojego systemu (`...-windows-x86_64.zip` albo `...-linux-x86_64.zip`).
2. (Opcjonalnie) sprawdź sumę: `SHA256SUMS.txt` z wydania; Linux: `sha256sum -c SHA256SUMS.txt`, Windows: `certutil -hashfile <plik.zip> SHA256`.
3. Rozpakuj.
   - **Windows:** uruchom `TankIST.exe`. SmartScreen może ostrzec o nieznanym wydawcy („Więcej informacji” → „Uruchom mimo to”) — to build bez podpisu cyfrowego.
   - **Linux:** `chmod +x TankIST.x86_64 && ./TankIST.x86_64`.

## Gra z drugą osobą
W lobby wpisz **Nazwę**, potem:
- **host:** kliknij **Hostuj** (domyślny port **7777**, protokół UDP). Przekaż znajomemu swój adres IP.
- **klient:** wpisz **Adres** hosta i port, kliknij **Dołącz**.

Następnie każdy wybiera czołg (A: Tiger I, B: T-34-85) i rolę, zaznacza **Gotowy**; host klika **Start**. Bez kompletu graczy zaznacz **Auto-załoga**.

### Połączenie przez internet
Najprościej bez ruszania routera: **Tailscale** lub **ZeroTier** (oboje instalują się i widzą w jednej wirtualnej sieci; wtedy adres hosta to jego adres z tej sieci). Alternatywa: przekierowanie portu **UDP 7777** na routerze hosta. W jednej sieci domowej wystarczy lokalny adres hosta (np. `192.168.x.x`). Zapora systemowa musi przepuszczać UDP 7777 dla TankIST.

### Z linii poleceń (opcjonalnie)
```
TankIST --host 7777            # uruchom jako host
TankIST --join 192.168.1.20:7777 --name Adam
TankIST --server               # serwer dedykowany bez okna gracza (ten sam plik)
```
Na Windowsie uruchamiaj z `cmd` lub PowerShella w katalogu z grą.

## Sterowanie (podstawy)
Kierowca: **W/S** gaz i wsteczny, **A/D** skręt, **Spacja** hamulec, **R/F** bieg w górę/w dół, **T** automat skrzyni, **I** silnik. **Tab** — menu miejsc (zmiana roli w trakcie), **Enter** — czat załogi. Działonowy i inni: myszą, klawisze **1/2/3** wybór amunicji u ładowniczego. Gdy coś jest niejasne — to też jest wartościowa uwaga dla nas.

## Zgłaszanie błędów
1. Wejdź w **Issues → New issue → Zgłoszenie błędu** i wypełnij formularz.
2. **Dołącz log.** Gra zapisuje go sama; zamknij grę i weź najnowszy plik z:
   - Linux: `~/.local/share/godot/app_userdata/TankIST/logs/`
   - Windows: `%APPDATA%\Godot\app_userdata\TankIST\logs\` (wklej tę ścieżkę w Eksploratorze plików)
   Plik `godot.log` to ostatnie uruchomienie. Przeciągnij go do zgłoszenia (lub wklej zawartość w bloku kodu).
3. **Dołącz zrzut ekranu** (Windows: Win+Shift+S; Linux: narzędzie systemowe). Przy błędach wizualnych zrzut jest ważniejszy niż opis.
4. Napisz, co robiłeś tuż przed błędem, czy byłeś hostem czy klientem i jaką miałeś rolę.

Pomysły i uwagi do rozgrywki zgłaszaj tym samym sposobem (szablon „Uwaga do rozgrywki”).
