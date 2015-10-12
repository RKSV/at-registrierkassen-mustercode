# Change Log
* **12.10.2015**: Release 0.2 auf GitHub veröffentlicht
	* **Wichtige Änderungen**:
		* Erweiterung der Prüfwerkzeuge
			* Detaillierte Prüfung von einzelnen Belegen (vor allem Format)
			* Detaillierte Prüfung des DEP-Export-Formats (vor allem Format)
			* Detaillierte Rückmeldungen zu Formatfehlern (MWST-Sätze, BASE64, RK Suite etc.)
	* Detailänderungen
		* Hinzufügen von Provider-unabhängigen [Nimbus JWS Library](https://bitbucket.org/connect2id/nimbus-jose-jwt/wiki/Home) (Demo-Code noch nicht Provider-unabhängig)
		* Entfernen des rudimentären Prüf-Codes
* **02.10.2015**: Release 0.1 auf GitHub veröffentlicht

**Planung für weitere Releases**:

 - PKCS11 Integration um Standard-Krypto-Produkte einbinden zu können
 - APDU Integration, um Signaturkarten direkt einbinden zu können
 - Erweiterung Use Cases (Signatureinrichtung ausgefallen, etc.), Erstellung und Prüfung

# Überblick
Dieses Projekt stellt Demo-Code als Begleitung zur Registrierkassensicherheitsverordnung (RKSV) (https://www.bmf.gv.at/steuern/Registrierkassensicherheitsverordnung.html) zur Verfügung. Der Demo-Code zeigt

* wie die wesentlichen Elemente der Detailspezifikation der Verordnung in Software implementiert werden können,
* gibt zusätzliche Erläuterungen zu Aspekten der Detailspezifikation die noch Interpretationsspielraum zulassen,
* und stellt Prüfwerkzeuge zur Verfügung, die es erleichtern die korrekte Umsetzung einer Registrierkasse im Sinne der Detailspezifikation zu überprüfen (diese Werkzeuge werden ständig erweitert, siehe ChangeLog).

In diesem Projekt werden vorwiegend technische Aspekte der Verordnung betrachtet. Die Informationen und der Code werden laufend erweitert und mit typischen Fragen/Antworten ergänzt.

## Wichtige Anmerkungen/Einschränkungen
* *Version 0.1 (02.10.2015) und 0.2 (12.10.2015)*: Mit den Versionen 0.1 und 0.2 werden im Demo-Code die wesentlichen Elemente in Bezug auf Signaturaufbereitung, Signaturerstellung, Erstellung des QR-Codes, Erstellung des OCR-Codes sowie der Export des Daten-Erfassung-Protokolls (DEP) demonstriert. Erweiterte Themen wie z.B. die korrekte Behandlung des Ausfalls der Signatureinheit, werden in späteren Versionen behandelt.
* *Wichtige Anmerkung*: Die Versionen 0.1 und 0.2 demonstrieren wie mit den unterschiedlichen Elementen (Signature, QR-Code etc.) umgegangen werden muss. Obwohl hier nach bestem Gewissen vorgegangen wurde, kann keine GARANTIE für die korrekte Funktionsweise übernommen werden. Um hier in den nächsten Versionen mehr Klarheit bieten zu können, werden vom aktuellen Code unabhängige Prüfwerkzeuge geschaffen. Diese ermöglichen den Kassaherstellern die jeweiligen Produkte (und auch diesen Demo-Code) so weit wie möglich auf das korrekte Verhalten mit Relevanz für die Verordnung zu überprüfen.
* *Sprache*: Diese Projektseite verwendet Deutsch als Sprache. In den textuellen Ergänzungen im Source Code wird Englisch verwendet.

##Weiteres Vorgehen
Diese Plattform wird für die weitere Bereitstellung von Demo-Code, für das Bereitstellen von Prüfwerkzeugen und für die Erstellung von FAQs verwendet. Die weiteren Versionen des Codes werden demnächst veröffentlicht und fokussieren sich auf erweiterte Verwendungsmuster (z.B. Ausfall Sicherheitseinrichtung) und das Bereitstellen von Prüfwerkzeugen die es ermöglichen erstellte Belege, DEP-Export-Dateien auf Ihre Korrektheit zu prüfen. Auch wird dieses Projekt laufend um Antworten zu häufig gestellten Fragen ergänzt.

##Kontakt/Fragen
Es wurde dazu eine Projektseite von der WKO eingerichtet. Es ist dazu eine Registrierung bei der WKO notwendig.

https://communities.wko.at/Kassensoftware/default.aspx

Etwaige Fragen sollten dort im Forum gestellt werden, um eine möglichst effizient die Beantwortung durchführen zu können. 

https://communities.wko.at/Kassensoftware/Lists/Forum/

Ausgewählte Fragen/Antworten werden aus diesem Forum übernommen und auf der hier verfügbaren WIKI Seite eingetragen.

https://github.com/a-sit-plus/at-registrierkassen-mustercode/wiki/Erläuterungen-FAQ

## Lizenz
Der gesamte Code wird unter der Apache 2.0 Lizenz zur Verfügung gestellt.(http://www.apache.org/licenses/LICENSE-2.0). 

Alle verwendeten Dritt-Bibliotheken und deren Lizenzen sind in den Maven Build Dateien (pom.xml) der einzelnen Module ersichtlich und auf der folgenden WIKI Seite zusammengefasst:

https://github.com/a-sit-plus/at-registrierkassen-mustercode/wiki/Lizenzen-Dritt-Bibiliotheken

# Verwendung des Democodes und der Demokassa

##Ausführen des Codes (Verwenden der Downloadpakete)
Neben dem Source Code wird auch immer eine ZIP Datei der ausführbaren Dateien zur Verfügung gestellt. Die neueste Version ist immer unter [Releases](https://github.com/a-sit-plus/at-registrierkassen-mustercode/releases) zu finden.

###Voraussetzungen
* *Java VM*: Es wird eine aktuelle Java VM (JRE ausreichend) mit Version >= 1.7 benötigt.
* *Kryptographie*: Der Registrierkassen-Demo-Code verwendet starke Kryptographie (z.B. AES mit 256 bit Schlüssel), der mit den Standard-Export Policies der Java VM nicht ausgeführt werden kann. Es muss daher die "Unlimited Strength Policy" von Oracle installiert werden. Siehe: "http://www.oracle.com/technetwork/java/javase/downloads/index.html"

###Verwendung des Demo-Codes - Demokassa
Der Demo Code enthält aktuell eine einfache Testklasse die eine Demokassa ansteuert. Diese Demokassa bietet die Möglichkeit eine angegeben Anzahl von Belegen zu erstellen, diese in das DEP Export Format zu exportieren, und einfache Test-Belege als PDF zu erstellen, die die Daten als QR-Code oder OCR-Code beinhalten.

Download und entpacken von regkassen-demo-release-0.2.zip (siehe https://github.com/a-sit-plus/at-registrierkassen-mustercode/releases).

Ausführen der Demokasse mit

      java -jar regkassen-demo-0.2.jar -o OUTPUT_DIR -n 20
      
Wobei "OUTPUT_DIR" ein Verzeichnis ist, in dem die vom Demo-Code erstellten Daten/Belege geschrieben werden. Es wird in der aktuellen Version dazu ein zufällig genierter Signaturschlüssel verwendet. Wenn die Option "o" nicht angegeben wird, dann wird im aktuellen Verzeichnis eines mit dem Prefix CashBox ersteerlällt.
Die Option "n" gibt die Anzahl der zu erstellenden Belege an. Wenn sie nicht angegeben wird, werden 15 Belege erstellt.
Das Output-Verzeichnis enthält folgende Dateien/Verzeichnisse:
 - **Datei dep-export.txt**: Die generierten Belege im DEP Export Format (Detailspezifikation, Abs 3)
 - **Datei qr-code-rep.txt**: Die textuelle Representation der maschinenlesbaren QR-Codes (der Inhalt der QR-Codes). Eine Zeile der Datei entspricht der QR-Code Repräsentation eines Belegs.
 - **Datei ocr-code-rep.txt**: Die textuelle Representation der maschinenlesbaren OCR-Codes. Eine Zeile der Datei entspricht der OCR-Code Repräsentation eines Belegs.
 - **Datei signatureCertificate.cer**: Das Signatur-Zertifikat im DER-Format
 - **Verzeichnis ocr-code-dir**: PDF-Belege die mit dem OCR-Code bedruckt wurden
 - **Verzeichnis qr-code-dir**: PDF-Belege die mit dem QR-Code bedruckt wurden

Ein Beispiel für den Output ist auch direkt verfügbar: example-output-0.2.zip (siehe https://github.com/a-sit-plus/at-registrierkassen-mustercode/releases).
Code dazu: siehe Klasse [SimpleDemo](https://github.com/a-sit-plus/at-registrierkassen-mustercode/blob/master/regkassen-democashbox/src/main/java/at/asitplus/regkassen/demo/SimpleDemo.java).

###Verwendung des Prüfwerkzeugs
In Version 0.2 wurden die Prüfwerkzeuge um detalliertet Formatprüfungen erweitert. Neben dem DEP Export Format können nun auch einzelne QR-Code-Bsp von Belegen geprüft werden.
Download und entpacken von regkassen-demo-release-0.2.zip (siehe https://github.com/a-sit-plus/at-registrierkassen-mustercode/releases).

**DEP-Export Format**

    java -jar regkassen-verification-depformat-0.2.jar -i DEP-EXPORT-FILE
	         
Wobei

 - **DEP-EXPORT-FILE** der im vorigen Beispiel erstellten *dep-export.txt* Datei entspricht. Für den schnellen Test kann die Datei *dep-export.txt* aus dem Beipspiel übernommen werden.

**QR-Code-Repräsentation eines einzelnen Belegs oder mehrerer Belege**

    java -jar regkassen-verification-receipts-0.2.jar -i QR-CODE-REP-FILE -s SIGNATURE-CERTIFICATE-FILE

Wobei

 - **QR-CODE-REP-FILE** der im vorigen Beispiel erstellen *qr-code-rep.txt* Datei Datei entspricht. Für den schnellen Test kann die Datei *qr-code-rep.txt* aus dem Beispiel übernommen werden.
 - **SIGNATURE-CERTIFICATE-FILE** der im vorigen Beispiel erstellen *signature-certificate.cer* Datei entspricht. Für den schnellen Test kann die Datei *signature-certificate.cer* aus dem Beispiel übernommen werden.

**Anmerkung**: Sollten sich mehrere Belege in der Datei **QR-CODE-REP-FILE** befinden, so wird deren Verkettung NICHT überprüft. Diese Prüfung wird nur bei der DEP-Export-Format Prüfung durchgeführt.
                    
 
##BUILD Prozess, Details zum Code
Das Projekt ist in drei Maven Module aufgeteilt:
 - **regkassen-core**: Dieses Modul enthält den Code der für die Erstellung und Signatur der Belege notwendig ist.
 - **regkassen-democashbox**: Dieses Modul verwendet das regkassen-core Modul und setzt Demo-Use Cases um. Aktuell (Versionen 0.1 und 0.2) ist dort nur ein Demo enthalten, das Belege erstellt, diese signiert, PDF-Belege erzeugt und die Belege anhand des DEP-Export-Formats ablegt.

###Übersicht über den Code
 - [at.sitplus.regkassen.core.base](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/base): Diese Package enthält Basisdatenstrukturen, Hilfsfunktionen und die in der Detailspezifikation definierten RegKassen Suite. (Detailspezifikation, Abs 2). Link zu Code
 - [at.asitplus.regkassen.core.modules](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules):  In diesem Package sind die Module der Kassa enthalten.
	 - [DEP](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/DEP): Modul für die Implementierung des Datenerfassungsprotokolls. Wesentliche Funktionalität hier ist der EXPORT des DEPs (implementiert in *[SimpleMemoryDEPModule](https://github.com/a-sit-plus/at-registrierkassen-mustercode/blob/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/DEP/SimpleMemoryDEPModule.java)*)
	 - [init](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/init): Parameter für die Initialisierung der Registrierkasse
	 - [print](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/print): Einfache Version eines PDF Druckers, der QR-Codes und OCR-Codes auf Belege druckt.
	 - [signature](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature): Dieses Package besteht aus zwei Hauptkomponenten:
		 - [jws](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature/jws): Mit dem Modul [OrgBitbucketBcJwsModule](https://github.com/a-sit-plus/at-registrierkassen-mustercode/blob/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature/jws/OrgBitbucketBcJwsModule.java) oder [ComNimbusdsJwsModule](https://github.com/a-sit-plus/at-registrierkassen-mustercode/blob/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature/jws/ComNimbusdsJwsModule.java) werden die JWS Signaturen erstellt. Die Module greifen auf das folgende Package zu:
		 - [rawsignatureprovider](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature/rawsignatureprovider): Dieses Modul erstellt die wirkliche Signatur und kann eine Smartcard, ein HSM, ein Cloud-Dienst oder ein anderes Modul (im geschlossenen System) darstellen. Wichtige Anmerkung: In der aktuellen DEMO-Kassa ist nur ein simples Software-basiertes Modul enthalten ([DemoSoftwareSignatureModule](https://github.com/a-sit-plus/at-registrierkassen-mustercode/blob/master/regkassen-core/src/main/java/at/asitplus/regkassen/core/modules/signature/rawsignatureprovider/DO_NOT_USE_IN_REAL_CASHBOX_DemoSoftwareSignatureModule.java)). Dieses DARF AUF KEINEN FALL in einer echten Kasse verwendet werden. In weiteren Demo-Code Versionen wird hier die Ansteuerung der Karte gezeigt.
 - [at.sitplus.regkassen.core](https://github.com/a-sit-plus/at-registrierkassen-mustercode/tree/master/regkassen-core/src/main/java/at/asitplus/regkassen/core): In diesem Package befindet sich Demo-Registrierkasse (DemoCashBox). Diese Klasse verwendet die oben genannten Module um Belege zu speichern, zu signieren und zu drucken (als PDF).

###Maven Build
Um den Maven Build-Prozess eigenständig durchzuführen, sind in den jeweiligen Verzeichnissen folgende Schritte notwendig:

      regkassen-core: mvn install
      regkassen-democashbox: mvn install
      
In den Verzeichnissen regkassen-democashbox, regkassen-verification befinden sich nach dem erfolgreichen Build-Prozess die JAR Dateien (im Unterverzeichnis "target"), die zum Ausführen benötigt werden (siehe Punkte zur Verwendung des Demo-Codes weiter oben).

#Erläuterungen zur Detailspezifikation der Verordnung/FAQs
Werden laufend ergänzt:
https://github.com/a-sit-plus/at-registrierkassen-mustercode/wiki/Erläuterungen-FAQ

# Impressum
Informationen zu A-SIT und A-SIT Plus unter http://www.a-sit.at

A-SIT Plus GmbH
A-1030 Wien,
Seidlgasse 22 / 9
1030 Wien
FN 436920 f,
Handelsgericht Wien


