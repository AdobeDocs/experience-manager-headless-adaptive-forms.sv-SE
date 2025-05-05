---
title: Bygg engagerande Forms med kärnkomponenter och headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Bygg engagerande Forms med kärnkomponenter och headless
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: bcc51bcae3b26cf20e7c0b5b75935bf69a991731
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 0%

---

# Bygg engagerande Forms med baskomponenter och Headless Adaptive Forms i AEM Forms as a Cloud Service {#build-engaging-forms-using-core-components-and-headless}

## Lab-översikt {#lab-overview}

I det här praktiska labbet lär du dig:

Hur man använder AEM Forms för att enkelt skapa anpassningsbara formulär med hjälp av de senaste kärnkomponenterna som är förenliga med AEM Sites, möjliggör datainhämtning i flera kanaler genom att leverera de adaptiva formulären som headless-formulär till webben, mobiler och chatt. Du får också lära dig de effektivaste strategierna när det gäller format, anpassningar och gränssnittsutveckling.

## Viktiga uppgifter {#key-takeaways}

* **Affärsflexibilitet**: Som affärsanvändare kan jag enkelt skapa formulärupplevelser för flera kanaler.

* **Framåtutvecklare**: Som klientutvecklare kan jag styra slutanvändarens upplevelse med headless-formulär.

* **Utvecklarhastighet**: Som utvecklare kan jag enkelt och konsekvent anpassa webbplatser och Forms-komponenter.

## Förutsättningar {#prerequisites}

Så här använder du händerna på labbet:

* Installera den [senaste versionen av Git](https://git-scm.com/downloads). Om du inte har använt Git tidigare läser du [Installera Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installera [Node.js 16.13.0 eller senare](https://nodejs.org/en/download/). Om du inte har använt Node.js tidigare läser du [Så här installerar du Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs).

* [Aktivera adaptiva Forms Core-komponenter](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) för din AEM Forms as a Cloud Service miljö.

* Installera [Microsoft Visual Studio Code](https://code.visualstudio.com/download) eller en vanlig textredigerare. Exempel i dokument använder Microsoft Visual Studio Code.



## Lektion 1 {#lesson-1}

### Syfte {#lesson-1-objectives}

Bekanta dig med AEM Forms as a Cloud Service miljö.

### Lektionssammanhang {#lesson-1-context}

I den här lektionen bekanta du dig med AEM Forms as a Cloud Service-miljön genom att navigera i användargränssnittet.

### Utövning {#lesson-1-excercise}

1. Öppna webbläsaren och ange webbadressen till Cloud Servicens författarmiljö. Till exempel:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Logga in i Cloud Servicens redigeringsmiljö.
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Om du vill navigera till användargränssnittet i AEM Forms klickar du på **Forms > Forms &amp; Documents**.



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Stäng alla popup-fönster som rör inställningar eller information. Alla tillgängliga formulär visas.


## Lektion 2

### Syfte

Skapa ett adaptivt formulär med hjälp av de senaste centrala komponenterna, konfigurera och skicka in formuläret.

### Lektionssammanhang

I den här lektionen kommer du som företagsanvändare att skapa ett anpassningsbart formulär för flera kanaler, som webben, mobiler och chatt, med hjälp av anpassningsbar formulärredigering och standardiserade OOTB-kärnkomponenter för datainhämtning.

### Utövning

1. Skapa en slutpunkt för överföring av formuläret:

   1. Öppna <https://requestbin.com/> på en ny webbläsarflik.
   1. Klicka på **Skapa en offentlig bin** och kopiera URL:en för slutpunkten.

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. Skapa ett anpassat formulär med hjälp av guidegränssnittet:

   1. Navigera till AEM Forms som Cloud Service och gå till Forms och Dokument på fliken Webbläsare som används i lektion 1.

      ![](/help/assets/screenshot2028114029.png)

   1. Klicka på **Skapa** och välj Adaptivt formulär.

      ![](/help/assets/screenshot2028114629.png)

   1. Välj mallen **Tom med kärnkomponenter** på mallvalsskärmen enligt nedan:

      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klicka på fliken **Format** och välj temat **wk-theme** så som visas nedan:

      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klicka på fliken **Överföring** och markera **Skicka till REST-slutpunktskortet** och ange det offentliga facket i fältet **URL för POST** enligt nedan:

      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klicka på **Skapa**. Ange ett namn och en rubrik för formuläret. Exempel: **registrering**. Klicka på **Skapa**.

   1. Den adaptiva formulärredigeraren öppnas. Stäng alla popup-fönster eller dialogrutor för inställningar eller information. Klicka på komponentwebbläsaren till vänster och lägg till komponenterna **Sidhuvud** och **Sidfot** i det tomma formulärets övre och nedre del.

      ![](/help/assets/screenshot2028121929.png)

   1. Dra och släpp komponenter från komponentwebbläsaren för att skapa ett formulär som liknar följande:

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. Lägg till valideringar i formuläret:

   1. Klicka på komponenten **Telefonnummer** så att snabbmenyn visas. Klicka på ikonen **Förnya** på menyn för att konfigurera fältet.

   1. Öppna fliken **valideringar**, markera fältet **Obligatoriskt** och klicka på **Klar**. Meddelandet om att åtgärden lyckades visas.

      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. Förhandsgranska och skicka formuläret.

   1. Klicka på **Förhandsgranska** om du vill förhandsgranska formuläret från ett slutanvändarperspektiv.

   1. Fyll i formuläret med provdata.

   1. Skicka formuläret.

      ![](/help/assets/screenshot2028125729.png)

   1. Kontrollera skickade data på fliken Begäranbehållare.

      ![](/help/assets/screenshot2028125829.png)

1. Lägg till interaktivitet i formulär med regler:

   1. Klicka på rutan **Markera om du vill få 5 % rabatt**. Klicka på ikonen Regler i alternativverktygsfältet. Alternativet Regelredigerare öppnas.

   1. Skapa en regel när alternativet **Markera kryssrutan för att få 5 % rabatt** är markerat inaktiveras alternativen för att använda kreditkort.

1. Publish blanketten.

   1. Öppna AEM Forms hanteringsgränssnitt, till exempel `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, och välj formuläret.

   1. Klicka på **Publish**.

      ![](/help/assets/screenshot2028115629.png)

      Meddelandet om att åtgärden lyckades visas.

      ![](/help/assets/screenshot2028115729.png)

      Publicerings-URL:en för formuläret liknar `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

   1. Om du vill visa det publicerade formuläret ska du ersätta program-ID:t (pXXXXXX) och miljö-ID:t (eXXXXXX) i ovanstående URL med ID:n för
miljö.

## Lektion 3

### Syfte

Uppdatera format med hjälp av vedertagna metoder för utveckling av klientprogram.

### Lektionssammanhang

I den här lektionen lär du dig hur du enkelt kan uppdatera formateringen för det tidigare skapade adaptiva formuläret.

### Utövning

Konfigurera lokal databas för temat:

1. Öppna kommandotolken eller kommandotolken med administratörsbehörighet:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till mappen **c:\git**

   ```Shell
   cd c:\git
   ```

1. Använd följande kommando för att klona koden för temat Framtend:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Använd följande kommando i den angivna ordningen för att navigera till katalogen **aem-forms-theme-canvas** och öppna Visual Studio-kod.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. Välj **Lita på författarna till alla filer i den överordnade mappen** och klicka på **Ja, jag litar på författarna**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Om du vill återge formuläret som finns i molntjänstens publiceringsmiljö byter du namn på filen `env_template`.  Om du vill byta namn på filen högerklickar du på filen **env_template** och väljer alternativet **Byt namn** .

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Ange följande värden för variablerna i .env-filen och spara filen:

   * **AEM_URL**: Ange molntjänstens publiceringsmiljö. Exempel: `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Ange sökvägen för formuläret. Om formulärsökvägen till exempel är `/content/forms/af/registration` blir värdet för den här variabeln `registration`.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. Skapa en lokal användare i AEM.

   >[!NOTE]
   > Så här skapar du en lokal användare:
   > Gå till `AEM Home` > `Tools` > `Security` > `Users`
   > Se till att användaren är medlem i gruppen för användare av formulär.


1. Kör följande kommando i kommandotolken:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Om du får ett meddelande som ber om att uppdatera npm via kommandot `npm notice Run npm nstall -g npm@9.6.0`, ska du ignorera meddelandet.
   > * Kör inte andra npm-kommandon om inte annat anges i arbetsboken.

1. Kör nu följande kommando för att förhandsgranska formuläret.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   När ovanstående kommando har körts väntar du på meddelandet `webpack compiled` och du omdirigeras till en AEM inloggningssida.

1. Klicka på **Logga in lokalt (endast administrationsuppgifter)** på AEM inloggningssida.
1. Ange inloggningsuppgifterna för den skapade lokala användaren och formuläret visas på en webbläsarflik.

   >[!NOTE]
   >
   >Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm run live` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. Öppna filen `PROJECT\src\site\_variables.scss` i Visual Studio Code. Observera att färgen `$error` är en skugga av RED.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Skicka formuläret i webbläsaren för att se den röda färgen i fältet **Förnamn**.

   ![](/help/assets/screenshot2028120829.png)

1. Ställ in färgen **$error** på **#5736eb** och spara filen.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Uppdatera webbläsaren och skicka formuläret. Observera att felfärgen i förnamnsfältet har ändrats därefter.

   ![](/help/assets/screenshot2028121129.png)

1. I kommandotolken trycker du på **CTRL+C**, anger **Y** och trycker på **Enter** för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.
1. Stäng fönster för Visual Studio-kod och kommandotolk.

## Lektion 4

### Syfte

Rendera formuläret till webb-/mobilgränssnitt och andra gränssnitt som en headless-form.

### Lektionssammanhang

I den här lektionen får du som frontutvecklare lära dig hur du kan återge den adaptiva formen som tidigare skapats som en headless-form med hjälp av ett ramverk för reaktionsspektrumdesign.

### Utövning

Konfigurera lokal databas med hjälp av ett reaktionsstartprojekt:

1. Öppna kommandotolken med administratörsbehörighet.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till mappen **c:\git**

   ```Shell
   cd c:\git
   ```

1. Använd följande kommando för att klona startprojektet för adaptiv formulärreaktion:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Använd följande kommandon i den listade ordningen för att navigera till katalogen **rea-starter-kit-aem-headless-forms** och öppna Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Fönstret Visual Studio Code öppnas.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Så här återger du formuläret som finns i molntjänstens publiceringsmiljö:

1. Byt namn på filen env_template till .env. Om du vill byta namn högerklickar du på filen **env_template** och väljer alternativet **Byt namn** .

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna.

   * **AEM_URL**: Ange URL:en för molntjänstens publiceringsmiljö. Exempel: `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Ange sökvägen för det adaptiva formuläret som skapades i föregående lektion. Exempel: `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Öppna kommandofönstret, kontrollera att du befinner dig i katalogen response-starter-kit-aem-headless-forms och kör följande kommando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Kör följande kommando i kommandotolken:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   Ovanstående kommando startar en lokal utvecklingsserver som skulle återge formulärdefinitionen som hämtats från AEM på ett headless sätt med hjälp av frontend-biblioteket för reaktionsspektrum.

   >[!NOTE]
   >
   > 
   > Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm start` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.

   ![](/help/assets/screenshot2028118229.png)

Låt oss kontrollera hur reglerna verkställs i den här rubrikfria formen:

1. Markera kryssrutan **Markera kryssrutan för att få 5 % rabatt**. Det efterföljande alternativet för att använda kreditkort är inaktiverat.

   ![](/help/assets/screenshot2028126229.png)

1. Avmarkera **Markera kryssrutan för att få 5 % rabatt** för att aktivera kreditkortsalternativet.

   ![](/help/assets/screenshot2028126329.png)

Låt oss göra ändringar i formuläret på servern som företagsanvändare och automatiskt se ändringarna som återspeglas i det headless-formuläret.

1. Öppna AEM Forms gränssnitt i webbläsaren. Exempel: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Markera formuläret **kontakter** och klicka på **Redigera.** Formuläret öppnas i redigeraren för anpassade formulär.


1. Markera fältet **Telefonnummer** och klicka på ikonen **Redigera (pennikonen)** i verktygsfältet. Om du inte kan se popup-verktygsfältet växlar du till redigeringsläget genom att klicka på knappen **Redigera** längst upp till höger, vänster till knappen **Förhandsgranska** .

   ![](/help/assets/screenshot2028119629.png)

1. Ändra etiketten till Mobilnummer. Klicka på ett tomt utrymme i formuläret så sparas ändringarna i formuläret.

   ![](/help/assets/screenshot2028119729.png)

Låt oss publicera det uppdaterade formuläret för att sprida ändringarna till publiceringsmiljön.

1. Markera registreringsformuläret på fliken för AEM Forms-hanteringsgränssnittet och klicka på **Avpublicera**. Om knappen **Avpublicera** inte visas går du vidare till steg 3 och publicerar ändringarna direkt.

1. Klicka på **Avpublicera**. Klicka på **Stäng** i respektive dialogruta.

1. När webbläsaren har uppdaterats markerar du registreringsformuläret och klickar på **Publish**.

1. Klicka på **Publish**. Klicka på **Stäng** i respektive dialogruta.

1. Uppdatera webbläsarfliken med det headfria formuläret synligt. Observera att telefonnummeretiketten har ändrats till Mobilnummer.

   ![](/help/assets/screenshot2028120529.png)

1. Öppna fönstret Kommandotolk som används för att starta projektet **responsstarter-kit-aem-headless-forms**, tryck på **CTRL+C** och sedan
ange **Y** och tryck på Retur för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.

1. Stäng fönster för Visual Studio-kod och kommandotolk.


## Lektion 5

### Syfte

Rendera formuläret som ett headless-formulär med Google Material UI

### Lektionssammanhang

I den här lektionen lär du dig att återge den adaptiva formen som tidigare skapats som ett headless-formulär med Google Material UI.

### Utövning

Konfigurera lokal databas med hjälp av huvudanvändargränssnittets startprojekt:

1. Öppna kommandotolken med administratörsbehörighet.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. Använd följande kommando på kommandotolken för att navigera till mappen **c:\git**:

   ```Shell
   cd c:\git
   ```

1. Kör följande kommandon i den angivna ordningen för att skapa en mapp med namnet mui och navigera till multimappen med följande kommandon:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Använd följande kommando för att klona startprojektet för adaptiv formulärreaktion:

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Använd följande kommando i den listade ordningen för att navigera till mappen **response-starter-kit-aem-headless-forms** och öppna koden i Visual Studio-koden:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Så här återger du formuläret som finns i molntjänstens publiceringsmiljö:

1. Byt namn på filen **env_template** till filen **.env**. Om du vill byta namn högerklickar du på filen **env_template** och väljer **Byt namn**.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna. Använd växlingskombinationen **CTRL + S** för att spara filen.

   * **AEM_URL**: Ange URL:en för molntjänstens publiceringsmiljö. Exempel: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Ange sökvägen för det adaptiva formuläret som skapades i föregående lektion. Till exempel /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. Öppna kommandofönstret, kontrollera att du är i katalogen **reak-starter-kit-aem-headless-forms** och kör följande kommando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Kör följande kommando i kommandotolken:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   Kommandot startar en lokal utvecklingsserver och återger formulärdefinitionen som hämtats från AEM på ett headless sätt med Google
Gränsbibliotek för materialgränssnitt.

   >[!NOTE]
   >
   >Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm start` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.

   ![](/help/assets/screenshot2028127229.png)

1. Så här utvärderar du körningen av samma affärslogik i den här formuläråtergivningen:

   Markera kryssrutan **om du vill få 5 % rabatt**. Det efterföljande alternativet **Vill du ansöka om kreditkortsformulär för Web.Finance Corporate?** inaktiveras.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## Lektion 6

### Syfte

Skapa ett alternativt utseende och känsla för den headless-formen med materialvariationer för UI-komponenter

### Lektionssammanhang

I den här lektionen lär du dig som gränssnittsutvecklare hur du skapar en alternativ representation av olika komponenter med hjälp av materialgränssnittet för det adaptiva formulär som tidigare skapats av företagsanvändaren.

### Utövning

Uppdatera variationen av komponenterna i det headless-projektet. Så här ändrar du varianten för textindatakomponenten i användargränssnittet till `OutlinedInput`:

1. I Visual Code navigerar du till textindatakomponenten genom att öppna filen `index.tsx` på `src/components/textinput/index.tsx`.

1. Lägg till `//` i början av kodraden 103. Raden konverteras till en kommentar.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Lägg till följande på rad 104 om du vill använda en annan variant av komponenten och spara filen. Använd växlingskombinationen **CTRL + S** för att spara filen.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   Det är viktigt att använda korrekt skiftläge för &#39;OutlinedInput&#39;-varianten, annars misslyckas kompileringen. Kompileringen av den lokala utvecklingsmiljön startar automatiskt i kommandotolken. Vänta tills följande meddelande visas

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Uppdatera webbläsaren, om den inte uppdateras automatiskt, för att se hur textindatakomponenten använder en annan variant.

   ![](/help/assets/screenshot2028127729.png)


   Den här ändringen sker för slutanvändare utan att formulärdefinitionen på AEM Forms Server ändras och gäller specifikt för headless
den aktuella kanalen. Webbkanal i det här labbet.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Stäng Visual Studio-kod och kommandotolken i Windows.

## Vanliga frågor och svar

+++ Är guiden Adaptiv blankett tillgänglig offentligt?

Ja, det finns med AEM Forms som Cloud Service.

+++


+++ Är kärnkomponenterna tillgängliga för allmänheten?

Ja, de adaptiva kärnkomponenterna i Forms finns tillgängliga med AEM Forms som Cloud Service.

+++

+++ Är headless-formulär tillgängliga för allmänheten?

Ja, formulär utan rubrik finns med AEM Forms som Cloud Service.

+++

+++ Kräver Headless-formulär en separat licens?

Nej, Headless-formulär använder samma licensvärde, antal formulärinskickade formulär.

+++

+++ Finns kärnkomponenter och headless-formulär med AEM 6.5 Forms?

Ja, både adaptiva formulär och headless-komponenter finns tillgängliga med AEM Forms 6.5 Service Pack 16 och senare.

+++


## Nästa steg

Nu när ni har lärt er att skapa anpassningsbara formulär och leverera dem till flera kanaler med hjälp av headless-formulär, bör ni försöka att använda era nya kunskaper i praktiken. Ha kul och gör det bara genom att skapa och leverera enastående datainhämtningsupplevelser till slutanvändarna, var de än är, i stor skala!

## Resurser

* [Introduktion till kärnkomponenter i adaptiva formulär](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=sv-SE)

* [Skapa anpassat formulär med kärnkomponenter](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Uppdatera format för grundkomponentbaserad AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=sv-SE)

* [Headless adaptive forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=sv-SE)

* [Använder startkit för Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=sv-SE)
