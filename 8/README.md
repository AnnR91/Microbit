# Muzyka 

MicroPython na p�ytce BBC micro:bit przychodzi z pot�nym modu�em
muzyczno-d�wi�kowym.
Umo�liwia on w bardzo prosty spos�b generowanie pisk�w i brzd�k�w z
u��dzenia, je�li pod��czy
si� pod nie g�o�nik. U�yj krokodylk�w by podpi�� piny 0 i GND do wej�� g�o�nika.
Nie ma znaczenia kierunek w kt�rym s� one pod��czone pod g�o�nik.

Uwaga: Nie pr�buj tego z piezo elektrycznym brz�czykiem - takie
brz�czyki s� przystosowane
do grania jedynie pojedy�czego tonu.

Przyst�pmy zatem do grania jakiej� muzyki:
...

Zauwa�, �e zaimportowali�my modu� "music". Zawiera on metody u�yte do
wytworzenia i kontrolowania d�wi�ku.

MikroPython ma ca�kiem sporo wbudowanych melodii. Ich kompletna lista to:
...

Teraz ponownie we� przyk�adowy kod i zmie� w nim melodi�. Kt�ra z nich
jest twoj� ulubion�?
W jaki spos�b u�y� by� takich melodyjek by co� zasygnalizowa� b�d� wskaza�?


Wolfgang Amadeusz Microbit

Tworzenie w�asnych melodyjek jest proste!

Ka�da nuta ma swoj� nazw� (jak C#, czy F), oktaw� (m�wi�c� MicroPythonowi jak
wysoko lub nisko powinien zagra� t� nut�) i okres trwania (jak d�ugo powinna
ona wybrzmiewa�). Oktawy oznaczone s� liczbami - 0 jest najni�sz� oktaw�,
zawiera �rodkowe C, a 8 jest najwy�sz� jak� b�dziesz kiedykolwiek potrzebowa�,
chyba �e tworzysz muzyk� dla ps�w. Okres trwania r�wnie� wyra�ony jest liczbami.
Im wi�ksza warto��, tym d�u�ej b�dzie on trwa�. Warto�ci te odnosz�
si� do siebie,
dla przyk�adu okres trwania o warto�ci 4 b�dzie trwa� dwa razy d�u�ej ni� okres
o warto�ci 2 (i tak dalej...).
Je�li u�yjesz nuty nazwanej "R", MicroPython przeczeka (tj. zamilknie) na zadany
okres trwania.

Ka�da nuta wyra�ona jest jako ci�g znak�w jak ten:

NUTA[oktawa][:okres trwania]

Dla przyk�adu "A1:4" odnosi si� do nuty nazwanej A w oktawie o numerze 1, granej
przez czas o d�ugo�ci 4 jednostek.

Zr�b list� nut by zapisa� melodi� (jest to odpowiednikiem tworzenia animacji
z listy obrazk�w). Przyk�adowo, w ten spos�b MicroPython mo�e zagra�
otwarcie "Frere Jaques":
...

Uwaga: MicroPython umo�liwia uproszczenie takich melodii. Zapami�ta on oktaw�
i okres trwania do p�ki go nie zmienisz nast�pnym razem. W wyniku powy�szy
przyk�ad mo�e by� przepisany tak:
...
Zauwa� jak zmieniaj� si� warto�ci oktaw i okres�w trwania jedynie gdy musz�.
Zaoszcz�dza to sporo pisania jak i u�atwia czytanie.


Efekty d�wi�kowe

MicroPython pozwala Ci wytwa�a� tony kt�ry nie s� muzycznymi nutami.
Dla przyk�adu,
w ten spos�b mo�esz wytworzy� sygna� policyjnej syreny:
...

Zauwa� jak w tym przyk�adzie u�yta jest metoda "music.pitch". Oczekuje
ona cz�stotliwo�ci.
Dla przyk�adu, cz�stotliwo�� 440 jest takasama jak koncertowy ton A,
u�ywany do "zgrania si�"
przez orkiestr� filharmonii.

W powy�szym przyk�adzie funkcja "range" u�yta jest do wygenerowania przedzia�u
warto�ci liczbowych. Te liczby u�yte s� do zdefiniowania wysoko�ci
tonu. Trzy argumenty
funkcji "range" s�: warto�ci� pocz�tkow�, ko�cow� i warto�ci� kroku. W
zwi�zku z tym
pierwsze u�ycie "range" m�wi, w j�zyku polskim: utw� przedzia�
warto�ci pomi�dzy 880 a 1760,
dodaj�c co krok 16. Trugie u�ycie "range" m�wi: utw� przedzia�
warto�ci pomi�dzy 1760 i 880,
dodaj�c co krok -16 (czyli odejmuj�c 16). W ten spos�b otrzymujemy
przedzia� cz�stotliwo�ci
zmieniaj�c wysoko�� tonu tak jak syrena.

Jako �e syrena powinna trwa� bez ko�ca otacza j� niesko�czona p�tla "while".

Najwa�niejsze w tym jest wprowadzenie nowego typu p�tli wewn�trz p�tli
"while" - p�tla "for".
Po polsku powiedzieliby�my "dla ka�dego elementu w pewnej kolekcji,
wykonaj z ni� pewne dzia�anie".
Po angielsku (na kt�rym bazuje j�zyk Python) brzmi to "for each item
in some collection, do some
activity with it". St�d mamy "for", "in". W naszym przyk�adzie to "dla
ka�dej cz�stotliwo�ci (freq)
w przedziale (range) graj dzi�k o tej cz�stotliwo�ci przez 6 milisekund".
Zauwa� �e ka�da akcja do wykonania w p�tli "for" ma wci�cie (zgodnie z
tym o czym rozmawiali�my
wcze�niej) dzi�ki czemu Python wie dok�adnie jaki kod wykona� dla
poszczeg�lnych element�w kolekcji.