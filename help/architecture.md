---
title: Headless adaptive forms architecture
description: Läs om arkitekturen i AEM Forms Headless Adaptive Forms och hur den kan hjälpa dig att snabbt skapa formulär för olika plattformar. Den här artikeln innehåller information om hur Headless Adaptive Forms fungerar och hur de kan integreras med olika program för att förenkla formulärbyggprocessen.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, adaptive form, architecture
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---


# Hur Headless adaptive form fungerar?

Ett Headless adaptive form är en JSON-struktur (schema) som består av formulärfält (textruta, alternativ och många fler fält) och motsvarande regler (villkorslogik) för att lägga till interaktivt beteende i formuläret. Du kan använda REST API:er i ditt program eller på din webbplats för att begära den värdbaserade JSON-strukturen och återge JSON-strukturen som ett formulär i din app eller på din webbplats. Ett enda formulär utan Headless-funktioner kan hantera flera webbsidor och applikationer utan att göra några app- eller webbplatsspecifika ändringar i det.

![Hur Headless adaptive form fungerar](/help/assets/how-headless-adaprive-forms-work.png)

## Arkitektur {#architecture}

En typisk Headless adaptive forms architecture är en Adobe Experience Manager Forms Server, Headless adaptive forms hosted on Adobe Experience Manager Forms Server och era klientapplikationer (webbplats, mobilapplikation, JavaScript-appar, chattapplikationer med mera) för kanalspecifika formuläråtergivningar.

En typisk arkitektur för en driftsättning av Headless-anpassade formulär ser ut så här:

![Arkitektur](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Komponent i implementering av Headless-anpassade formulär

**Adobe Experience Manager Server**: Tillsammans med att fungera som värd för Headless-adaptiva formulär erbjuder Adobe Experience Manager följande backend-funktioner:

* RESTful APIs to list, fetch, pre-fill, validate, submit, track submit status of headless forms.
* Visuell redigerare som enkelt tar fram en Headless-blankett.
* Forms datamodell för att ta emot eller skicka data till olika datakällor.
* Arbetsflödesmotor för att automatisera komplexa uppgifter.

**Headless adaptive forms**: En Headless adaptive-form representeras som en .json-fil. JSON-strukturen definierar komponenter, begränsningar och struktur i ett formulär.

**Front-end-appar**: Front-end-appar som SPA (Single Page Applications), Mobile Apps, JavaScript Apps, använder Headless-anpassade formulär (JSON Form Representation) och återger formuläret på en klient. Du kan använda React Renderer-komponenten som levereras med Headless adaptive-formulär för att återge ett adaptivt formulär eller skapa en egen anpassad komponent för att återge Headless-adaptiva formulär.

<!-- ### Understanding Headless adaptive forms definition -->



### Utvecklarverktyg

I en typisk utvecklingscykel börjar du med att skapa och använda Headless-anpassade formulär på Adobe Experience Manager Forms Server. I det andra steget mappar du dina UI-komponenter eller använder ett offentligt UI-komponentbibliotek, som Google Material UI eller Chakra UI för att utforma formulären. I det sista steget hämtar och visar du formulär utan Headless-funktioner i programmet (webbplats, mobilprogram, JavaScript-appar, chattprogram eller många andra ytor).

Följande verktyg hjälper dig att skapa och integrera Headless-formulär i dina program:

**Forms Web SDK (Client-Side Runtime)**: Forms Web SDK är ett klientbibliotek för JavaScript. Det gör att du kan använda validering på klientsidan på formulärfält, behålla formulärets status och tillhandahåller kopplingar för att ansluta formulär med UI-lager eller adaptiva formuläråtergivna komponenter. Det gör det möjligt för kunder att validera begränsningar som tillämpas på olika fält i ett formulär och gör att man kan ansluta JSON-formulärstrukturen till användargränssnittets ramverk. Forms Web SDK har följande komponenter:

* **Affärsregelprocessor**: Affärsregelprocessorn accepterar formulärets JSON-struktur som indata, hanterar tillståndet för formulärfälten, kör regler och händelsehanterare som finns i JSON.
* **Reagera binder**: Tillhandahåller hookar över kontrollenhet för att lägga till tillstånd i Form Components. Det är också användbart när du ska fylla i ett formulär i förväg.
* **Komponentbibliotek**: Den innehåller React Spectrum-komponenter och använder kopplingar i React Binder-modulen för att lägga till tillstånd i dessa komponenter.

Förutom att tillhandahålla API:er för att validera begränsningar som tillämpas på olika fält i ett formulär, tillhandahåller Forms Web SDK kopplingar för att ansluta Headless-anpassade formulär till gränssnittets ramverk. Den innehåller även &#x200B; React Renderer för Headless-adaptiva formulär som hjälper dig att integrera ett Headless-adaptivt formulär i programmet. Följande komponenter i Web SDK finns:

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Alla dessa komponenter ingår i AEM. När du skapar ett AEM Archetype 37-projekt eller senare för Headless-formulär inkluderas den senaste versionen av ovanstående bibliotek i projektet.

* **Kodspelaren**: [Kodspelaren](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en) är en interaktiv miljö som är utformad för utvecklare som vill experimentera med, lära sig om och testa funktionerna i Headless Adaptive Forms.

**Startat program**: Adobe har också släppt ett startprogram som hjälper dig att snabbt komma igång med Headless-anpassade formulär.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) innehåller en översikt över olika komponenter i Headless-anpassade formulär. Den innehåller också en lista över alla komponenter som stöds, deras motsvarande egenskaper och begränsningar.

**Visual Studio Code Extension**: [Visual Studio Code extension](visual-studio-code-extension-for-headless-adaptive-forms.md) för att skapa en giltig JSON-struktur. Den har IntelliSense-stöd och -validering för JSON-formulärstruktur tillsammans med vanliga funktioner som att lägga till, ta bort eller byta namn på komponenter i en JSON-struktur.

**HTTP- och JavaScript-API:er**: [HTTP-API:er](https://opensource.adobe.com/aem-forms-af-runtime/api/) gör att du kan visa, hämta, validera, skicka och spåra status för headless-formulär. [JS API:er](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) hjälper dig att använda Headless-anpassade formulär med alla JavaScript-baserade gränssnittsramverk.

**JSON-formel**: Det är en implementering av formuläruttrycksgrammatik som hjälper dig att fråga efter JSON-struktur och skapa regler för Headless-adaptiva formulär. Grammatiken är en kombination av kalkylbladsliknande funktioner och operatorer och [JMESPath](https://jmespath.org/) är ett JSON-frågespråk. Du kan använda [playground](https://opensource.adobe.com/json-formula/dist/index.html) för att utforska JSON-formelsyntax och -funktioner.

Specifikationer för **Adaptiv Forms version 2.0**: Specifikationen Adaptiv Forms version 2.0 innehåller detaljerad information om alla komponenter, begränsningar och metoder som finns för att definiera adaptiva formulär utan Headless. Specifikationen är tillgänglig i formatet [PDF](/help/assets/headless-adaptive-forms-specification.pdf).

