---
title: Skapa och publicera ett headless-formulär med Adobe Experience Manager Adaptive Forms | Stegvisa handböcker
description: Lär dig hur du skapar och publicerar ett headless-formulär med Adobe Experience Manager adaptiva formulär i den här steg-för-steg-guiden. Upptäck fördelarna med att skapa formulär utan papper och effektivisera processen för att skapa formulär redan idag. Börja bygga dynamiska, responsiva formulär som fungerar smidigt på olika enheter med Adobe Experience Manager Headless Adaptive Forms.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---



# Skapa och förhandsgranska ett Headless-formulär med en React-app {#introduction}

Startsatsen hjälper dig att komma igång snabbt med en React-app. Du kan utveckla och använda Headless-anpassade formulär i en Angular, Vanilla JS och andra utvecklingsmiljöer som du själv väljer.

Att börja med Headless adaptive forms är enkelt och snabbt. Klona det färdiga React-projektet, installera beroendena och kör projektet. Du har ett Headless-anpassat formulär som är integrerat i en React-app. Du kan använda exempelprojektet för att skapa och testa Headless-adaptiva formulär innan du distribuerar dem i en produktionsmiljö.

Låt oss börja:

>[!NOTE]
>
>
> Den här guiden för att komma igång använder en React-app. Du kan använda valfritt teknik- eller programmeringsspråk för att använda Headless adaptive-formulär.

## Innan du börjar {#pre-requisites}

Om du vill skapa och köra en React-app bör du ha följande installerat på datorn:

* Installera [senaste versionen av Git](https://git-scm.com/downloads). Om du inte har använt Git tidigare kan du läsa [Installerar Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installera [Node.js 16.13.0 eller senare](https://nodejs.org/en/download/). Om du inte har använt Node.js tidigare, se [Så här installerar du Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

## Kom igång

Så här kommer du igång:

1. [Startpaket för Headless adaptive forms](#setup)

1. [Förhandsgranska den Headless adaptive-form som ingår i startpaketet](#preview)

1. [Skapa och återge din egen anpassade Headless-form](#custom)



## 1. Konfigurera startpaket för Headless adaptive forms {#install}

Startsatsen är en React-app med ett exempel på Headless-anpassningsbart formulär och motsvarande bibliotek. Använd paketet för att utveckla och testa formulär för Headless-anpassning och motsvarande React-komponenter. Kör följande kommandon för att konfigurera startkit för Headless-anpassade formulär:

1. Öppna kommandotolken och kör följande kommando:

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   Kommandot skapar en katalog med namnet **response-starter-kit-aem-headless-forms** i din nuvarande position och klonar programmet Headless adaptive forms React starter i det. Tillsammans med de konfigurationer och listor över beroenden som krävs för att återge formuläret innehåller katalogen följande viktiga innehåll:

   * **Exempelformulär**: Startsatsen innehåller ett exempelformulär för låneansökan. Om du vill visa formuläret (formulärdefinitionen) som ingår i appen öppnar du `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` -fil.
   * **Exempel på reaktionskomponenter**: Startsatsen innehåller samplingsreaktionskomponenter för RTF och Slider. Den här guiden hjälper dig att skapa egna anpassade komponenter med hjälp av dessa Rich Text- och Slider-komponenter.
   * **Mappningar.ts**: Filen mappings.ts hjälper dig att mappa anpassade komponenter med formulärfält. Du kan till exempel mappa ett numeriskt nummerfält med en klassificeringskomponent.
   * **Miljökonfigurationer**: Med miljökonfigurationer kan du välja att återge ett formulär som ingår i startpaketet eller hämta ett formulär från en AEM Forms-server.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > Exemplen i dokument är baserade på VSCode. Du kan använda vilken kodredigerare som helst för oformaterad text.


1. Navigera till **response-starter-kit-aem-headless-forms** och kör följande kommando för att installera beroendena:

   ```shell
   npm install
   ```

   Kommandot hämtar alla nödvändiga paket och bibliotek som behövs för att köra och skapa appen, till exempel Headless adaptive forms libraries (@aemforms/af-response-renderer, @aemforms/af-response-components, @adobe/rea-trum), kör valideringar och bevarar data för instanser av formuläret.

   ![](/help/assets/install-react-app-starter-kit.png)


## 2. Förhandsgranska den Headless-anpassade formen {#preview}

När du har konfigurerat startpaketet kan du förhandsgranska det Headless-anpassade formuläret och ersätta det med din egen anpassade form. Du kan också konfigurera startsatsen för att hämta ett formulär från en AEM Forms-server. Förhandsgranska formuläret

1. Byt namn på `env_template` fil till `.env` -fil. Kontrollera också att alternativet USE_LOCAL_JSON är inställt på true.

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. Använd följande kommando för att köra programmet:

   ```shell
     npm start
   ```


   Det här kommandot startar en lokal utvecklingsserver och öppnar exempelformuläret Headless adaptive form, som ingår i startappen, i din standardwebbläsare.

   ![Exempel på Headless-formulär](assets/sample-headless-adaptive-form.png)

   Voila! Du är redo att börja utveckla ett anpassat Headless-formulär.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless adaptive form on an AEM Server  -->

## 3. Skapa och återge en egen Headless-blankett{#custom}

Ett anpassat formulär utan rubrik representerar formuläret och dess komponenter, till exempel fält och knappar, i JSON-format (JavaScript Object Notation). Fördelen med JSON-formatet är att det enkelt kan tolkas och användas av olika programmeringsspråk, vilket gör det enkelt att utbyta formulärdata mellan system. Om du vill visa exempelformuläret Headless adaptive som ingår i appen öppnar du `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` -fil.

Låt oss skapa ett kontaktformulär med fyra fält: Namn, E-post, Kontaktnummer och Meddelande. Fälten definieras som objekt (objekt) i JSON, där varje objekt (objekt) har egenskaper som typ, etikett, namn och obligatoriskt. Formuläret har också en knapp av typen &quot;skicka&quot;. Här är JSON för formuläret.


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * Attributet afModelDefinition behövs bara för React-program och är inte en del av formulärdefinitionen.
> * Du kan skapa formuläret JSON för hand eller använda [AEM adaptiv formulärredigerare (adaptiv formulärredigerare, WYSIWYG)](create-a-headless-adaptive-form.md) för att skapa och leverera formuläret JSON. I en produktionsmiljö använder du AEM Forms för att leverera formuläret JSON, mer om det senare.
> * I självstudien används https://pipedream.com/ för att testa inskickade formulär. Du använder egna slutpunkter eller slutpunkter från tredje part som godkänts av din organisation för att ta emot data från ett Headless Adaptive-formulär.


Ersätt exempelformuläret Headless adaptive form JSON om du vill återge formuläret `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` med ovanstående JSON sparar du filen, väntar på att starter-kit ska kompilera och uppdatera formuläret.

![Ersätt exemplet Headless adaptive form JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` med den anpassade Headless-adaptiva formen JSON](assets/render-custom-headless-adaptive-form.png)

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Du har renderat den Headless Adaptive-formen.


## Bonus

Låt oss ange rubriken på webbsidan som är värd för formuläret till `Contact Us | WKND Adventures and Travel`. Öppna dialogrutan _react-starter-kit-aem-headless-forms/public/index.html_ -fil för redigering och ange titeln.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## Nästa steg

Som standard används [Adobe Spectrum](https://spectrum.adobe.com/) -komponenter för att återge formuläret. Du kan använda för att skapa och använda egna komponenter eller tredjepartskomponenter. Du kan till exempel använda användargränssnittet för Google-material eller Chakra-gränssnittet.

Låt oss [använd Google Material UI](use-google-material-ui-react-components-to-render-a-headless-form.md) för att återge formuläret Kontakta oss.




