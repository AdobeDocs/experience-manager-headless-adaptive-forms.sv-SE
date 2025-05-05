---
title: Bygg engagerande Forms med kärnkomponenter och headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Bygg engagerande Forms med kärnkomponenter och headless
seo-description: Build Engaging Forms Using Core Components and Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '2130'
ht-degree: 0%

---

# Bygg engagerande Forms med kärnkomponenter och Headless Adaptive Forms på AEM 6.5 Forms {#build-engaging-forms-using-core-components-and-headless}

## Lab-översikt {#lab-overview}

I det här praktiska labbet lär du dig:

Så här använder du AEM Forms för att enkelt skapa adaptiva Forms med hjälp av de senaste Core-komponenterna som är kompatibla med AEM Sites, vilket möjliggör datainhämtning i flera kanaler genom att leverera det adaptiva Forms som headless-formulär till webben, mobiler och chatt. Du får också lära dig de effektivaste strategierna när det gäller format, anpassningar och gränssnittsutveckling.

## Viktiga uppgifter {#key-takeaways}

* **Affärsflexibilitet**: Som affärsanvändare kan jag enkelt skapa formulärupplevelser för flera kanaler.

* **Framåtutvecklare**: Som klientutvecklare kan jag styra slutanvändarens upplevelse med headless-formulär.

* **Utvecklarhastighet**: Som utvecklare kan jag enkelt och konsekvent anpassa webbplatser och Forms-komponenter.

## Innan du börjar {#pre-requisites}

Så här använder du händerna på labbet:

* Installera den [senaste versionen av Git](https://git-scm.com/downloads). Om du inte har använt Git tidigare läser du [Installera Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installera [Node.js 16.13.0 eller senare](https://nodejs.org/en/download/). Om du inte har använt Node.js tidigare läser du [Så här installerar du Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [Aktivera Headless Adaptive Forms](enable-headless-adaptive-forms-and-core-components.md) i din Forms-miljö AEM 6.5.

* Installera [Microsoft Visual Studio Code](https://code.visualstudio.com/download) eller en vanlig textredigerare. Exempel i dokument använder Microsoft Visual Studio Code.

## Lektion 1 {#lesson-1}

### Syfte {#lesson-1-objectives}

Bekanta dig med AEM 6.5 Forms-miljö.

### Lektionssammanhang {#lesson-1-context}

I den här lektionen bekanta du dig med AEM 6.5 Forms genom att navigera i användargränssnittet.

### Utövning {#lesson-1-excercise}

1. Öppna webbläsaren och ange webbadressen till författarmiljön. Till exempel:
   [https://localhost:4502](https://localhost:4502).

1. När du är inloggad navigerar du till användargränssnittet för AEM Forms. Klicka på **Forms**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Klicka på **Forms &amp; Documents**. Stäng alla popup-fönster som rör inställningar eller information.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Alla tillgängliga formulär visas.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## Lektion 2

### Syfte

Skapa ett adaptivt formulär med hjälp av de senaste kärnkomponenterna, konfigurera och skicka in formuläret.

### Lektionssammanhang

I den här lektionen, som företagsanvändare, skapar du ett adaptivt formulär för flera kanaler som webben, mobiler och chatt med adaptiv Forms-redigerare med standardiserade färdiga kärnkomponenter för att hämta in data.

### Utövning

1. Skapa en slutpunkt för överföring av formuläret:

   1. Öppna <https://requestbin.com/> på en ny webbläsarflik.

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Klicka på **Skapa en offentlig bin** och kopiera URL:en för slutpunkten.

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Den här särskilda slutpunkten fungerar som ett exempel för att skicka och visa data. I den faktiska produktionen använder du din egen slutpunkt eller datakällor för att lagra hämtade data.

1. Skapa ett anpassat formulär:

   1. Navigera till AEM Forms webbgränssnitt och gå till **Forms** > **Forms och dokument** på fliken för webbläsare som används i lektion 1.

   1. Klicka på **Skapa** och välj Adaptivt formulär.

      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Välj mallen **Tom med kärnkomponenter** på mallvalsskärmen som visas nedan och klicka på **Nästa**.

      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Ange `Contact us` som **rubrik** för formuläret. Kontrollera att formulärets **namn** är `contact-us`.

      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Klicka på **Skapa**. En dialogruta visas.

   1. Klicka på **Redigera** i dialogrutan. Formuläret öppnas i Adaptiv formulärredigerare. Stäng alla popup-fönster eller dialogrutor för inställningar eller information.

   1. Öppna webbläsaren Komponenter och dra och släpp panelkomponenten mitt på skärmen.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Dra och släpp komponenter från komponentwebbläsaren för att skapa ett formulär som liknar följande:

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Öppna Content Browser, klicka på egenskapsikonen för Guide Container och öppna fliken **Submission** . Markera **Skicka till REST-slutpunkten** Skicka-åtgärden, markera alternativet **Aktivera begäran om POST** och ange REST-slutpunkten som skapades i lektion 2 i textrutan **URL för begäran om POST**. Klicka sedan på ikonen **Klar** .

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publish och adaptiv form:

   1. Öppna AEM, navigera till **Forms** > **Forms &amp; Documents**. Markera formuläret som skapades i föregående steg och klicka på **Publish**.

   1. Klicka på **Publish** i dialogrutan Publish Assets. Meddelandet om att åtgärden lyckades visas.

## Lektion 3

### Syfte

Uppdatera format med hjälp av vedertagna metoder för utveckling av klientprogram.

### Lektionssammanhang

I den här lektionen lär du dig hur du enkelt kan uppdatera format för tidigare skapade adaptiva formulär.

### Utövning

Konfigurera lokal databas för temat:

1. Öppna kommandotolken eller kommandotolken med administratörsbehörighet:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till mappen `c:\git`.

   ```Shell
   cd git
   ```

   Om mappen inte finns skapar du den med kommandot `md git`.

1. Använd följande kommando för att klona koden för temat Framtend:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Använd följande kommando i den angivna ordningen för att navigera till katalogen **aem-forms-theme-canvas** och öppna Visual Studio-kod.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Välj **Lita på författarna till alla filer i den överordnade mappen** och klicka på **Ja, jag litar på författarna**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Byt namn på filen `env_template` till .env.  Om du vill byta namn på filen högerklickar du på filen **env_template** och väljer alternativet **Byt namn** .

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Ange följande värden för variablerna i .env-filen och spara filen:

   * **AEM_URL**: Ange URL för en **publish**-instans. Exempel: `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: Ange formulärets namn. Exempel: `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


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

   När ovanstående kommando har körts väntar du på meddelandet `webpack compiled`. Formuläret visas på en webbläsarflik.

   >[!NOTE]
   >
   >Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm run live` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. Öppna filen `PROJECT\src\site\_variables.scss` i Visual Studio Code. Observera att färgen `$error` är en skugga av RED.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Skicka formuläret i webbläsaren för att se den röda färgen i fältet **Förnamn**.

   ![](/help/assets/error-color-before.png)

1. Ställ in färgen **$error** på **#5736eb** och spara filen.

1. Uppdatera webbläsaren och skicka formuläret. Observera att felfärgen i förnamnsfältet har ändrats därefter.

   ![](/help/assets/error-color-after.png)

1. I kommandotolken trycker du på **CTRL+C**, anger **Y** och trycker på **Enter** för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.
1. Stäng fönster för Visual Studio-kod och kommandotolk.

## Lektion 4

### Syfte

Rendera formuläret till webb-/mobilgränssnitt och andra gränssnitt som en headless-form.

### Lektionssammanhang

I den här lektionen får du lära dig hur du kan återge den adaptiva formen som du skapat tidigare som en headless form med hjälp av ett ramverk för reaktionsspektrumdesign.

### Utövning

Konfigurera lokal databas med hjälp av ett reaktionsstartprojekt:

1. Öppna kommandotolken med administratörsbehörighet.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till mappen `c:\git`.

   ```Shell
   cd git
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

Så här återger du formuläret som finns i publiceringsmiljön:

1. Byt namn på filen env_template till .env. Om du vill byta namn högerklickar du på filen **env_template** och väljer alternativet **Byt namn** .

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna.

   * **AEM_URL**: Ange URL-adressen för publiceringsmiljön. Exempel: `https://localhost:4503/`

   * **AEM_FORM_PATH**: Ange sökvägen för det adaptiva formuläret som skapades i föregående lektion. Exempel: `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Öppna kommandofönstret, kontrollera att du är i katalogen **reak-starter-kit-aem-headless-forms** och kör följande kommando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Kör följande kommando i kommandotolken:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   Ovanstående kommando startar en lokal utvecklingsserver som skulle återge formulärdefinitionen som hämtats från AEM på ett headless sätt med hjälp av frontend-biblioteket för reaktionsspektrum.

   >[!NOTE]
   >
   > 
   > Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm start` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Låt oss göra ändringar i formuläret på servern som företagsanvändare och automatiskt se ändringarna som återspeglas i det headless-formuläret.

1. Öppna AEM Forms gränssnitt i webbläsaren. Exempel: [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Markera formuläret **Kontakta oss** och klicka på **Redigera.** Formuläret öppnas i Adaptiv Forms-redigerare.


1. Markera fältet **Kontaktnummer** och klicka på ikonen **Redigera (pennikon)** i verktygsfältet. Om du inte kan se popup-verktygsfältet växlar du till redigeringsläget genom att klicka på knappen **Redigera** längst upp till höger, vänster till knappen **Förhandsgranska** .

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Ändra etiketten till **Mobilnummer**. Klicka på ett tomt utrymme i formuläret så sparas ändringarna i formuläret.

Låt oss publicera det uppdaterade formuläret för att sprida ändringarna till publiceringsmiljön.

1. Markera kontaktformuläret på fliken för AEM Forms-hanteringsgränssnittet och klicka på **Avpublicera**. Om knappen **Avpublicera** inte visas går du vidare till steg 3 och publicerar ändringarna direkt.


1. Klicka på **Avpublicera**. Klicka på **Stäng** i respektive dialogruta.

1. När webbläsaren har uppdaterats markerar du kontaktformuläret och klickar på **Publish**.


1. Klicka på **Publish**. Klicka på **Stäng** i respektive dialogruta.

1. Uppdatera webbläsarfliken med det headfria formuläret synligt. Observera att etiketten Kontaktnummer har ändrats till Mobilnummer.

   ![](/help/assets/headless-adaptive-form.png)

1. Öppna fönstret Kommandotolk som används för att starta projektet **responsstarter-kit-aem-headless-forms**, tryck på **CTRL+C** och sedan
ange **Y** och tryck på Retur för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.

1. Stäng fönster för Visual Studio-kod och kommandotolk.


## Lektion 5

### Syfte

Rendera formuläret som ett headless-formulär med Google Material UI

### Lektionssammanhang

I den här lektionen lär du dig att återge den adaptiva formen som tidigare skapats som en headless-form med Google Material UI.

### Utövning

Konfigurera lokal databas med hjälp av huvudanvändargränssnittets startprojekt:

1. Öppna kommandotolken med administratörsbehörighet.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till mappen `c:\git`.

   ```Shell
   cd git
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

Så här återger du formuläret som finns i publiceringsmiljön:

1. Byt namn på filen **env_template** till filen **.env**. Om du vill byta namn högerklickar du på filen **env_template** och väljer **Byt namn**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna. Använd växlingskombinationen **CTRL + S** för att spara filen.

   * **AEM_URL**: Ange URL-adressen för publiceringsmiljön. Exempel: [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: Ange sökvägen för det adaptiva formuläret som skapades i föregående lektion. Till exempel /content/forms/af/contact-us/


1. Öppna kommandofönstret, kontrollera att du är i katalogen **reak-starter-kit-aem-headless-forms** och kör följande kommando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Kör följande kommando i kommandotolken:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   Kommandot startar en lokal utvecklingsserver och återger formulärdefinitionen som hämtats från AEM utan rubrik med hjälp av Google materialgränssnittets bibliotek i förgrunden.

   >[!NOTE]
   >
   >Om du får en tom skärm i webbläsaren efter att ha kört kommandot `npm start` i mer än 3-4 minuter ändrar du `localhost` i webbläsarens URL till 127.0.0.1 och trycker på **Retur**.

   ![](/help/assets/google-mui-form.png)

## Lektion 6

### Syfte

Skapa ett alternativt utseende och känsla för den headless-formen med materialvariationer för UI-komponenter

### Lektionssammanhang

I den här lektionen lär du dig som gränssnittsutvecklare hur du skapar en alternativ representation av olika komponenter med hjälp av materialgränssnittet för det adaptiva formuläret som skapats tidigare av företagsanvändaren.

### Utövning

Uppdatera variationen av komponenterna i det headless-projektet. Så här ändrar du varianten för textindatakomponenten i användargränssnittet till `OutlinedInput`:

1. I Visual Code navigerar du till textindatakomponenten genom att öppna filen `index.tsx` på `src/components/textinput/index.tsx`.

1. Lägg till `//` i början av kodraden 104. Raden konverteras till en kommentar.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Lägg till följande på rad 105 om du vill använda en annan variant av komponenten och spara filen. Använd växlingskombinationen **CTRL + S** för att spara filen.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   Det är viktigt att använda korrekt skiftläge för &#39;OutlinedInput&#39;-varianten, annars misslyckas kompileringen. Kompileringen av den lokala utvecklingsmiljön startar automatiskt i kommandotolken. Vänta tills följande meddelande visas

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Uppdatera webbläsaren, om den inte uppdateras automatiskt, för att se hur textindatakomponenten använder en annan variant.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   Den här ändringen sker för slutanvändare utan att formulärdefinitionen på AEM Forms Server ändras och gäller specifikt för headless
den aktuella kanalen. Webbkanal i det här labbet.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Stäng Visual Studio-kod och kommandotolken i Windows.

## Vanliga frågor och svar

+++ Är kärnkomponenter tillgängliga offentligt?

Ja, adaptiva Forms Core-komponenter finns med AEM 6.5 Forms och Forms som Cloud Service. Du behöver AEM Forms 6.5 Service Pack 16 eller senare för att kunna använda adaptiva Forms Core-komponenter.

+++

+++ Kräver Headless-formulär en separat licens?

Nej, Headless-formulär använder samma licensvärde, antal formulärinskickade formulär.

+++




## Nästa steg

Nu när du har lärt dig hur man bygger Adaptive Forms och levererar dem till flera kanaler med headless-formulär bör du försöka sätta dina nya kunskaper i praktiken. Ha kul och gör det bara genom att skapa och leverera enastående datainhämtningsupplevelser till slutanvändarna, var de än är, i stor skala!

## Resurser

* [Introduktion till kärnkomponenter i adaptiva formulär](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=sv-SE)

* [Skapa anpassat formulär med hjälp av kärnkomponenter](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Uppdatera format för grundkomponentbaserad AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=sv-SE)

* [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=sv-SE)

* [Använder startkit för Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=sv-SE)
