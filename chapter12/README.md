# Radio

Wewn�trz ka�dego Micro:bita znajduje si� bardzo przydatna funkcjonalno�ci, a mianowicie Radio. Dzi�ki tej funkcjonalno�ci mo�emy przesy�a� i odbiera� wiadomo�ci.
W ka�dym Micro:bicie znajduje si� ciekawa oraz przydatna funkcjonalno��, a mianowicie `Radio`. Modu� radio pozwala nam
na przesy�anie oraz odbieranie wiadomo�ci.

Po pierwsze musimy zaimportowa� modu� radia `import radio`, aby udost�pni� funkcje naszemu programowi. Nast�pnie musimy uruchomi� radio, za pomoc� `radio.on()`.

W tym momencie modu� radiowy jest skonfigurowany do rozs�dnych warto�� domy�lnych, sprawiaj� one �e jest kompatybilny z innymi platformami, kt�re s� zgodne z BBC micro:bit.
Mo�liwe jest sterowanie z om�wionymi powy�ej funkcjami, jak r�wnie� ilo�� wykorzystywana transmijsi wiadomo�ci i ilo�ci pami�ci RAM. Zak�adaj�c, �e jeste�my zadowoleni z ustawie�
domy�lnych, najprostszy spos�b wysy�ania wiadomo�ci jest nast�puj�cy:

`radio.send("wiadomo��")`

W przyk�adzie u�yli�my funkcji wysy�ania, aby po prostu nada� ci�g znak�w "wiadomo��". Otrzymywanie wiadomo�ci jest jeszcze prostsze:

```markdown
new_message = radio.receive()
```

Po otrzymaniu wiadomo�ci s� one umieszczane w kolejce wiadomo�ci. Funkcja `receive` (odbierania) zwraca najstarsz� wiadomo�� z kolejki jako ci�g znak�w, co umo�liwia utworzenie nowej wiadomo�ci przychodz�cej. Je�li wype�ni si� kolejka komunikat�w, nowe przychodz�ce wiadomo�ci s� ignorowane.

Posiadaj�c tak� wiedz�, mo�emy stworzy� sw�j pierwszy projekt:

```markdown
from microbit import display, button_a, Image
import radio
radio.on()
while True:
    message = radio.receive()
    if message:
        display.show(Image.DUCK)
    if button_a.was_pressed():
        display.clear()
        radio.send("hello")

```

Kluczowa cz�� zawiera si� w p�tli zdarze�. Po pierwsze, sprawdza ona czy przycisk A zosta� wci�ni�ty, i je�li tak - u�ywa radia by by wys�a� wiadomo�� "hello" (ang. cze��). Nast�pnie czyta wszelkie wiadomo�ci z kolejki wiadomo�ci z u�yciem radio.receive(). Po czym u�ywa display.show() by pokaza� obrazek kaczki.

## �wiczenie

Dobieramy si� w dwu osobowe zespo�y. Staramy si� prze�wiczy� w parach dzia�anie powy�szego przyk�adu. Po prze�wiczeniu, zadaniem Waszym jest
na podstawie przyk�adu stworzy� w�asny program. Program musi dzia�a�, zgodnie z poni�szymi instrukcjami:

* Zaimportowa� modu� radio
* W��czy� radio
* Wysy�a� albo otrzymywa� wiadomo�ci
* Wy�wietli� animacje
