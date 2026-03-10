---
title: Frågor och svar om Headless Adaptive Forms
description: Frågor och svar
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, adaptive form, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Vanliga frågor och svar {#headless-adaptive-forms-faq}

## Ska jag känna till React.js för att använda Headless adaptive-formulär?

Du kan använda vilket ramverk, bibliotek eller språk som helst för att återge formulär som kan anpassas utan Headless och använda Adobe REST API:er för att validera och skicka formulären. AF-kärnbiblioteket, som du får direkt, är ramverksoberoende. Bibliotek för React Render och React Component (React-render och React-komponenter) som medföljer när du packar upp dem är till stor hjälp. Du kan skapa egna komponenter. Du begränsas inte till de som finns.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Kräver jag att Forms as a Cloud Service sandlåda använder formulär som kan anpassas utan headless?

Du kan använda startappen för att börja utveckla och formatera dina Headless-formulär. Du behöver Forms as a Cloud Service för att hantera Headless-anpassade formulär tillsammans med backend-formulärfunktioner.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Var kan jag få en förhandsvisning av en Headless-blankett? {#storybook-example}

Du kan använda startappen för att återge och förhandsgranska ett anpassat Headless-formulär. Du kan också ändra ett [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples—introduction)-exempel om du vill förhandsgranska ett Headless-anpassat formulär.

![](/help/assets/storybook-example.png)

## Går det att använda Headless-anpassade formulär med anpassade ramverk?

Headless adaptive forms are based on [standard specification](/help/assets/headless-adaptive-forms-specification.pdf). Du kan utöka specifikationen och använda den för att skapa anpassade komponenter. Exempel: komponenter för Chakra-gränssnittet, Vue.js med flera.

## Har Headless adaptive forms stöd för överlappande fält?

För överlappande fält beror innehållet i det andra fältet på det innehåll som valts i det första fältet. [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behavior—options&args=formJson.items[0].fieldType:drop down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items son.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) innehåller ett exempel på överlappande fält.

## Kan man med Headless-anpassade blanketter förifylla blanketter med skräddarsydda data?

Headless adaptive forms allow prefill forms with personalized data. [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples—prefill-form-with-personalized-data) innehåller ett exempel på hur du fyller i ett Headless-formulär i förväg.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Kan jag använda Headless-anpassade formulär med Angular SPA?

Du kan använda Web SDK för att integrera Headless-formulär med Angular SPA. Den är oberoende av alla ramverk. Du kan använda React SDK som referens.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Finns det någon plugin som underlättar utvecklingen för Headless AF?

Ja - med Visual Studio Code-tillägget kan du manuellt skapa headless adaptive-formulär i JSON.

## Vad rekommenderas för mobilformulär och offlineformulär? {#mobile-offline-forms}

Bygg en egen app och hämta formulärdefinitioner via det Headless Adaptive Forms API. Du kan också implementera offlinesupport (till exempel lokal lagring och synkronisering). Mer information om rekommenderad metod och länkar till API:er finns i [Bästa praxis för mobilformulär](mobile-forms-best-practices.md).

## Hur använder man GraphQL eller headless API:er med AEM Forms?

AEM Headless Adaptive Forms använder **HTTP/REST API:er**, inte GraphQL. Appen anropar dessa API:er för att lista formulär, hämta en formulärdefinition (JSON), validera, skicka och spåra överföringsstatus. Använd [Headless adaptive forms HTTP API:er](https://opensource.adobe.com/aem-forms-af-runtime/api/) som fullständig referens. Information om hur formulär hämtas och återges finns i [Arkitektur](architecture.md) och [Förstå formulär utan rubriker](understanding-headless-forms.md).

## Hur kan jag implementera och formatera headless-formulär med React-komponenter i Adobe AEM Forms?

Du implementerar och formaterar headless-formulär med dina egna React-komponenter och CSS (eller ett UI-bibliotek som materialgränssnitt). Formulärlogiken - stat, validering och regler - kommer från Forms Web SDK och formuläret JSON; appen har det användargränssnitt som återger den.

* Mer information om hur du formaterar ett headless-formulär med ett React UI-bibliotek finns i [Använda ett anpassat responsbibliotek för att återge ett headless-formulär](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Mer information om hur du skapar och mappar anpassade React-komponenter till formulärfält finns i [Använda anpassade komponenter för att återge ett headless-formulär](developing-for-headless-forms-using-your-own-components.md).

Mer information om begrepp som när du ska använda headless-formulär, statushantering och validering finns i [Om rubrikfria formulär](understanding-headless-forms.md).

## Hur kan jag implementera och anpassa AEM Forms med anpassade CSS-format, teman, regelredigerare och rubrikfria formulär?

**Headless-former:** Du kan styra formatering och utseende. Du använder dina egna React-komponenter (eller andra) och din egen CSS. Det finns inga inbyggda teman. Se [Använd ett anpassat svarsbibliotek för att återge ett headless-formulär](use-google-material-ui-react-components-to-render-a-headless-form.md) och [Använd anpassade komponenter för att återge ett headless-formulär](developing-for-headless-forms-using-your-own-components.md) för att implementera och formatera headless-formulär.

**Klassisk AEM Forms (teman, regelredigerare, visuell redigerare):** Anpassad CSS, temaredigeraren och regelredigeraren används för den klassiska (ej headless) redigeringsfunktionen i Forms. Information om detta finns i [AEM Forms-dokumentationen](https://experienceleague.adobe.com/docs/experience-manager-forms.html) för Experience League.

## Kan ett Headless-anpassat formulär ansluta till någon CRM för att läsa eller skriva data?

Du kan använda Microsoft Dynamics och Salesforce för att skicka eller förifylla ett formulär utan Headless-funktioner. Förutom CRM:er har Headless adaptive forms stöd för att skicka eller förifylla med REST-slutpunkter, e-post och anpassade skicka-åtgärder.
