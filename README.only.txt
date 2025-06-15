Acest proiect controlează un releu de încălzire pe baza temperaturii citite de la un senzor LM35. Utilizatorul poate ajusta pragul superior de temperatură prin intermediul butoanelor, iar toate informațiile sunt afișate pe un ecran LCD 16x2.

*Componente necesare
-Arduino UNO sau compatibil
-Senzor de temperatură LM35
-Releu (modul)
-Ecran LCD 16x2 (folosind librăria LiquidCrystal)
-4 Butoane:
OK (confirmă sau intră în mod editare)
Cancel (resetează la valoarea implicită sau întrerupe temporar controlul)
Plus (+) (crește temperatura de oprire)
Minus (-) (scade temperatura de oprire)
-Rezistențe de pull-down dacă nu folosești INPUT_PULLUP
-Fire de conexiune
-Breadboard (opțional)

*Conexiuni
LCD RS	D12
LCD EN	D11
LCD D4	D5
LCD D5	D4
LCD D6	D3
LCD D7	D2
Releu (IN)      D10
LM35	        A0
Buton OK	D8
Buton Cancel	D9
Buton Plus (+)	D6
Buton Minus (-)	D7

Toate butoanele sunt configurate cu INPUT_PULLUP, deci trebuie conectate între pin și GND.

*Funcționalități
-Afișarea temperaturii curente pe LCD.
-Control automat al releului:
-Se pornește dacă temperatura scade sub tempOn (ex: 50°C).
-Se oprește dacă temperatura depășește pragul ajustabil (tempOff).
-Timp de încălzire și răcire afișat dinamic pe LCD.
-Mod de editare al temperaturii de oprire (cu butoanele +, -, OK, Cancel).
-Resetare la temperatura implicită și oprirea controlului cu Cancel.

*Utilizare
La pornire, LCD-ul afișează mesajul „Initializing...”.
După pornire:
Vezi temperatura curentă și starea sistemului (Heating, Cooling, Idle).
Apasă OK pentru a intra în modul de editare.
Folosește + și - pentru a ajusta temperatura de oprire (tempOff).
Apasă OK din nou pentru a salva noua valoare.
Apasă Cancel pentru a reseta temperatura la valoarea implicită și a opri temporar controlul.

*Cod sursă
Codul include debounce pentru butoane și tratează stările de editare, răcire și încălzire.
Temperatura este citită analog de la LM35, convertită în grade Celsius.

*Note
tempOn: Temperatura la care se pornește încălzirea (default: 50°C).
tempOff: Temperatura la care se oprește încălzirea (default: 55°C, ajustabilă).
coolingThreshold: Dacă temperatura scade sub 40°C, sistemul consideră că s-a terminat faza de răcire.