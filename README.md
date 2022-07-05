# intouch_scada_hmi
Wonderware InTouch SCADA project
(some graphic files can be missing)

### Sterowanie systemem czterech taśmociągów
1. Skrypty aplikacyjne
Application Script, While Running, Every 1 Msc

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/first.png" width=80% height=80%>

Ruch taśmociągów warunkowany jest włączonym zasilaniem oraz obecnością krowy na taśmie.
Gdy ustawiony jest tryb automatyczny, taśmociąg jest aktywowany i dezaktywowany w zależności od tego, czy krowa się na nim znajduje.
W przypadku wybrania trybu manualnego, natychmiastowo wyłączane są wszystkie działające taśmociągi. Ich ruch teraz zależny jest od ustawienia trójstanowych przełączników. Za ich pomocą można wtedy kontrolować również kierunek działania taśmociągu.
W danej chwili na trasie może znajdować się tylko jedna krowa. Gdy dojedzie do końca, pojawia się możliwość postawienia nowej na początku i licznik martwych krów inkrementuje się o jeden.
Całość można wyłączyć za pomocą głównego wyłącznika awaryjnego. Po jego naciśnięciu następuje rozłączenie zasilania w układzie.

2. Instrukcja użytkowania

- Główny widok:

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/second.png" width=80% height=80%>

Na powyższym zdjęciu zaprezentowany jest główny widok wizualizacji linii produkcyjnej. Są to cztery taśmociągi w szeregu, które działają w dwóch trybach: automatycznym oraz manualnym. Zadania jakie można wykonywać, uwarunkowane są poziomem dostępu kont użytkowników.

- Ekran logowania:

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/third.png" width=60% height=60%>

Na tym ekranie można zalogować się na konta użytkownika definiujące dostęp do niektórych funkcji programu. Przycisk  „Nazwisko operatora” służy do wpisania loginu, a przycisk „Hasło” hasła. Można natychmiast się wylogować przy pomocy kolejnego przycisku, ale po 40 sekundach braku aktywności system automatycznie wyloguje użytkownika (po 20 sekundach braku aktywności zapali się lampka ostrzegająca). Przycisk „OK” zamyka okno logowania. Zdefiniowani zostali 2 użytkownicy o 2 różnych poziomach dostępu:
- Pan Kierownik (hasło 1234, poziom dostępu 9001)
- Pan Arek (hasło 12, poziom dostępu 5000)

- Ekran alarmów:

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/fourth.png" width=80% height=80%>

Alarmy pozwalają na wgląd w zmienne programowe. Predefiniowane alarmy w tym programie informują o tym, na którym taśmociągu znajduje się aktualnie krowa, jak daleko już zajechała oraz o liczbie spalonych krów.

- Sygnalizacja oraz manualne sterowanie

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/fifth.png" width=70% height=70%>  

Wszystkie taśmociągi posiadają 3 lampki sygnalizujące ich aktualny stan. Zapalenie się koloru pomarańczowego oznacza włączone zasilanie oraz gotowość do działania. Kolor zielony oznacza, że taśmociąg porusza się do przodu, a kolor czerwony oznacza poruszanie się w kierunku przeciwnym. Kiedy załączony jest tryb sterowania manualnego pojawiają się trójstanowe przełączniki za pomocą, których można osobno aktywować ruch każdego taśmociągu. Do przełączników wymagany jest minimalny dostęp 4999.

- Detekcja obiektu

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/sixth.png" width=65% height=65%>

W trybie automatycznym, taśmociąg zostaje aktywowany w momencie kiedy krowa znajdzie się pod czujnikiem.
W trybie ręcznym, podświetlenie czujnika informuje użytkownika o przejechaniu obiektu na następną taśmę.

- Panel sterowania systemem

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/seventh.png" width=80% height=80%>

Od lewej:
- Czerwony przycisk umożliwiający awaryjne rozłączenie zasilania w układzie. Jest dostępny dla każdego użytkownika
- Dwupołożeniowy przełącznik na klucz pozwalający na włączenie zasilania. O włączeniu prądu informuje świecąca lampka. Aby go zobaczyć trzeba zalogować się przynajmniej na konto „Pana Arka”
- Dwupołożeniowy przełącznik do wyboru trybu automatycznego lub manualnego. Tym elementem może sterować jedynie „Pan Kierownik”
- Wyświetlacz informujący użytkownika o aktualnym postępie obiektu na linii produkcyjnej. Widzi go każdy użytkownik.
- Wyświetlacz zliczający obiekty, które dotarły od końca produkcji. Także widzi go każdy użytkownik.
- Przycisk “Reset” pozwalający na zresetowania licznika obsłużonych krów. Dostępny jest jedynie dla  „Pana Kierownik”
- Wyświetlacz pełniący funkcję zegara
- Przycisk “Alarms” pozwala na wyświetlenie tabeli z alarmami
- Przycisk “Log in” otwiera okno logowania
(ostatnie trzy elementy widoczne są dla każdego użytkownika)

- Panel dodawania obiektów

<img src="https://github.com/cezarywawrzyniak/intouch_scada_hmi/blob/main/screenshots/eight.png" width=50% height=50%>

Nad naczepą ciężarówki wskazującą punkt wejściowy nowych obiektów znajdują się 2 przyciski. Przycisk znajdujący się po prawej można aktywować manualnie kiedy taśmociągi są puste i po naciśnięciu go na pierwszy taśmociąg zostanie dodana jedna krowa. Przycisk po lewej spełnia podobną funkcję, ale jest bistabilny. Oznacza to, że po jego aktywacji nowe krowy będą dodawane automatycznie kiedy poprzednie zjadą z ostatniego taśmociągu. Przycisk po prawej dostępny jest dla „Pana Arka”, a do przycisku bistabilnego dostęp ma jedynie „Pan Kierownik”.
