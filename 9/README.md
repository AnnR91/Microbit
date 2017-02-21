#Gesty

Interesuj�cym efektem ubocznym posiadania akcelerometru jest detekcja gest�w.
Je�li b�dziesz rusza� swoj� p�ytk� BBC micro:bit w okre�lony spos�b,
MicroPython b�dzie je m�g� rozpoznawa�.

MicroPython jest zdolny do rozpoznawania nast�puj�cych gest�w: `up` (do g�ry),
`down` (do do�u), `left` (w lewo), `right` (w prawo), `face up` (wierzchem do g�ry),
`face down` (wierzchem do do�u), `freefall` (swobodny spadek), `3g`, `6g`, `8g`.
O ile wi�kszo�� nazw powinna by� oczywista, `3g`, `6g` i `8g` maj� miejsce gdy
urz�dzenie spotykaj� te poziomy przeci��enia (jak astronaute wysy�anego
w kosmos).

By odczyta� aktualny gest u�yj metody `accelerometer.current_gesture`. Jej
wynikiem b�dzie nazwa jednego z wy�ej wymienionych gest�w. Przyk�adowo, ten
program b�dzie czyni� twoj� p�ytk� szcz�liw� jedynie gdy zwr�cona b�dzie ona
wierzchem do g�ry.

```markdown
from microbit import *

while True:
    gesture = accelerometer.current_gesture()
    if gesture == "face up":
        display.show(Image.HAPPY)
    else:
        display.show(Image.ANGRY)
```

Ponownie, poniewa� chcemy by p�ytka reagowa�a na zmieniaj�ce si� okoliczno�ci
u�yjemy p�tli `while` W jej ciele odczytywany jest aktualny gest, po czym
przypisywany jest pod nazw� "gesture". Warunek `if` sprawdza czy `gesture`
to `face up` (Python u�ywa `==` do sprawdzenia zgodno�ci, a pojedy�czy znak
`=` u�yty jest do przypisywania - tak jak przypisali�my odczytany gest do
nazwy `gesture`). Je�li gest to `face up`, wtedy u�yj wy�wietlacza by pokaza�
u�miechni�t� buzi�. W przeciwnym wypadku urz�dzenie przybiera gro�ny wygl�d!


##Magiczna 8

Kula magiczna �semka to zabawka wynaleziona w latach 50tych XX wieku. Idea
polega na tym by zada� pytanie na kt�re mo�na odpowiedzie� tak/nie, potrz�sn��
ni� i poczeka� a� ujawni si� prawda. To raczej proste przekszta�ci� j�
w program:

```markdown
from microbit import *
import random

answers = [
    "To pewne",
    "Zdecydowanie tak",
    "Pewnie tak",
    "Tak, definitywnie",
    "Mozesz polega� na tym",
    "Tak, nawet to widze",
    "Chyba tak",
    "Perspektywy dobre",
    "TAK",
    "Objawy wskazuj� na tak",
    "Nie wiem, sprobuj ponownie",
    "Zapytaj potem",
    "Nie chce odpowiadac teraz",
    "Nie mozna przewidziec",
    "Skoncentruj si� i zapytaj raz jeszcze",
    "Nie licz na to"
    "Nie",
    "Moje dowody mowia nie",
    "Perspektywy kiepskie",
    "Watpliwe",
]

while True:
    display.show("8")
    if accelerometer.was_gesture("shake"):
        display.clear()
        sleep(1000)
        display.scroll(random.choice(answers))
		
```

Wi�kszo�� programu to lista nazwana "answers" (odpowiedzi). W�a�ciwa gra zawiera
si� w p�tli `while` na ko�cu.

Domy�lnym stanem gry jest pokazywanie cyfry `8`. Jednak�e program musi wykrywa�
�e urz�dzenie�dzenie jest potrz�sane. Metoda `was_gesture` u�ywa swojego
argumentu (w tym
wypadk napisu `shake` (potrz�sa�) poniewa� chcemy wykry� potrz�sanie) by zwr�ci�
`True`/`False` (prawda/fa�sz) w odpowiedzi. Je�li u��dzenie by�o potrz�sane,
warunkowy "if" wykona blok kodu kt�ry wyczy�ci ekran, poczeka sekund� (dzi�ki
czemu b�dzie wygl�da�o jakby u��dzenie my�la�o nad odpowiedzi� na twoje pytanie)
po czym wy�wietli przypadkowo wybran� (ang. `random choice`) odpowied�.

Dlaczego by nie zapyta� urz�dzenie czy to nie najwspanialszy program kiedykolwiek
napisany? Co mo�esz zrobi� by `oszukiwa�` i uzyskiwa� zawsze odpowied� pozytywn�
lub negatywn�? (Podpowied�: u�yj przycisk�w).