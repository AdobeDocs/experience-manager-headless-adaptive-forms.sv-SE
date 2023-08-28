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
exl-id: 46df943c-0622-4b3b-a802-85c39ac6a734
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 0%

---

# Bygg engagerande Forms med kärnkomponenter och Headless Adaptive Forms på AEM 6.5 Forms {#build-engaging-forms-using-core-components-and-headless}

## Lab-översikt {#lab-overview}

I det här praktiska labbet lär du dig:

Så här använder du AEM Forms för att enkelt skapa adaptiva Forms med hjälp av de senaste Core-komponenterna som är kompatibla med AEM Sites, vilket möjliggör datainhämtning i flera kanaler genom att leverera det adaptiva Forms som headless-formulär till webben, mobiler och chatt. Du får också lära dig de effektivaste strategierna när det gäller format, anpassningar och gränssnittsutveckling.

## Viktiga uppgifter {#key-takeaways}

* **Affärsflexibilitet**: Som affärsanvändare kan jag enkelt skapa formulärupplevelser för flera kanaler.

* **Framåtutvecklare**: Som frontutvecklare kan jag styra användarupplevelsen med headless-formulär.

* **Utvecklarhastighet**: Som utvecklare kan jag enkelt och konsekvent anpassa webbplatser och Forms-komponenter.

## Innan du börjar {#pre-requisites}

Så här använder du händerna på labbet:

* Installera [senaste versionen av Git](https://git-scm.com/downloads). Om du inte har använt Git tidigare kan du läsa [Installerar Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installera [Node.js 16.13.0 eller senare](https://nodejs.org/en/download/). Om du inte har använt Node.js tidigare, se [Så här installerar du Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [Aktivera Headless Adaptive Forms](enable-headless-adaptive-forms-and-core-components.md) i AEM 6.5 Forms.

* Installera [Microsoft Visual Studio Code](https://code.visualstudio.com/download) eller en vanlig textredigerare. Exempel i dokument använder Microsoft Visual Studio Code.

## Lektion 1 {#lesson-1}

### Syfte {#lesson-1-objectives}

Bekanta dig med AEM 6.5 Forms-miljö.

### Lektionssammanhang {#lesson-1-context}

I den här lektionen bekanta du dig med AEM 6.5 Forms genom att navigera i användargränssnittet.

### Utövning {#lesson-1-excercise}

1. Öppna webbläsaren och ange webbadressen till författarmiljön. Till exempel:
   [https://localhost:4502](https://localhost:4502).

1. När du är inloggad navigerar du till användargränssnittet för AEM Forms. Klicka **Forms**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Klicka **Forms och dokument**. Stäng alla popup-fönster som rör inställningar eller information.

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

   1. Öppna <https://requestbin.com/> på en ny flik i webbläsaren.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Klicka **Skapa en offentlig behållare** och kopiera slutpunkts-URL:en.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Den här särskilda slutpunkten fungerar som ett exempel för att skicka och visa data. I den faktiska produktionen använder du din egen slutpunkt eller datakällor för att lagra hämtade data.

1. Skapa ett anpassat formulär:

   1. Navigera till AEM Forms webbgränssnitt och navigera till **Forms** > **Forms och dokument**.

   1. Klicka **Skapa** och väljer Adaptiv form.
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Välj **Tom med kärnkomponenter** mall från mallurvalsskärmen som visas nedan och klicka på **Nästa**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Ange `Contact us` som **Titel** av formuläret. Se till att **Namn** formuläret är `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Klicka **Skapa**. En dialogruta visas.

   1. Klicka på **Redigera**. Formuläret öppnas i Adaptiv formulärredigerare. Stäng alla popup-fönster eller dialogrutor för inställningar eller information.

   1. Öppna webbläsaren Komponenter och dra och släpp panelkomponenten mitt på skärmen.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Dra och släpp komponenter från komponentwebbläsaren för att skapa ett formulär som liknar följande:

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Öppna Content Browser, klicka på egenskapsikonen för Guide Container och öppna dialogrutan **Inlämning** -fliken. Välj **Skicka till REST-slutpunkt** Skicka åtgärd väljer du **Aktivera begäran om POST** och ange REST-slutpunkt som skapats i lektion 2 i **URL för begäran om POST** och klicka på **Klar** -ikon.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publicera ett anpassat formulär:

   1. Öppna AEM, navigera till **Forms** > **Forms och dokument**. Markera formuläret som skapades i föregående steg och klicka på **Publicera**.

   1. I dialogrutan Publicera resurser klickar du på **Publicera**. Meddelandet om att åtgärden lyckades visas.

## Lektion 3

### Syfte

Uppdatera format med hjälp av vedertagna metoder för utveckling av klientprogram.

### Lektionssammanhang

I den här lektionen lär du dig hur du enkelt kan uppdatera format för tidigare skapade adaptiva formulär.

### Utövning

Konfigurera lokal databas för temat:

1. Öppna kommandotolken eller kommandotolken med administratörsbehörighet:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Använd följande kommando på kommandotolken för att navigera till `c:\git` mapp.

   ```Shell
   cd git
   ```

   Om mappen inte finns använder du `md git` för att skapa den.

1. Använd följande kommando för att klona koden för temat Framtend:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Använd följande kommando i listordningen för att navigera till **aem-forms-theme-canvas** och öppna Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Välj **Författarna av alla filer i den överordnade mappen är betrodda** och klicka **Ja, jag litar på författarna**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Byt namn på `env_template` till .env.  Om du vill byta namn på filen högerklickar du på **env_template** och väljer **Byt namn** alternativ.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Ange följande värden för variablerna i .env-filen och spara filen:

   * **AEM_URL**: Ange URL för en **publicera** -instans. Till exempel, `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: Ange formulärets namn. Till exempel, `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. Kör följande kommando i kommandotolken:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Om du får ett meddelande där du ombeds att uppdatera npm via `npm notice Run npm nstall -g npm@9.6.0`ignorera meddelandet.
   > * Kör inte andra npm-kommandon om inte annat anges i arbetsboken.

1. Kör nu följande kommando för att förhandsgranska formuläret.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   När ovanstående kommando har körts väntar du på `webpack compiled` meddelande. Formuläret visas på en webbläsarflik.

   >[!NOTE]
   >
   >Om du får en tom skärm i webbläsaren när du har kört `npm run live` i mer än 3-4 minuter, ändra `localhost` i webbläsarens URL till 127.0.0.1 och tryck **Retur**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. Öppna dialogrutan `PROJECT\src\site\_variables.scss` -fil. Lägg märke till `$error` färgen är en skugga av RED.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Skicka formuläret i webbläsaren för att se den röda färgen i **Förnamn** fält.

   ![](/help/assets/error-color-before.png)

1. Ange **$error** färg till **#5736Web** och spara filen.

1. Uppdatera webbläsaren och skicka formuläret. Observera att felfärgen i förnamnsfältet har ändrats därefter.

   ![](/help/assets/error-color-after.png)

1. Tryck på i kommandotolken **CTRL+C**, ange **Y** och tryck **Retur** för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.
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

1. Använd följande kommando på kommandotolken för att navigera till `c:\git` mapp.

   ```Shell
   cd git
   ```

1. Använd följande kommando för att klona startprojektet för adaptiv formulärreaktion:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Använd följande kommandon i listordningen för att navigera till **response-starter-kit-aem-headless-forms** och öppna Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Fönstret Visual Studio Code öppnas.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Så här återger du formuläret som finns i publiceringsmiljön:

1. Byt namn på filen env_template till .env. Om du vill byta namn högerklickar du på **env_template** och väljer **Byt namn** alternativ.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna.

   * **AEM_URL**: Ange URL-adressen för publiceringsmiljön. Till exempel, `https://localhost:4503/`

   * **AEM_FORM_PATH**: Ange sökvägen till det adaptiva formulär som skapades i föregående lektion. Till exempel, `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Öppna kommandofönstret och kontrollera att du är vid **response-starter-kit-aem-headless-forms** och kör följande kommando:

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
   > Om du får en tom skärm i webbläsaren när du har kört `npm start` i mer än 3-4 minuter, ändra `localhost` i webbläsarens URL till 127.0.0.1 och tryck **Retur**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Låt oss göra ändringar i formuläret på servern som företagsanvändare och automatiskt se ändringarna som återspeglas i det headless-formuläret.

1. Öppna AEM Forms gränssnitt i webbläsaren. Till exempel: [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Välj **Kontakta oss** formulär och klicka **Redigera.** Formuläret öppnas i Adaptiv Forms-redigerare.


1. Välj **Kontaktnummer** och klicka på **Ikonen Redigera (pennikonen)** i verktygsfältet. Om du inte kan se popup-verktygsfältet växlar du till redigeringsläget genom att klicka på **Redigera** överst till höger, vänster till **Förhandsgranska** -knappen.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Ändra etiketten till **Mobilnummer**. Klicka på ett tomt utrymme i formuläret så sparas ändringarna i formuläret.

Låt oss publicera det uppdaterade formuläret för att sprida ändringarna till publiceringsmiljön.

1. På fliken AEM Forms hanteringsgränssnitt väljer du kontaktformuläret och klickar på **Avpublicera**. Om du inte ser **Avpublicera** går du vidare till steg 3 för att publicera ändringarna direkt.


1. Klicka **Avpublicera**. Klicka **Stäng** i respektive dialogruta.

1. När webbläsaren har uppdaterats markerar du formuläret Kontakta oss och klickar på **Publicera**.


1. Klicka **Publicera**. Klicka **Stäng** i dialogrutan.

1. Uppdatera webbläsarfliken med det headfria formuläret synligt. Observera att etiketten Kontaktnummer har ändrats till Mobilnummer.

   ![](/help/assets/headless-adaptive-form.png)

1. Öppna kommandotolkfönstret som används för att starta **response-starter-kit-aem-headless-forms** projekt, tryck **CTRL+C** och sedan ange **Y** och tryck på Retur för att avsluta npm-processen. Det är viktigt att stoppa npm-servern så att den inte hamnar i konflikt med nästa uppsättning övningar.

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

1. Använd följande kommando på kommandotolken för att navigera till `c:\git` mapp.

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

1. Använd följande kommando i listordningen för att navigera till **response-starter-kit-aem-headless-forms** och öppna koden i Visual Studio Code:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Så här återger du formuläret som finns i publiceringsmiljön:

1. Byt namn på **env_template** fil till **.env** -fil. Om du vill byta namn högerklickar du på **env_template** fil och markera **Byt namn**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Ange följande värden för variablerna i .env-filen. Spara filen när du har uppdaterat variablerna. Använd **CTRL + S** växla kombination för att spara filen.

   * **AEM_URL**: Ange URL-adressen för publiceringsmiljön. Till exempel: [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: Ange sökvägen till det adaptiva formulär som skapades i föregående lektion. Till exempel /content/forms/af/contact-us/


1. Öppna kommandofönstret och kontrollera att du är vid **response-starter-kit-aem-headless-forms** och kör följande kommando:

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
   >Om du får en tom skärm i webbläsaren när du har kört `npm start` i mer än 3-4 minuter, ändra `localhost` i webbläsarens URL till 127.0.0.1 och tryck **Retur**.

   ![](/help/assets/google-mui-form.png)

## Lektion 6

### Syfte

Skapa ett alternativt utseende och känsla för den headless-formen med materialvariationer för UI-komponenter

### Lektionssammanhang

I den här lektionen lär du dig som gränssnittsutvecklare hur du skapar en alternativ representation av olika komponenter med hjälp av materialgränssnittet för det adaptiva formuläret som skapats tidigare av företagsanvändaren.

### Utövning

Uppdatera variationen av komponenterna i det headless-projektet. Ändra varianten på textindatakomponenten i användargränssnittet till `OutlinedInput`:

1. I Visual Code navigerar du till textindatakomponenten genom att öppna `index.tsx` fil på `src/components/textinput/index.tsx`.

1. Lägg till `//` i början av kodraden 104. Raden konverteras till en kommentar.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Lägg till följande på rad 105 om du vill använda en annan variant av komponenten och spara filen. Använd **CTRL + S** växla kombination för att spara filen.

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


   Den här ändringen sker för slutanvändare utan att formulärdefinitionen på AEM Forms Server ändras och gäller specifikt för den aktuella huvudlösa kanalen. Webbkanal i det här labbet.

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

* [Introduktion av komponenter i adaptiv Form Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Skapa adaptiv form med hjälp av kärnkomponenter](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Uppdatera format för grundkomponentbaserad AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Använda startkit för Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
