Contao Task Center Extension
============================

This is the "Task Center" extension for Contao Open Source CMS, which was
bundled with the core until version 3. It allows you to create tasks, assign
them to other users and track their progress.


Installation
------------

The extension can be installed using the Contao extension manager in the Contao
back end. If you prefer to install it manually, download the files here:

http://contao.org/de/extension-list/view/tasks.html


Tracker
-------

https://github.com/cliffparnitzky/TaskCenter/issues


Compatibility
-------------

- min. version: Contao 2.9.5
- max. version: Contao 2.9.5


Dependency
----------

- There are no dependencies to other extensions, that have to be installed.


Features
--------

 1. Ersteller eines Komentar
	- Anzeige in der Aufgabenhistorie
	- Issue: http://dev.contao.org/issues/1701
 2. Feld: 'Stand'
	- im Filter
 3. Feld: 'Status'
	- weiterer Wert: Analysiert (per DCA)
	- im Specialfilter (Mehrfachauswahl m�glich, Issue: http://dev.contao.org/issues/1275)
 4. neues Feld: 'Priorit�ten'
	- Werte: sehr hoch, hoch, normal, niedrig, sehr niedrig
	- mit entsprechenden Icons
	- Anzeige in der Liste
	- �ndern im Formular
	- im Specialfilter (Mehrfachauswahl m�glich)
	- Erweiterung per DCA
 5. neues Feld: 'Aufgabentyp'
	- Werte: Fehler / Bug, Verbesserung / Improvement, Aufgabe / Exercise, Neue Funktion / New Feature
	- Anzeige in der Liste
	- �ndern im Formular
	- im Specialfilter (Mehrfachauswahl m�glich)
	- Erweiterung per DCA
 6. Feld: 'Kommentar'
	- Tiny Editor f�r den Text (eigene Tiny Definition: ohne 'newdocument', mit 'hr'/'strikethrough')
	- Issue: http://dev.contao.org/issues/1275
 7. Systemeinstellungen
	- Default Selektion von "Benutzer benachrichtigen" (Issue: http://dev.contao.org/issues/1275)
 8. Feld: 'Id'
	- Anzeige in der Liste
	- im Filter
	- in der Suche
 9. Filter wird nach Wertwechsel ausgel�st (onChange Event)
10. Style (CSS Klasse / CSS Style) f�r jeweiligen Status oder "Dealine erreicht" wird per DCA definiert
    - kann in system/config/dcaconfig.php angepasst werden
11. Feld: '�bertragen an'
	- ist nicht mehr vorbelegt -> explizite Auswahl eines Benutzers
12. Anpassung Notification Mail
    - keine Email an sich selbst (aktuelles Benutzer = Bearbeiter -> keine NotificationMail)
    - Mailtext per Sprachdatei definier- bzw. anpassbar ($GLOBALS['TL_LANG']['tl_task_mail']['notification'])
	- Backendsprache des Empf�ngers definiert die Mailsprache
	- Angaben von HTML und Plain Text
	- Ausgabe aller Aufgabe Attribute mittels Insert Tags (Dokumentiert in der Sprachdatei)
13. Detailseite zum Anzeigen eines Aufgabe im Nur-Lese-Modus
    - Anzeige der Daten inkl. letzter Aktualisierung, sowie kompletter Bearbeitungshistorie
    - Verkn�pfung in den Emails auf die Detailsseite
	- Button in der Aufgabenliste
14. Einbindung als separaten Zweig im Backend Baum
    - Task Center
	  - Aufgaben
	  - Projekte
15. Projektverwaltung
    - Anlegen von Projekten mit Name, Kurzname, Projektleiter uvm.
	- Einbindung Projekt in Aufgabe (nur ver�ffentlichte Projekte k�nnen benutzt werden)
16. Sortierung mit Contao Standard Widget
17. Task Center nur f�r bestimmte Benutzergruppen konfigurieren
	- in den Benutzergruppeneinstellungen kann das Task Center aktiviert bzw. deaktiviert werden
	- Link: http://www.contao-community.de/showthread.php?11672-Backend-Module-f%FCr-Benutzer-bzw.-Benutzergruppen-einschr%E4nken&highlight=task+center
18. Benutzereinstellungen
    - Email an sich selbst (wenn ich Bearbeiter eine Aufgabe und Kommentarverfasser)
	- Sortierung der Bearbeitungshistorie (http://www.contao-community.de/showthread.php?15005-Im-Task-Center-die-Bearbeitungshistorie-anders-rum-darstellen&highlight=task+center)
	- sichtbare Spalten in der �bersichtstabelle
    - Verwendung von Kurznamen in der Spalten�berschriften der �bersichtstabelle
	- Verwendung von Icon statt Text in der �bersichtstabelle f�r Aufgabentyp, Priorit�t und Status
	- Auswahl des Iconsets f�r Priorit�ten (Flaggen, Pfeile)
19. Buttons f�r mehr Funktionen in den Erstell- / Editier-Masken
    - Aufgaben erstellen: "Erstellen", "Erstellen und bearbeiten", "Erstellen und neu"
	- Aufgaben bearbeiten: "Aktualisieren", "Aktualisieren und schlie�en"

Planung
-------

 ?. Anpassung an Contao 2.10.0
    - Hinweise: http://www.contao.org/neuigkeiten/items/contao_2-10-RC1.html
 ?. Erweiterung um Job, der t�glich 1 x pr�ft, f�r welche Tasks die Dealine erreicht ist und dann eine Email an den Bearbeiter schickt
	- Ausf�hrung: t�glich per CRON Job
	- Inhalt f�r HTML und Text Mail in DCA Konfiguriert
	- in Einstellungen definierbar, ob Job ausgef�hrt werden soll
	- in Einstellungen definierbar, wann die Mail rausgehen soll: 1 Woche vorher, 1 Tag vorher, am Tag der Dealine (per DCA um zus�tzlich Werte erweiterbar ???)
 ?. Aufgaben f�r Benutzergruppen sichtbar, bearbeitbar, entsprechend Projektkonfiguration
    - Matrix erstellen
 ?. Dateianh�nge
	- Issue: http://dev.contao.org/issues/1275
 ?. Anpassung Startseite
    - Hook: parseBackendTemplate 
 ?. Email wenn Aufgabe gel�scht an letzten Bearbeiter und Projektleitung --> ggf. per Extra Extension --> Hooks f�r create, update and delete task einf�gen
 ?. FE Modul zum Erfassen von Aufgaben
    - erlaubte Mitgliedergruppen im Projekt definieren
	- FE Modul
      - Projekt (bietet eingeloggtem Mitglied nur ver�ffentlichte Projekte an, die f�r seine Mitgliedergruppen definiert sind)
	  - Titel, Endtermin, Aufgabentyp, Priorit�t, Kommentar
	  - wird automatisch dem Projektleiter zugewiesen --> automatisch per Mail benachrichigen
	  - Tiny f�r Kommentar: http://www.contao-community.de/showthread.php?551-Smileys-im-Kommentar-Modul-%28ContentComments.php%29
 ?. �ffentlichkeitsstatus des Projektes in der BE Liste der Tasks anzeigen als Icon
 ?. �berlegen was mit Aufgaben ist, wenn das Projekt nicht ver�ffentlicht ist, bzgl. bearbeiten und l�schen
 ?. Systemeinstellung
	- L�schen von Aufgaben verbieten --> blendet Button "delete" aus
	- Vorgaben von Folgezust�nde
	- Definition, welche Operationen in welchem Status m�glich sind (z.B. ARCHIVED --> keine Edit)
 ?. was passiert mit Projekt wenn Aufgaben dran h�ngen, bzw. was passiert mit Aufgaben, wenn Projekt gel�scht wird
 ?. Benutzereinstellungen
	- Initialisierung der Spalte nach Installation --> default Wert?
 ?. Projekt
    - Projektzugeh�rigkeit: Gruppen erlauben --> Subpalette mit Benutzergruppen / Mitgliedergruppen (Benutzergruppen = mandatory) ... muss noch ausgewertet werden
 ?. Status Variablen entsprechend der Reihenfolge wie sie vorkommen sortieren
 ?. Projekte f�r Mitgliedergruppe erlauben, aber nicht f�r Benutzergruppe ??? ---> JA, Adminprojekt, was Issues aus dem FE erhalten kann
 ?. Link f�r Tiny zum Tasks

Fehler
------

 ?. �nderung der Deadline wird nicht in Email angezeigt
 ?. Fehler im Toggel wenn Datum gesetzt bei der Projektverwaltung