# stripe-lexoffice-csv

Dieses kleine Tool soll dir helfen die Salden aus Stripe in deine Lexoffice Buchhaltung zu übernehmen. Der Api Schlüssel wird verwendet um den Name des Kunden zu hinterlegen. Ansonsten wird die Salden export csv aus Stripe so umformatiert das diese dirket in Lexoffice als Bank Import verwendet werden kann.

Benötigte Packages:
 - csv (standard libary, no need to install)
 - stripe
	 

## Einrichtung (tested on mac)
 - Lade dir das Repository runter.
 - Installiere die oben genannten Packages (bspw. mit "python3 -m venv ." > "source ./bin/activate" > "python3 -m pip install stripe").
 - Erstelle einen [eingeschränkten Stripe API Schlüssel](https://dashboard.stripe.com/apikeys/create) > bei **Charges** auf Lesen klicken > Schlüssel erstellen > Schlüssel kopieren
 - Hinterlege im deinen Stripe API Key in der Datei stripe.key
 - In Lexoffice lege ein neues Bankkonto an: Finanzen > Bank > "..." recht oben > Konto hinzufügen > Neues Konto > Daten ausfüllen (Konto unterstützt keine Anbindung, daher machen wir das ja Manuell)

## Benutzung
 - Export der csv Datei mit den zu konvertierenden Daten hier herunterladen: *[Salden](https://dashboard.stripe.com/balance/overview) > [Alle Aktivitäten](https://dashboard.stripe.com/balance) > **Exportieren** klicken > Spalten auf **Spalten (17)** stellen > Zeitraum wählen > Export runterladen
 - Datei in **import.csv** umbenennen und in den gleich Ordner wie main.py legen
 - Starte das Script mit python3 main.py
 - Du erhältst die angepasste CSV-Datei **export.csv** im gleichen Ordner.
 - in Lexoffice > Finanzen > Bank > bei deinem bei der Einrichtung erstelltem Stripe Bankkonto auf **...** > Umsätze importieren (CSV) > export.csv hochladen > Weiter > Importieren (die erste Zeile (header) wird zwar mir importiert, schlägt aber im nächsten Schritt fehl)
 - Import sollte jetzt geklappt haben. Jetzt auf die Nicht zugeordneten Umsätze
 - die Erlöse mit den jeweiligen Kundenrechnungen verbuchen
 - "STRIPE PAYOUT" mit "Geldtransit" buchen, hier wurde das Geld nur vom neuen Stripe Konto aufs Girokonto übertragen (auch mit "Geldtransit" verbuchen)
 - Die Stripe Gebühren dann mit der Rechnung von Stripe [Einstellungen > Konformität und Dokumente > Dokumente](https://dashboard.stripe.com/settings/documents) verbuchen

## Disclaimer

Beachte das dieses Script und diese Anleitung nur eine freiwillige Hilfestellung ist, die Fehler enthalten kann. Es kann daher keine Haftung übernommen werden, die aus der Nutzung des Script und/oder der Anleitung entstehen. Checke selbst nochmal das das alles passt. Melde dich falls du hier einen Fehler findest.