#Funkcje i modu�y

Zastan�w si�, ile rzeczy wyrzucasz ka�dego dnia: butelki po wodzie, torebki po chipsach, pude�ka po lodach, gazety itd. A teraz wyobra� sobie, co by si� sta�o, gdyby wszystkie te �mieci l�dowa�y
po prostu na stosie na podje�dzie do Twojego domu, bez segregowania papieru, plastiku i aluminiowych puszek.

Jestem pewna, �e w miare mo�liwo�ci segregujesz odpady i to si� chwali, poniewa� nikt nie lubi w drodze do szko�y przedzierad� si� przez g�r� �mieci. Znacznie lepiej jest, je�li te wszystkie
niepotrzebne, szklane pojemniki zostan� przetopione na nowe s�oiki czy butelki, je�li makulatora zostanie przemielona na papier makulatorowy, a plastik na przerobiony na inne wyroby plastikowe.

W ten spos�b ponownie wykorzystujemy r�ne rzeczy, kt�re w przeciwnym razie l�dowa�yby na coraz wy�szym poziomie �mieci. W �wiecie programowania zada powt�rnego wykorzystywania jest r�wnie wa�na. 
Oczywi�cie programy nie znikaj� pod g�r� �mieci, ale je�li nie b�dziemy w jakim� stopniu wielokrotnie wykorzystywa� tego, co ju� mamy, to od ci�g�ego 
przepisywania kodu zatrzemy sobie palce. Powt�rne wykorzystanie kodu to r�wnie� kr�tsze i �atwiejsze do czytania programy. Je�li si� wkr�tce przekonasz w Pythonie jest kilka sposob�w tworzenia kodu 
wielokrotnego u�ytku.

##U�ywanie funkcji

Jeden ze sposob�w na wielokrone u�ywanie kody Pythona ju� znamy. W poprzednim rozdziale u�yli�my funkcji `range` i `list`, aby nakaza� Pythonowi liczenie:

```markdown
>>> list(range(0,5))
[0, 1, 2, 3, 4]
>>>
```

Ka�dy, kto potrafi liczy�, poradzi sobie z napisaniem listy zawieraj�cej kolejne liczby, po prostu je wypisuj�c, ale im d�u�sza lista, tym wi�cej pisaniny. Dzi�ki funkcjom utworzenie 
lisy zawieraj�cej tysi�ce pozycji nie jest niczym trudnym. 
Poni�ej generujemy list� liczb za pomoc� funkcji `list` i `range`:

```markdown
>>> list(range(0,1000))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 3
7, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105,
 142, 143, 144, 145, 146, 147, 148, 149, 150, 151, 152, 153, 154, 155, 156, 157, 158, 159, 160, 161, 162, 163, 164, 165,
 202, 203, 204, 205, 206, 207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218, 219, 220, 221, 222, 223, 224, 225,
 262, 263, 264, 265, 266, 267, 268, 269, 270, 271, 272, 273, 274, 275, 276, 277, 278, 279, 280, 281, 282, 283, 284, 285,
 322, 323, 324, 325, 326, 327, 328, 329, 330, 331, 332, 333, 334, 335, 336, 337, 338, 339, 340, 341, 342, 343, 344, 345,
 382, 383, 384, 385, 386, 387, 388, 389, 390, 391, 392, 393, 394, 395, 396, 397, 398, 399, 400, 401, 402, 403, 404, 405,
 442, 443, 444, 445, 446, 447, 448, 449, 450, 451, 452, 453, 454, 455, 456, 457, 458, 459, 460, 461, 462, 463, 464, 465,
 502, 503, 504, 505, 506, 507, 508, 509, 510, 511, 512, 513, 514, 515, 516, 517, 518, 519, 520, 521, 522, 523, 524, 525,
 562, 563, 564, 565, 566, 567, 568, 569, 570, 571, 572, 573, 574, 575, 576, 577, 578, 579, 580, 581, 582, 583, 584, 585,
 622, 623, 624, 625, 626, 627, 628, 629, 630, 631, 632, 633, 634, 635, 636, 637, 638, 639, 640, 641, 642, 643, 644, 645,
 682, 683, 684, 685, 686, 687, 688, 689, 690, 691, 692, 693, 694, 695, 696, 697, 698, 699, 700, 701, 702, 703, 704, 705,
 742, 743, 744, 745, 746, 747, 748, 749, 750, 751, 752, 753, 754, 755, 756, 757, 758, 759, 760, 761, 762, 763, 764, 765,
 802, 803, 804, 805, 806, 807, 808, 809, 810, 811, 812, 813, 814, 815, 816, 817, 818, 819, 820, 821, 822, 823, 824, 825,
 862, 863, 864, 865, 866, 867, 868, 869, 870, 871, 872, 873, 874, 875, 876, 877, 878, 879, 880, 881, 882, 883, 884, 885,
 922, 923, 924, 925, 926, 927, 928, 929, 930, 931, 932, 933, 934, 935, 936, 937, 938, 939, 940, 941, 942, 943, 944, 945,
 982, 983, 984, 985, 986, 987, 988, 989, 990, 991, 992, 993, 994, 995, 996, 997, 998, 999]
>>>
```

Funkcje to fragmenty kodu, kt�re nakazuj� Pythonowi wykona� jakie� zadanie. Jest to jeden ze sposob�w na wielokrotne wykorzystywanie kodu - funkcji mo�na wielkrotnie u�ywa� w r�nych programach.
Przydatno�� funkcji wida� ju� przy pisaniu prostych program�w. Gdy zaczniesz pisa� d�ugie pisa� d�ugie, bardziej skomplikowane aplikacje, takie jak gry, przekonasz si� funkcje s� niezast�opione.

##Budowa funkcji 

Funkcja sk�ada si� trzech cz�ci: nazwy, parametr�w i tre�ci. Oto przyk�ad prostej funkcji:

```markdown
>>>
>>> def funkcjaTestowa(mojeImie):
...     print("Witaj %s" %mojeImie)
```

Nazwa funkcji to `funkcjaTestowa`. Ma ona jeden parametr, `mojeImie`, a jej tre�ci� jest blok kodu znajduj�cy si� bezpo�rednio pod wierszem zaczynaj�cym si� od `def`.
Aby wykona� funkcj�, nale�y j� wywo�a�, podaj�c kolejno jej nazw� i warto�� parametru w nawiasach:

```markdown
>>> funkcjaTestowa("Marta")
Witaj Marta
```

Mo�emy te� najpierw utworzy� kilka zmiennych, a nast�pnie wywo�a� funkcje, podaj�c ich nazwy jako parametry:








