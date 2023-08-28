---
title: Konfigurera utvecklingsmiljö för en Forms as a Cloud Service Sandbox
description: Konfigurera utvecklingsmiljö för en Forms as a Cloud Service Sandbox
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 0%

---

# Konfigurera utvecklingsmiljö för Headless adaptive forms på Cloud Service

<span class="preview"> Det här är en **PÅGÅENDE ARBETE** artikel.</span>


Är du redo att skapa och testa Headless-anpassade formulär på Cloud Servicen? Aktivera Forms för er Cloud Service och komma igång.

## Innan du börjar

* Installera [Senaste versionen av Git](https://git-scm.com/downloads) på din lokala dator. Om du inte har använt Git tidigare kan du läsa [Installerar Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Du använder Git-databasen för att skicka formulären och den anpassade koden som utvecklats i den lokala utvecklingsmiljön till Cloud Servicens utvecklingsmiljö.

* Installera [Node.js 16.13.0 eller senare](https://nodejs.org/en/download/) på din lokala dator. Om du inte har använt Node.js tidigare, se [Så här installerar du Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* Skapa ett AEM as a Cloud Service program: Följ steg 1-7 i [skapa program](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program) artikel för att skapa ett program för din organisation.

* Aktivera [Förhandslanseringskanal för Cloud Servicen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?cloud-environments).

## Konfigurera arbetsflöde

Aktivera Headless-anpassade formulär på din Forms as a Cloud Service sandlåda `Forms - Digital enrolment` för ditt AEM Cloud Service-program, skapa ett Archetype 37-projekt eller senare baserat på din dator och skicka det vidare till din as a Cloud Service Forms-miljö. Hela processen är:

![Arbetsflöde för att konfigurera utvecklingsmiljö för en Forms as a Cloud Service Sandbox](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### 1. Aktivera Forms för programmet

<table style="table-layout:auto">
<tr>
  <td>
  1. Logga in på <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>  och väljer <b> Experience Manager </b> alternativ.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. För <b> Cloud Manager </b> alternativ, klicka <b> Starta. </b> En lista över program för din organisation visas.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. För ditt program trycker du på ...-ikonen och väljer <b> Redigera program </b> alternativ. En dialogruta visas. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    4. I dialogrutan Redigera program går du till <b> Fliken Lösningar och tillägg </b>väljer du <b> Forms - digital registrering </b> och tryck <b> uppdatera </b>. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### 2. Klona Git-databasen för ditt program till din lokala dator

Alla AEM as a Cloud Service program har en Git-databas. Med den kan du överföra anpassad kod och resurser från den lokala datorn till din Cloud Service. Under installationen använder vi Git-databasen för att ta med kod, mallar och annan information för Headless-formulär från din lokala Cloud Service. Klona Cloud Servicens Git-databas på den lokala datorn är det första steget mot att överföra anpassad kod och innehåll från den lokala datorn till Cloud Servicen.

>[!INFO]
>
> Du kan alltid implementera en Git-databas utan att klona den. Men den har sina egna frågetecken. Vi använder kloningsmetoden i det här dokumentet.


Så här klonar du databasen:

<table style="table-layout:fixed">
<tr>
  <td>
  1. Tryck på <b> Få åtkomst till svarsinformation. </b> En dialogruta med databasinformation visas 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Tryck <b> Generera lösenord </b> och kopiera <b> Databas-URL. </b> 
  </td>
  <td>
      <img alt="AEM as a Cloud Service program" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Öppna kommandotolken på den lokala datorn, skapa en mapp och kör följande kommando och ange databasens autentiseringsuppgifter. Fråga:
    </br>
    <code> git clone [Repository URL] </code> </br></br>
    Till exempel: </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br> När du blir tillfrågad kan du <b> Användarnamn</b> och <b>Lösenord</b> från <b>Databasinformation</b> skärm.
</td>
  <td>
     <img alt="AEM as a Cloud Service program" src="assets/clone-success.png">
  </td>
</tr>
</table>


### 3. Skapa ett AEM Archetype-baserat projekt

Arketype-projektet är en maven-baserad mall. Det skapar ett minimalt projekt baserat på bästa praxis för att komma igång med Headless-anpassade formulär. Den innehåller även basfunktioner för Headless-anpassade formulär för Forms as a Cloud Service. Det är obligatoriskt att skapa och distribuera det arkitekturbaserade projektet 37 eller senare.
®® Beroende på vilket operativsystem du har kan du köra kommandot maven för att skapa ett as a Cloud Service Experience Manager Forms-projekt. Använd arketype version 37 eller senare. Se [Arketype-dokumentation](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) för att hitta den senaste versionen av Archetype.

+++ Microsoft® Windows

1. Öppna kommandotolken med administratörsbehörighet (Kör kommandotolken eller bash-skalet som administratör).
1. Kör kommandot nedan:

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
     -D archetypeGroupId=com.adobe.aem ^
     -D archetypeArtifactId=aem-project-archetype ^
     -D archetypeVersion=37 ^
     -D appTitle=myheadlessform ^
     -D appId=myheadlessform ^
     -D groupId=com.myheadlessform ^
     -D includeFormsenrollment="y" ^
     -D includeFormsheadless="y" 
   ```

™™ * Ställ in `appTitle` för att definiera titel- och komponentgrupper.
* Uppsättning `appId` för att definiera Maven artifactId, komponentens, konfigurations- och innehållsmappens namn samt klientbibliotekens namn.
* Uppsättning `groupId` för att definiera Maven groupId och Java™ Source Package.
* Använd `includeFormsenrollment=y` om du vill inkludera Forms-specifika konfigurationer, teman, mallar, kärnkomponenter och beroenden som krävs för att skapa Adaptiv Forms.
* Använd `includeFormsheadless=y` om du vill inkludera Forms Core-komponenter och beroenden som krävs för att inkludera funktionen för Headless-anpassade formulär. När du aktiverar det här alternativet ingår följande:\
* **Tom med kärnkomponenter** mall med [kärnkomponenter](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).
* En modul för frontinslag, `ui.frontend.react.forms.af`. Det hjälper dig att återge Headless-formulär i en responsapp.

+++®®


+++ Apple macOS eller Linux®

1. Öppna terminalen som rotanvändare. Det gör att du kan köra kommandon med administratörsbehörighet. Du kan också använda `sudo root` när du har öppnat terminalfönstret för att köra kommandon med administratörsbehörighet.
1. Kör kommandot nedan:

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
     -D archetypeGroupId=com.adobe.aem \
     -D archetypeArtifactId=aem-project-archetype \
     -D archetypeVersion=37 \
     -D appTitle=myheadlessform \
     -D appId=myheadlessform \
     -D groupId=com.myheadlessform \
     -D includeFormsenrollment="y" \
     -D includeFormsheadless="y"  
   ```

™™ * Ställ in `appTitle` för att definiera titel- och komponentgrupper.
* Uppsättning `appId` för att definiera Maven artifactId, komponenten, config, innehållsmappnamn och klientbiblioteksnamn.
* Uppsättning `groupId` för att definiera Maven groupId och Java™ Source Package.
* Använd `includeFormsenrollment=y` om du vill inkludera Forms-specifika konfigurationer, teman, mallar, kärnkomponenter och beroenden som krävs för att skapa Adaptiv Forms.
* Använd `includeFormsheadless=y` om du vill inkludera Forms Core-komponenter och beroenden som krävs för att inkludera funktionen för Headless-anpassade formulär. När du aktiverar det här alternativet ingår följande:\
* **Tom med kärnkomponenter** mall med [kärnkomponenter](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).
* En modul för frontinslag, `ui.frontend.react.forms.af`. Det hjälper dig att återge Headless-formulär i en responsapp.

+++

När kommandot är klart skapas en projektmapp med namnet som anges i `appID` skapas. Om du till exempel använder `appID` med värde `myheadlessform`, en mapp med namnet `myheadlessform` skapas. Det innehåller det Arketype-baserade projektet.

### 4. Skicka det AEM Arketype-baserade projektet till Cloud Servicen

1. Ersätt Git-databasens innehåll med innehållet i ett Archtype-baserat projekt.

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. Öppna kommandotolken, navigera till din Git-databasmapp och kör nedanstående kommandon i den ordning som visas för att överföra det ersatta innehållet till din Cloud Service-miljö. Du kan också använda en visuell redigerare i stället för att använda kommandona nedan för att överföra innehåll till Cloud Servicens databas.

   ```
      git add .
      git commit
      git push origin
   ```

### 5. Kör byggpipeline för ditt program



<table style="table-layout:auto">
<tr>
  <td>
  1. Logga in på <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>  och väljer <b> Experience Manager </b> alternativ.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. För <b> Cloud Manager </b> alternativ, klicka <b> Starta. </b> En lista över program för din organisation visas. Öppna programmet. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. För din pipeline trycker du på ...-ikonen och väljer <b> Kör </b> alternativ. Tryck på om du uppmanas att köra pipeline <b> Kör </b> och vänta på pipeline <b> Status </b>  att ändra till <b> Slutförd </b>.  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM as a Cloud Service program" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

Nu kan du börja använda Headless-formulär. Du kan nu överföra JSON-definitionen för ett formulär till din Cloud Service-miljö, skapa ett Headless-anpassat formulär baserat på den och använda [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm) och andra övriga API:er för att använda det Headless-anpassade formuläret i programmet eller tjänsten.
