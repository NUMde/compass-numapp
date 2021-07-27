# NUM-App

[General Documentation](https://github.com/NUMde/compass-numapp/tree/main/docs)

![App Overview](assets/numAppOverview.png "App Overview")

## About the NUM-App

[Zur Version auf Deutsch 🇩🇪](#über-die-num-app)

The NUM-App is an open source project to digitally conduct questionnaire-based studies. It is available as a mobile (native) app and a web app. The app is part of the [COMPASS project](https://num-compass.science/) (Coordination On Mobile Pandemic Apps Best Practice And Solution Sharing).

The NUM-App supports the international Fast Healthcare Interoperability Resources (FHIR) standard and enables displaying [FHIR Questionnaires](https://www.hl7.org/fhir/questionnaire.html) as well as encrypted transmission and storage of corresponding [FHIR Questionnaire Responses](https://www.hl7.org/fhir/questionnaireresponse.html).

## How the NUM-App works

The NUM-App provides a quick and easy way to digitally conduct questionnaire-based studies. Study participants fill out and submit questionnaires using their web browser or mobile device.

The study staff can easily retrieve submitted questionnaire responses and change questionnaires without the need for participants to reinstall or update their mobile app.

Questionnaire responses are always transmitted with end-to-end encryption, which makes the NUM-App suitable to conduct medical studies.

The app is easily customizable and can be adapted to individual requirements.

The main advantages of the app are:

* **Open-source**: Everyone can use the app and get involved in the development process.
* **Standards-based**: Using the international FHIR standard guarantees compatibility of the app.
* **Community-supported and funded**: The work of our community is guaranteed in the long run, thanks to funding by the [German Federal Ministry of Education and Research (BMBF)](https://www.bmbf.de/).
* **Practical**: Our community is supported by domain and technical experts, as we are a [COMPASS project](https://num-compass.science/) of the [NUM network](https://www.netzwerk-universitaetsmedizin.de/).
* **Simple**: The app can be set up and customized quickly, even without deep technical knowledge.

## Using the NUM-App

The NUM-App has the following components:

1. [Mobile Frontend](https://github.com/NUMde/compass-numapp-frontend): An easy to use mobile app (React Native) that can dynamically render FHIR Questionnaires and display information sections.

2. [Web Frontend](https://github.com/NUMde/compass-numapp-web): An easy to use web app (TypeScript) that can dynamically render FHIR Questionnaires and display information sections.

3. [Mobile & Web Backend (+ Database)](https://github.com/NUMde/compass-numapp-backend): Backend component which provisions FHIR Questionnaires based on user context and manages storing FHIR Questionnaire Responses.

4. [Downloader Script](https://github.com/NUMde/compass-numapp-downloader): Component to retrieve and decrypt the submitted FHIR Questionnaire Responses.

You need to set up at least one Frontend, the Backend, and the Downloader Script to enable the end-to-end usage flow of the NUM-App, including the provisioning of a FHIR Questionnaire, the storage of the corresponding response and its retrieval.
See the documentation files of the linked repositories for information on setup and configuration.

For general documentation on aspects that are component-unspecific (for example, encryption and forking), see the [docs](https://github.com/NUMde/compass-numapp/tree/main/docs).

You can find videos of our recorded [enabling sessions on YouTube](https://www.youtube.com/channel/UC_JVfREe2bDR87dPjV7Y8og). A collection of more links to useful information sources is [available here](https://drive.google.com/file/d/17TCqD8hVgp68FOXxgf0y6n2ms1Q3IBX3/view).

<p align="center">
    <img src="assets/componentOverview.png" alt="Component Overview" width="600">
</p>

## Example: COVID-19 study using the NUM-App

The following example shows how you can use the NUM-App to digitally conduct your (clinical) studies. Meet Max, who participates in a COVID-19 study at a university hospital.

<img src="assets/studyFlow_EN.png" alt="Visualization Study Flow" width="400" align="right">

### Step 1 - Logging in and first questionnaire

<div class="block">Max receives a personalized QR code from the hospital, which he scans with the NUM-App to log in. A special questionnaire is displayed, as it is the first time he uses the app. The initial questionnaire includes questions that Max must only answer once. Max completes the questionnaire in one go and submits it. The NUM-App transforms it into a FHIR Questionnaire Response object, encrypts it, and transmits it to the backend where it is persisted.</div>

### Step 2 - Retrieving questionnaire responses

<div class="block">The study staff at the university hospital wants to check if new questionnaire responses were submitted. A staff member runs the downloader script and the encrypted response from Max is retrieved and decrypted locally.</div>

### Step 3 - Answering standard questionnaires

The study staff defined a questionnaire frequency of seven days. Therefore, Max receives a new standard questionnaire once a week. When he completes one, the NUM-App shows him the time when the next questionnaire becomes available. As Max is not checking the NUM-App every day, a push notification is sent to his mobile app when a new questionaire is available. The study staff set the time of the day for the notification to 10:00 AM, so Max is reminded once a week at that time. As the questionnaire is quite long, Max does not always answer all questions in one go. As the NUM-App saves his answers, he can always complete the questionnaire later.

### Step 4 - Answers triggering alternative questionnaires

At one point during the study, Max answers one of the questions with a value that was predefined as a _trigger value_. In this study, this is the information that Max has tested positive for coronavirus. This is detected by the NUM-App. After Max submits the questionnaire, his profile is automatically adapted based on preconfigured settings. Instead of the standard questionnaire, Max now receives an alternative questionnaire. Also, the questionnaire frequency is increased to once a day and the distribution time of the new questionnaire is set to seven days. Max now receives the new questionnaire daily for one week. After that, the settings are back to their initial values.

### Step 5 - Submitting special reports

Max is provided the standard questionnaire again. He has already finished most of the recent one and has to wait six days for the next to become available. However, after one day he notices common COVID-19 symptoms and requests a special report using the app. This again triggers a change to Max's user profile. He now receives a special questionnaire independent of the normal frequency and can directly report his symptoms. Afterwards, he will go back to the standard reporting as not configured otherwise. However, in the meantime, the study staff changed the standard questionnaire frequency to five days instead of seven. So Max now receives the standard questionnaires every five days.

### Step 6 - Retrieving questionnaire responses

It has been a while since the study staff retrieved the latest questionnaire responses. They run the downloader script and receive all questionnaire responses that Max submitted since the last retrieval. They also receive an entry with the special symptom report that Max sent. They can process the decrypted responses as needed.

## Get involved!

Our community depends on everyone's active contributions. Take the first step and join our [Meetup group](https://www.meetup.com/de-DE/num-compass) and our events.

Gain an impression of our work and take a look at our videos in the [COMPASS YouTube channel](https://www.youtube.com/channel/UC_JVfREe2bDR87dPjV7Y8og).

### NUM-App licensing

The NUM-App components are licensed under the Apache 2.0 and MIT licenses:

Apache 2.0

* [Mobile Frontend](https://github.com/NUMde/compass-numapp-frontend)
* [Mobile & Web Backend (+ Database)](https://github.com/NUMde/compass-numapp-backend)
* [Downloader Script](https://github.com/NUMde/compass-numapp-downloader)

MIT

* [Web Frontend](https://github.com/NUMde/compass-numapp-web)

### Code of conduct

We follow the code of conduct defined by the [Contributor Covenant](https://www.contributor-covenant.org/version/2/0/code_of_conduct/).

---

## Über die NUM-App

[To version in English 🇬🇧](#about-the-num-app)

Die NUM-App ist ein Open-Source-Projekt und ermöglicht es, Studien auf Basis von Fragebögen digital durchzuführen. Hierzu werden eine Web-App und eine (native) mobile App bereitgestellt. Die NUM-App ist Teil des Projekts [COMPASS](https://num-compass.science/) (Coordination On Mobile Pandemic Apps Best Practice And Solution Sharing).

Die NUM-App unterstützt den internationalen Standard Fast Healthcare Interoperability Resources (FHIR) und ermöglicht das Anzeigen von [FHIR Questionnaires](https://www.hl7.org/fhir/questionnaire.html) sowie das verschlüsselte Versenden und Speichern der zugehörigen [FHIR Questionnaire Responses](https://www.hl7.org/fhir/questionnaireresponse.html).

## So funktioniert die NUM-App

Die NUM-App ermöglicht eine einfache und digitale Durchführung von Studien auf Basis von Fragebögen. Studienteilnehmende können Fragebögen direkt auf ihrem Mobilgerät oder im Browser ausfüllen und absenden.

Studienverantwortliche können eingereichte Antworten einfach abrufen und Fragebögen aktualisieren, ohne dass Studienteilnehmende die mobile App neu installieren oder aktualisieren müssen. Antworten aus den Fragebögen werden mit Ende-zu-Ende-Verschlüsselung an die empfangende Institution übermittelt, wodurch die NUM-App auch für medizinische Studien geeignet ist. Die App ist flexibel personalisierbar und kann für eigene Anforderungen angepasst werden.

Die Hauptvorteile der App sind:

* **Open Source**: Die App kann frei genutzt werden und alle können sich an der Entwicklung beteiligen.
* **Verwenden von Standards**: Die Verwendung des internationalen FHIR-Standards stellt die Kompatibilität der App sicher.
* **Community und Förderung**: Dank der Förderung durch das [Bundesministerium für Bildung und Forschung (BMBF)](https://www.bmbf.de/) ist die Arbeit unserer Community langfristig sichergestellt.
* **Praxisnähe**: Als [COMPASS-Projekt](https://num-compass.science/) im [NUM-Netzwerk](https://www.netzwerk-universitaetsmedizin.de/) wird unsere Community durch Fach- und Technikexperten unterstützt.
* **Einfachheit**: Die App kann auch ohne tiefes technisches Verständnis in kurzer Zeit aufgesetzt und angepasst werden.

## Verwenden der NUM-App

Die NUM-App hat folgende Komponenten:

1. [Mobile Frontend](https://github.com/NUMde/compass-numapp-frontend): Eine einfach zu verwendende mobile App (React Native), die FHIR Questionnaires dynamisch darstellen und informative Inhalte anzeigen kann.

2. [Web Frontend](https://github.com/NUMde/compass-numapp-web): Eine einfach zu verwendende Web-App (TypeScript), die FHIR Questionnaires dynamisch darstellen und informative Inhalte anzeigen kann.

3. [Mobile & Web Backend (+ Database)](https://github.com/NUMde/compass-numapp-backend): Backend-Komponente, welche die FHIR Questionnaires auf Basis des Nutzerkontexts bereitstellt und das Speichern der FHIR Questionnaire Responses verwaltet.

4. [Downloader Script](https://github.com/NUMde/compass-numapp-downloader): Komponente zum Abrufen und Entschlüsseln eingereichter FHIR Questionnaire Responses.

Um die Verwendung der App in vollem Umfang zu gewährleisten, muss mindestens ein Frontend, das Backend sowie das Downloader Script aufgesetzt werden. Dies umfasst die Bereitstellung von FHIR Questionnaires, die Speicherung der zugehörigen Antworten sowie deren Abruf.

Die Dokumentation der oben verlinkten Repositories bietet weitere Informationen zum Einrichten und Konfigurieren.

Allgemeine Inhalte (z.B. Verschlüsselung, Forking), welche übergreifend relevant sind, werden in den [Docs](https://github.com/NUMde/compass-numapp/tree/main/docs) erläutert.

Die Videoaufzeichnungen der Enabling-Termine sind auf [YouTube](https://www.youtube.com/channel/UC_JVfREe2bDR87dPjV7Y8og) verfügbar. Darüber hinaus gibt es eine Sammlung von weiterführenden Links zu [hilfreichen Informationsquellen](https://drive.google.com/file/d/17TCqD8hVgp68FOXxgf0y6n2ms1Q3IBX3/view).

<p align="center">
    <img src="assets/componentOverview.png" alt="Component Overview" width="600">
</p>

## Beispiel: COVID-19-Studie mit der NUM-App

Das folgende Beispiel zeigt, wie eine digitale (klinische) Studie mit der NUM-App durchgeführt wird. Wir betrachten dabei Max, der an der COVID-19-Studie einer Universitätsklinik teilnimmt.

<img src="assets/studyFlow_DE.png" alt="Visualization Study Flow" width="400" align="right">

### Schritt 1 - Login und erster Fragebogen

<div class="block">Max erhält von der Klinik einen personalisierten QR-Code zum Login bei der NUM-App. Ihm wird zunächst ein besonderer Fragebogen angezeigt, da dies seine erste Anmeldung bei der App ist. Der Startfragebogen enthält Fragen, die Max nur einmal beantworten soll. Max füllt den Fragebogen aus und schickt ihn ab. Die NUM-App wandelt den Fragebogen in eine FHIR Questionnaire Response um, verschlüsselt diese und sendet sie zum Speichern an das Backend.</div>

### Schritt 2 - Abfragen eingereichter Fragebögen

<div class="block">Das Studienpersonal am Universitätsklinikum möchte überprüfen, ob neue Fragebögen eingereicht wurden. Das Personal führt das Downloader Script aus und erhält die verschlüsselte Questionnaire Response von Max, welche lokal entschlüsselt wird.</div>

### Schritt 3 - Ausfüllen von Standardfragebögen

Das Studienpersonal hat die Frequenz für Fragebögen auf sieben Tage festgelegt. Max erhält daher jede Woche einen neuen Fragebogen. Nachdem er einen eingereicht hat, informiert ihn die NUM-App darüber, wann der nächste Fragebogen verfügbar ist. Da Max seine App nicht regelmäßig überprüft, schickt ihm die mobile NUM-App eine Push-Benachrichtigung, sobald ein neuer Fragebogen verfügbar ist. Das Studienpersonal hat die Benachrichtigungszeit auf 10:00 Uhr festgelegt. Daher erhält Max zu dieser Uhrzeit einmal jede Woche eine Benachrichtigung. Max füllt den Fragebogen nicht immer gleich vollständig aus, da dieser sehr lang ist. Da die NUM-App seine Antworten zwischenspeichert, kann Max den Fragebogen jederzeit weiter ausfüllen und fertigstellen.

### Schritt 4 - Antworten und alternative Fragebögen

Zu einem bestimmten Zeitpunkt beantwortet Max eine Frage des Standardfragebogens mit einem _Schlüsselwert_. In dieser Studie ist es die Information, dass Max positiv auf das Coronavirus getestet wurde. Die NUM-App erkennt dies und aktualisiert nach Absenden des Fragebogens  durch Max dessen Nutzerprofil automatisch auf Basis vorkonfigurierter Werte. Anstatt des Standardfragebogens erhält er nun einen alternativen Fragebogen. Zusätzlich wird die Häufigkeit des Fragebogens auf einmal pro Tag angehoben und die Verteildauer für den alternativen Fragebogen wird auf sieben Tage gesetzt. Das bedeutet, dass Max nun eine Woche lang täglich den neuen Fragebogen erhält. Danach werden die Einstellungen auf die Standardwerte zurückgesetzt.

### Schritt 5 - Einreichen von Sonderberichten

Max erhält wieder den Standardfragebogen. Er hat den aktuellsten bereits abgeschickt und muss nun sechs Tage auf den nächsten warten. Am folgenden Tag bemerkt Max allerdings COVID-19-Symptome und fordert einen Sonderbericht über die App an. Wieder wird sein Nutzerprofil aktualisiert. Max erhält nun einen Spezialfragebogen unabhängig von der üblichen Frequenz und kann seine Symptome über diesen Fragebogen eingeben. Danach erhält er wieder den Standardfragebogen, da nicht anders konfiguriert. In der Zwischenzeit hat das Studienpersonal jedoch die Frequenz der Fragebögen von sieben auf fünf Tage geändert. Daher erhält Max den Standardfragebogen nun alle fünf Tage.

### Schritt 6 - Abfragen eingereichter Fragebögen

Es ist eine Weile her, dass das Studienpersonal die eingereichten Fragebögen abgerufen hat. Das Personal führt das Downloader Script aus und erhält alle von Max versendeten Antworten seit der letzten Abfrage. Enthalten ist außerdem ein Eintrag zum Sonderbericht mit den Symptomen, den Max angefordert hat. Die entschlüsselten Antworten können nun je nach Anforderung verarbeitet werden.

## Mach mit!

Unsere Community lebt von deinem Engagement. Mach den ersten Schritt und tritt unserer [Meetup-Gruppe](https://www.meetup.com/de-DE/num-compass) bei und nehme an Events teil.

Gewinne einen Eindruck von unserer Arbeit und schau dir unsere Videos im [COMPASS YouTube Channel](https://www.youtube.com/channel/UC_JVfREe2bDR87dPjV7Y8og) an.

### NUM-App-Lizenzierung

Die NUM-App-Komponenten stehen unter der Apache 2.0- und MIT-Lizenz:

Apache 2.0

* [Mobile Frontend](https://github.com/NUMde/compass-numapp-frontend)
* [Mobile & Web Backend (+ Database)](https://github.com/NUMde/compass-numapp-backend)
* [Downloader Script](https://github.com/NUMde/compass-numapp-downloader)

MIT

* [Web Frontend](https://github.com/NUMde/compass-numapp-web)

### Verhaltenskodex

Wir halten uns an den Verhaltenskodex, der durch den [Contributor Covenant](https://www.contributor-covenant.org/version/2/0/code_of_conduct/) festgeschrieben wurde.
