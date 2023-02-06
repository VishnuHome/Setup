# Setup
Enthält im Ordner *<u>Vishnu.src</u>* ein Archiv *<u>init.zip</u>* zur Ersteinrichtung lokaler Repository-Clones für ein umwandelbares **Vishnu** plus aller umwandelbarer Quellen für **Plugins** und das Basis-**Framework**.

Enthält außerdem im Ordner *<u>Vishnu.bin</u>* ein Archiv *<u>init.zip</u>* zur Ersteinrichtung für ein lauffähiges Vishnu ohne Quellen.

#### Dieses README.md befasst sich vor allem mit speziellen Informationen für Team-Mitglieder.<br/>Bitte beachte unbedingt auch die allgemeinen Informationen im [README.md auf VishnuHome/Vishnu](https://github.com/VishnuHome/Vishnu).

# Vishnu.src/init.zip
init.zip enthält die Grundausstattung für eine Ersteinrichtung lokaler Repository-Clones.

###### Voraussetzungen:

 - Läuft auf Windows-Systemen ab Version 7.
 - Entwicklung und Umwandlung mit Visual Studio 2019 oder höher.
 - Eigener GitHub-Account: https://github.com/login
 - Lokal installierte Git bash
   - Git bash downloaden und installieren:	https://gitforwindows.org/
 - SSH-Zugriff auf git@github.com einrichten: https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh

###### Vorbereitung:

 - [init.zip](https://github.com/VishnuHome/Setup/raw/master/Vishnu.src/init.zip) herunterladen und in ein Verzeichnis, das das Root-Verzeichnis für alle weiteren Verzeichnisse und Repositories sein soll, entpacken.

 - #### Wichtig: Eine Umgebungsvariable auf den Pfad zum Root-Verzeichnis für alle Repositories setzen, also das Verzeichnis in dem sich später Unterordner wie VishnuHome, InPlug oder WorkFrame, befinden, z.B.: Vishnu_Root=c:\\Users\\&lt;user&gt;\\Documents\VishnuRoot.
   
###### Installation:

- <u>*vollständige Installation (empfohlen):*</u> nacheinander in die Verzeichnisse WorkFrame, VishnuHome und InPlug wechseln und dort jeweils ./clone_&lt;Verzeichnisname&gt;.sh ausführen.
- <u>*Teil-Installationen:*</u> 
  - zusätzlich das [init.zip aus Vishnu.bin](https://github.com/VishnuHome/Setup/raw/master/Vishnu.bin/init.zip)
    herunterladen und in das Basisverzeichnis entpacken (vorhandene Dateien können überschrieben werden),
  - danach in das Verzeichnis VishnuHome wechseln und dort ./clone_VishnuHome.sh ausführen,
  - ggf. für die spätere Analyse/Bearbeitung von Vishnu-Plugins noch in das Verzeichnis InPlug wechseln und dort ./clone_InPlug.sh ausführen.

###### Batch-Umwandlung und -Verteilung:

- bei *<u>vollständiger Installation</u>* (bitte in der angegebenen Reihenfolge nacheinander ausführen): 
   - Im Verzeichnis WorkFrame: rebuildall_Framework.bat ausführen.
   - Im Verzeichnis VishnuHome: rebuildall_Vishnu.bat und danach copy_Vishnu_Bins_to_Vishnu.bin.bat ausführen.
   - im Verzeichnis InPlug: rebuildall_VishnuPlugins.bat und danach copy_Vishnu_Plugin_Assemblies.bat ausführen.
- bei *<u>Teil-Installation</u>*: 
   - Im Verzeichnis VishnuHome: rebuildall_Vishnu.bat und danach copy_Vishnu_Bins_to_Vishnu.bin.bat ausführen,
   - ggf. im Verzeichnis InPlug: rebuildall_VishnuPlugins.bat und danach copy_Vishnu_Plugin_Assemblies.bat ausführen.

###### Vishnu-Demo:

- Im Verzeichnis ReadyBin/Vishnu.bin das Script **_Vishnu_Demo.bat** starten.

###### *optional:* Company-eigene (Firmen-spezifische) Jobs und Assemblies verwalten:

 - Ein Company-Rootverzeichnis außerhalb der Vishnu_Root-Unterverzeichnisse anlegen.
 - Eine Umgebungsvariable auf den Pfad zum Company-Rootverzeichnis setzen, z.B.:
   Vishnu_Company=c:\\Users\\&lt;user&gt;\\Documents\\&lt;company-name>.
 - Im Company-Rootverzeichnis das in init.zip enthaltene init_Company.zip entpacken.
 - Die entstandenen Verzeichnisse Assemblies, Jobs, InPlug und WorkFrame können dann analog zu den existierenden Vishnu-Verzeichnissen genutzt werden
   (Jobs wie DemoJobs).

###### *optional:* eine eigene Vishnu-Veröffentlichung erstellen

 - Gegebenenfalls im Company-Rootverzeichnis copy_Company_all_to_Publication.bat ausführen.
 - Im Verzeichnis VishnuHome copy_all_to_Publication.bat ausführen.
 - Im Verzeichnis VishnuHome die Solution Vishnu/Vishnu.sln mit Visual Studio öffnen und
   - in den Eigenschaften der Projekte Vishnu und VishnuWeb die Signierung aktivieren und eigene Zertifikate hinzufügen.
   - Unter Veröffentlichen die relevanten Einstellungen ändern:
     - Speicherort des Veröffentlichungsordners,
     - URL des Installationsordners,
     - Updates.../Update-Pfad und Haken setzen bei Die Anwendung soll nach Updates suchen.
   - Haken setzen bei ClickOnce-Sicherheitseinstellungen aktivieren (macht der Veröffentlichungsvorgang ansonsten auch automatisch).
   
   Danach über den Button "Jetzt veröffentlichen" veröffentlichen.
   
   Hinweis: das Aktivieren der ClickOnce-Sicherheitseinstellungen führt zu etlichen Warnings der Art "Die &lt;Name&gt;-Assembly wurde falsch als Datei angegeben.".
   Sie sollten daher die ClickOnce-Sicherheitseinstellungen nach erfolgreicher Veröffentlichung wieder deaktivieren.
   Die Warnungen selbst können ignoriert werden. Wer sich für die Details interessiert, kann sich z.B. unter
   https://developercommunity.visualstudio.com/t/assembly-is-incorrecely-specified-as-a-file/172532 genauer informieren.

###### *abweichende Konfigurationen*

 - Über die Umgebungsvariable %Vishnu_Repository% kann eine abweichende URL zu den GitHub-Repositories gesetzt werden (Default ist git@github.com).
 - Über die Umgebungsvariable %Vishnu_Assemblies% kann ein anderer Ort für das "Assembly"-Verzeichnis gesetzt werden (Default ist ...ReadyBin/Assemblies).
 - Über die Umgebungsvariable %Vishnu_UserAssemblies% kann ein anderer Ort für das "UserAssembly"-Verzeichnis gesetzt werden (Default ist ...ReadyBin/UserAssemblies).
