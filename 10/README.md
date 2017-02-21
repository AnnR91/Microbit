#Mowa

Komputer i roboty, kt�re m�wi� czuj� si� bardziej ludzkie. Sprawienie aby micro:bit m�wi� jest tzw. form� przekazywania informacji w formie zabawy, 
w skuteczny i u�yteczny spos�b. W zwiazku z tym w urz�dzeniu wbudowany jest syntezator mowy oparty na in�ynierii wstecznej wersji syntezatora z 1980 roku.

Brzmi to bardzo fajnie, maj�c to na uwag� zamierzamy wykorzysta� syntezator mowy do stworzenia...

##Dalek Poetry

![dalek][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/dalek.jpg "robot dalek"

To bardzo ma�o znany fakt, �e Dalekowie uwielbiaj� poezje - szczeg�lnie limeryki. Kto by pomy�la�, ale fakt jest faktem. 
W ka�dym razie chcieliby�my aby Dalek nam recytowa� na �adanie.

##Powiedz co�

Przed umo�liwieniem m�wienia urz�dzeniu musimy pod��czy� przewody, tak jak na obrazku poni�ej:

![plytka][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/speech1.png "obraz plytki"

Najprostszym sposobem na uzyskanie mo�liwo�ci m�wienia jest zaimportowanie `speech` czyli modu�u mowy. U�yj tej funkcji np. tak:

```markdown

import speech

speech.say("Hello, World")
```

Chocia� sprawili�my, �e nasze urz�dzenie przem�wi�o i jest to fajne, nie przypomina to robota Dalek. Wi�c musimy zmieni� niekt�re parametry.
Aby przystosowa� syntezator mowy dla naszych potrzeb, syntezator mowy jest bardzo mocny w tym zakresie, poniewa� mo�emy zmienia� cztery parametry:

*`pitch` - jak wysoki lub niski jest d�wi�k g�osu (0 = wysoki, 255 = Barry White)
*`speed` - jak szybka jest mowa urz�dzenia (0 = niemo�liwy, 255 = bajka na dobranoc)
*`mouth` - jak wydawa� d�wi�ki z zaci�ni�tymi lub otwartymi ustami (0 = manekin brzuchom�wcy, 255 = Foghorn Leghorn)
*`throat` - jak zrelaksowany lub napi�ty jest ton g�osu(0 = rozstrz�siony , 255 = totalnie wyluzowany)

��cznie, paramatry te kontroluj� jako�� d�wi�ku (barwa). M�wi�c szczerze to najlepszy spos�b, aby uzyska� ton idealny ton g�osu. Chcesz eksperytmentowa�, 
�mia�o dzia�aj z d�wi�kiem i os�dzaj jego jako��. 

My r�wnie� ekperymentowali�my, i oto nasz przyk�ad: 

```markdown
speech.say(" I am a Dalek, I'm deadly", speed=120, pitch=150, throat=100, mouth=230)
```

##Poezja

Mo�na r�wnie� kaza� naszemu urz�dzeniu aby m�wi� nam limeryki:

```markdown
# DALEK poetry generator, by The Doctor
import speech
from microbit import sleep

poem = [
    "there was a young man from koczala"
    "where he was born",
    "He returned to his hometown dark",
    "he went to the lake",
    "and I have been there forever",
    "EXTERMINATE",
]

# Loop over each line in the poem and use the speech module to recite it.
for line in poem:
    speech.say(line, speed=120, pitch=100, throat=100, mouth=200)
    sleep(500)
	
```

Jak wida� mamy ustawienia mowy 

##Za�piewaj piosenke

Zmieniaj�c ustawienie `pitch` i wywo�anie funkcji `sing` sprawi, �e urz�dzenie nam za�piewa (cho� pewnie nie wygra eurowizji ;))
Mapowanie numer�w skoku do nut znajduje si� poni�ej:

![nuty][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/speech.png "obraz nut"

```markdown
speech.sing("#115DOWWWW")
```

```markdown
import speech
from microbit import sleep

# The say method attempts to convert English into phonemes.
speech.say("I can sing!")
sleep(1000)
speech.say("Listen to me!")
sleep(1000)

# Clearing the throat requires the use of phonemes. Changing
# the pitch and speed also helps create the right effect.
speech.pronounce("AEAE/HAEMM", pitch=200, speed=100)  # Ahem
sleep(1000)

# Singing requires a phoneme with an annotated pitch for each syllable.
solfa = [
    "#115DOWWWWWW",   # Doh
    "#103REYYYYYY",   # Re
    "#94MIYYYYYY",    # Mi
    "#88FAOAOAOAOR",  # Fa
    "#78SOHWWWWW",    # Soh
    "#70LAOAOAOAOR",  # La
    "#62TIYYYYYY",    # Ti
    "#58DOWWWWWW",    # Doh
]

# Sing the scale ascending in pitch.
song = ''.join(solfa)
speech.sing(song, speed=100)
# Reverse the list of syllables.
solfa.reverse()
song = ''.join(solfa)
# Sing the scale descending in pitch.
speech.sing(song, speed=100)
```






