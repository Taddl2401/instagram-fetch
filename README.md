# instagram-fetch
Wordpress Block | Instagram Wall / Slider

Schritt 1: App vorbereiten:

Rufe dein Facebook / Meta Developer Dashboard auf und erstelle deine App!
Folgende Werte kannst du schon entnehmen:

client_id

client_secret

redirect_uri

App-Werte finden

Folgende Zugänge benötigen wir vom Kunden:

Instagram - Username

Instagram - Password

(Standard E-Mail)

Schritt 2: Logik vorbereiten:

Erklärung Dateien:

get_posts.php             | Logik zum Abrufen/Speichern der Posts per Access-Token

get_AuthBearer.php    | Logik zum automatischen Update von Access-Tokens

instagram.json             | Ablageort der Instagram Posts (URL´s laufen ab)

instagram-slider.php   | Ausgabe der Posts als Owl-Carousel-Slider



Am Beispiel: http://klimakarl.de :

Erstelle den Ordner “Instagram-fetcher” (Struktur übernehmen) 

Öffne die Datei “get_posts.php”:Prüfe die Pfade & Links auf RichtigkeitTrage dich (wenn App-Admin) als Empfänger der Fehler-Mails ein (Line: 48)-> Bei Ersteinrichtung sollte der Entwicklermodus aktiviert werden (Line 1)

Öffne die Datei “get_authBearer.php”:Trage die App-Werte aus Schritt 1 ab Zeile 3 ein.Prüfe die Pfade & Links auf RichtigkeitPasse in Zeile 69 die Link-URL an (soll auf get_posts.php zeigen)

Öffne die Datei “instagram-slider.php” (Einbetten variiert je nach System)Prüfe die Pfade & Links auf RichtigkeitSetze den Link zum Instagram Account in Zeile 29

Lege einen Cronjob an, der (täglich - alle 2-4 Stunden) auf neue Instagram Posts prüft=> auf “get_posts.php”

Lege noch einen Cronjob an, der (Mo, Mi, Fr) den AccessToken auf gültigkeit prüft und bei Bedarf aktualisiert => auf “refreshAccessToken.php”

!!!Cronjob Leitfaden unbedingt lesen!!!
(weil: gängiges Sonderzeichen-Problem)

Detailiertere Informationen zum Anlegen der Cronjobs bei DomainFactory findest du hier:

https://kreativkarussell.atlassian.net/l/cp/8NW2FhSV 





Schritt 3: Autorisierung anfordern:Instagram-Nutzer-Zugriffsschlüssel

Um mit dem Vorgang zu beginnen, rufe das Autorisierungs Fenster ab (App-Werte in Code eintragen) und präsentiere es dem Benutzer:Der Benutzer muss in der gleichen Browsersession bei seinem entsprechenden Instagram eingeloggt sein.

https://api.instagram.com/oauth/authorize?client_id={instagram-app-id}&redirect_uri={redirect-uri}&scope=user_profile,user_media&response_type=code

 

Sobald der Instagram Nutzer die Verknüpfung zwischen der App und seinem Account bestätigt, wird ein User Auth-Code gespeichert, gegen den kurzlebigen Instagram-Schlüssel getauscht (1h gültig) und dieser anschließend zu einen langlebigen-Instagram-Schlüssel (60 Tage gültig) konvertiert.

Die langlebigen Schlüssel werden in der App automatisch ausgetauscht. Ein Eingreifen ist nicht erforderlich.



Fehlerbehebung:

bei einem Fehler wird eine E-Mail an Elias Florman und Christian Wahl gesendet (bei kreativkarussell.de auch an die info@)

Die Fehler werden in die instagram.json geschrieben (wo die Posts sonst stehen).

(Wenn der Slider schon länger läuft und unerwartet einen Fehler generiert, kann der Kunde das Instagram Passwort geändert haben - einfach mit neuem Passwort Schritt 3 ausführen)

Abhilfe: Schritt 3 ausführen
