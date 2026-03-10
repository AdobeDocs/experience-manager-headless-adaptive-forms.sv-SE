---
title: Förstå headless-formulär - koncept och frågor och svar
description: Svar på vanliga frågor om vilka rubrikfria formulär som är, hur de skiljer sig från traditionella formulärbibliotek, implementeringsinformation, gränssnittskontroll, prestanda och integrering med ramverk och backends.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless forms, headless form library, adaptive forms, state management, validation, design system, SSR, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---


# Förstå headless-formulär - koncept och frågor och svar {#understanding-headless-forms}

Den här guiden besvarar vanliga frågor om headless-formulär i allmänhet och hur de gäller för AEM Headless Adaptive Forms. Använd det för att bestämma när ett headless-tillvägagångssätt ska användas och hur formulär ska implementeras, formateras och integreras i stacken.

## Grunderna och förståelse {#basics-understanding}

### Exakt vad är ett headless-formulärbibliotek?

Ett **headless-formulärbibliotek** är en formulärlösning som skiljer **formulärlogik** (tillstånd, validering, regler, överföring) från **presentation** (UI-komponenter och format). &quot;head&quot; är det synliga användargränssnittet. &quot;headless&quot; betyder att biblioteket inte dikterar eller skickar ett fast användargränssnitt. I stället visas följande:

* En **formulärmodell** (ofta JSON): struktur, fält, begränsningar och regler.
* **API:er eller kopplingar** för att läsa och uppdatera formulärstatus, köra validering och hantera överföring.
* **Händelser och livscykel** så att användargränssnittet kan reagera på ändringar.

I AEM Headless Adaptive Forms är formuläret en [JSON-struktur](architecture.md) på Adobe Experience Manager. [Forms Web SDK](architecture.md#developer-tools) (körningsmiljö på klientsidan) innehåller logiklagret, affärsregelprocessor, statshantering, validering, medan programmet tillhandahåller det användargränssnitt som återger strukturen.

### Hur skiljer sig ett headless-formulär från ett vanligt formulärbibliotek?

| Proportioner | Traditionellt formulärbibliotek | Headless-formulärbibliotek |
|--------|---------------------------|------------------------|
| **Gränssnitt** | Levereras med inbyggda komponenter och format | Inget förskrivet användargränssnitt - du har egna komponenter |
| **Formatering** | Tema eller åsidosättningar för bibliotekskomponenter | Full kontroll; använd designsystemet i befintligt skick |
| **Formulärdefinition** | Kodskydda ofta (komponenter i JSX/HTML) | Datadriven (JSON/schema från CMS eller API) ofta |
| **Läge och validering** | Kopplad till bibliotekskomponenter | Exponeras via API:er/krokar, vilket gränssnitt som helst kan bindas till dem |
| **Kanaler** | Webb (ibland ett ramverk) | Samma formulärdefinition kan skapa webbplatser, mobiler, chatt osv. |

Med AEM Headless Adaptive Forms [skapar och publicerar du ett formulär](create-and-publish-a-headless-form.md) en gång i AEM. Alla klienter (React, Angular, native mobile, chatbot) kan [hämta formuläret JSON](architecture.md) och återge det med rätt användargränssnitt för den kanalen.

### Varför ska jag använda headless-formulär istället för en UI-baserad formulärlösning?

Headless-formulär passar bra när du behöver:

* **Konsekvent design av system** - Använd dina befintliga komponenter och varumärken utan att bryta mot standardinställningar för bibliotek.
* **Flerkanals** - En formulärdefinition för webb, mobil och andra kontaktytor (se [Översikt](overview.md)).
* **CMS- eller backend-drivna formulär** - Författare ändrar formulärstruktur och regler utan koddistributioner. Din app använder bara JSON.
* **Ramverksflexibilitet** - Biblioteket [AF-core](https://www.npmjs.com/package/@aemforms/af-core) är ramverksoberoende. Reaktionsbindningar tillhandahålls av praktiska skäl, men du kan skapa bindningar för andra ramverk.
* **Backend-funktioner** - Utnyttja AEM Forms för förifyllning, validering, sändning, arbetsflöden och Forms datamodell utan att låsa i en specifik gränssnittsstack.

### När är det klokt att använda en headless-strategi?

Använd headless-formulär när:

* Du har eller vill ha ett starkt designsystem eller komponentbibliotek.
* Forms skapas av icke-utvecklare (t.ex. i en CMS) och måste fungera i flera appar eller kanaler.
* Ni behöver samma formulärlogik (validering, regler) för webben, mobiler och andra klienter.
* Du vill minimera återgivningarna och kunna testa formulärlogiken oberoende av användargränssnittet.

Ta en titt på ett traditionellt, användargränssnitt som ingår i ett formulärbibliotek när:

* Du behöver ett arbetsformulär i ett enda webbprogram snabbt och behöver inte tänka på anpassat användargränssnitt eller flerkanaligt.
* Teamet föredrar att definiera formulär endast i kod i ett ramverk.

### Är &quot;headless&quot; bara ett surrord eller löser det verkliga problem?

Det löser de verkliga arkitektoniska problemen:

* **Separation av problem** - Formulärstruktur, regler och validering finns i data och ett logiklager. Gränssnittslagret återger bara och skickar användaråtgärder. Detta förbättrar testbarheten och återanvändningen.
* **Kanaloberoende** - En formulärdefinition kan generera olika användargränssnitt (t.ex. React web, React Native, Angular eller voice). AEM Headless Adaptive Forms har byggts för detta: [bygg en gång, leverera för React, SPA, webb, mobil med mera](overview.md).
* **Redigering utan kod** - Affärsanvändare kan ändra fält och regler i [redigeraren för anpassade formulär](create-a-headless-adaptive-form.md). Utvecklare behöver inte distribuera om för innehållsändringar.
* **Integrering med befintliga stackar** - Du behåller designsystemet, lägeshanteringen och routningen. Det headless-lagret hanterar bara formulärtillstånd, validering och överföring.

## Implementering och tekniska frågor {#implementation-technical}

### Hur hanterar headless-formulär delstat?

I AEM Headless Adaptive Forms hanteras läget av **Forms Web SDK**:

* **Affärsregelprocessor** - Accepterar formulär-JSON, hanterar fälttillstånd och kör regler och händelsehanterare som definierats i JSON.
* **Reagera binder** - Tillhandahåller kopplingar (t.ex. `useRuleEngine`) över kontrollenheten så att React-komponenter tar emot det aktuella läget och hanterare. Samma tillstånd kan användas av icke-React-gränssnitt via de centrala API:erna.
* **Läge** innehåller fältvärden, synlighet, giltighet och anpassade egenskaper som definierats i formulärmodellen.

Gränssnittskomponenterna tar emot tillstånd och hanterare (t.ex. `[state, handlers] = useRuleEngine(props)`). Du återger från `state` och anropar `handlers` när användaren interagerar. Runtime-modulen håller statusen synkroniserad med formulärdefinitionen och reglerna. Se [Arkitektur](architecture.md) och [Använd anpassade komponenter för att återge ett headless-formulär](developing-for-headless-forms-using-your-own-components.md).

### Hur fungerar valideringen i en headless-formulärkonfiguration?

Valideringen ingår i formulärlogiklagret:

* **Begränsningar** definieras i formatet JSON (t.ex. required, min/max, pattern). Forms Web SDK tillämpar dessa begränsningar och visar valideringsstatus (t.ex. giltig/ogiltig, felmeddelanden) för dina komponenter.
* **Verifiering på klientsidan** tillämpas av SDK baserat på formulärstrukturen. Gränssnittet visar fel från läget.
* **Verifiering på serversidan** är tillgänglig via AEM API:er (t.ex. validera slutpunkten). Du kan validera före eller under sändning.

Du implementerar inte valideringslogik i användargränssnittet. Du visar bara valideringsstatusen och meddelanden som tillhandahålls av körningsmiljön.

### Kan jag integrera headless-formulär med schemavalidering (Yup, Zod, Joi)?

Den inbyggda valideringen styrs av JSON-begränsningarna i formuläret. Så här använder du Yup, Zod, Joi eller liknande:

* Du kan **härleda eller generera** JSON för Headless Adaptive Form från ditt schema (t.ex. konvertera JSON-schema till JSON-format) så att en av de sanna källorna driver både schemavalidering och formulärstruktur.
* För **anpassad validering** utöver JSON-formuläret kan du köra egna validerare (Yup/Zod/Joi) i händelsehanterare eller före sändning, och skicka resultat till formulärtillståndet eller blockera överföringen. Integrationspunkter är samma kopplingar/API:er som du använder för delstat och sändning.

[Adaptiv Forms-specifikation](/help/assets/headless-adaptive-forms-specification.pdf) och [JSON-formel](architecture.md) definierar regeln och begränsningsmodellen som används av körningsmiljön.

### Hur hanterar jag asynkron validering (t.ex. tillgänglighet för användarnamn)?

Asynkron validering kan implementeras i programlagret:

* Använd **regler eller händelsehanterare** i JSON-formuläret (där det stöds) för att utlösa logik när ett fält ändras.
* I dina **anpassade komponenter** använder du samma status-/hanterarkopplingar för att anropa din serverdel (t.ex. API:t för användarnamnstillgänglighet) och sedan uppdatera fältets giltighet eller visa ett fel via de körnings-API:er eller lokala tillstånd som du använder i gränssnittet.
* Du kan också kontrollera **vid oskärpa eller före sändning** och ange att fälttillståndet är ogiltigt med ett anpassat meddelande om den asynkrona kontrollen misslyckas.

Det exakta mönstret beror på hur appen integreras med [affärsregelprocessorn](architecture.md) och anpassade komponenter.

### Hur skickar jag data till API:er med headless-formulär?

Inlämningen är fristående från användargränssnittet:

* **AEM skicka-åtgärder** - Du konfigurerar formuläret i AEM att skicka till REST-slutpunkter, e-post eller integreringar (t.ex. Microsoft Dynamics, Salesforce). Formuläret skickas via AEM, som hanterar det faktiska HTTP/backend-anropet. Se [Använd händelser för att hantera och skicka formulärdata](use-events-to-handle-and-submit-form-data.md).
* **Klientbaserad sändning** - Din app kan lyssna efter sändning eller samla in formulärdata från körningstillståndet och skicka den till dina egna API:er. [HTTP API:er](https://opensource.adobe.com/aem-forms-af-runtime/api/) dokumentlista, hämta, validera, skicka och spåra överföringsstatus.
* **Förifyll** - Data kan förifyllas via REST-slutpunkter eller serversidan så att läget redan är ifyllt när formuläret läses in. Se [Storybook - Exempel på förifyllning](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples—prefill-form-with-personalized-data).

## Gränssnitt och designkontroll {#ui-design-control}

### Kan jag använda mitt eget designsystem eller komponentbibliotek med headless-formulär?

Ja. Detta är en viktig fördel med headless-formulär. Med AEM Headless Adaptive Forms:

* Du **mappar** dina egna komponenter till formulärmodellen (efter fälttyp eller resurstyp). Se [Använd anpassade komponenter för att återge ett headless-format](developing-for-headless-forms-using-your-own-components.md) och [Använd Google materialgränssnittskomponenter för att återge ett headless-formulär](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Körningsmiljön innehåller **lägen och hanterare**. Dina komponenter återges med ditt designsystem och anropar hanterarna så att formulärlogiken hålls synkroniserad.
* Du kan använda **React Spectrum**, Material UI, Chakra UI eller något annat anpassat komponentbibliotek. [specifikationen](/help/assets/headless-adaptive-forms-specification.pdf) kan utökas för anpassade komponenter (t.ex. Chakra UI, Vue.js). Se [Frågor och svar - anpassade ramverk](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks).

### Har headless-formulär stöd för tillgänglighet (ARIA, tangentbordshantering)?

Hjälpmedel implementeras i det **gränssnittslager** som du anger. Det Headless-lagret återger inte DOM, så det lägger inte till ARIA eller tangentbordsbeteenden separat. Du får åtkomst genom att:

* Använder **hjälpmedelskomponenter** från ditt designsystem eller bibliotek (många omfattar ARIA och tangentbordsstöd).
* Följ **de bästa metoderna för hjälpmedel** i dina anpassade fältkomponenter (etiketter, felmeddelanden, fokushantering, tangentbordsnavigering).
* Kontrollera att den formulärstruktur och det tillstånd du får (t.ex. obligatoriskt, ogiltigt, synligt) återspeglas i komponenternas ARIA-attribut och -beteende.

Om du använder de färdiga React Spectrum-baserade komponenterna har du nytta av deras inbyggda tillgänglighet.

### Hur hanterar jag komplexa gränssnittskomponenter (datumväljare, anpassade listrutor)?

Hantera dem som **anpassade komponenter** mappade till motsvarande fälttyper eller anpassade resurstyper i formuläret JSON:

* Implementera komponenten så att den accepterar samma **props/state/handlers** som andra fältkomponenter (t.ex. via `useRuleEngine`).
* Använd **state** för värde, synlighet och giltighet. Använd **hanterare** för att uppdatera värde och utlösa validering.
* Rendera datumväljaren eller den anpassade listrutan med det valda gränssnittsbiblioteket. Om du ändrar något anropar du hanteraren med det nya värdet så att formulärstatusen förblir korrekt.

Se [Använd anpassade komponenter för att återge ett headless-formulär](developing-for-headless-forms-using-your-own-components.md) för mappning efter fälttyp och resurstyp.

### Kan jag lägga till eller ta bort fält dynamiskt (dynamiska formulär)?

Formulärstrukturen definieras av **form-JSON** som returneras från servern. Dynamiskt beteende uppnås genom att

* **Regler i formuläret JSON** - Visa/dölj, aktivera/inaktivera eller ange värden baserat på uttryck. [Affärsregelprocessorn](architecture.md) kör dessa regler. Dina komponenter reagerar på `state.visible` och liknande.
* **Serverdriven struktur** - Olika användare eller kontexter kan ta emot olika formulär-JSON (t.ex. olika steg eller avsnitt), så&quot;dynamisk&quot; kan betyda&quot;olika formulärdefinitioner per begäran&quot;.
* **Ändringar på klientsidan** - Om appen kan ändra formulärmodellen (t.ex. lägga till/ta bort objekt i en upprepningsbar struktur) kan körningsmiljön återspegla det. Den exakta kapaciteten beror på API:erna för formulärschemat och körningsmiljön.

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) innehåller exempel på dynamiskt beteende.

### Hur hanterar jag villkorliga fält (visa/dölj baserat på indata)?

Villkorsstyrd synlighet styrs av **regler** i form av JSON, som utvärderas av affärsregelprocessorn. Du definierar villkor (t.ex.&quot;när fält A är lika med X, visa fält B&quot;); körtidsbiblioteket uppdaterar läge (t.ex. `state.visible`). Dina komponenter behöver bara **respektera status** (t.ex. `if (!state.visible) return null;`). Ingen extra gränssnittslogik krävs för att visa/dölja bortom återgivning från läge. Cascading och conditional behavior beskrivs i [Adaptive Forms specification](/help/assets/headless-adaptive-forms-specification.pdf) och visas i [Storybook - cascading fields](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behavior—options&args=formJson.items[0].fieldType:drop down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items son.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down). Se även [Vanliga frågor - överlappande fält](faq.md#do-headless-adaptive-forms-support-cascading-fields).

## Prestanda och skalbarhet {#performance-scalability}

### Är headless-formulär mer avancerade än traditionella formulärbibliotek?

De kan vara det, men det beror på implementeringen:

* **Målinriktade uppdateringar** - En väldesignad headless-miljö uppdaterar bara det tillstånd som har ändrats och meddelar bara de komponenter som är beroende av den, vilket kan minska antalet onödiga återgivningar jämfört med en monolitisk formulärkomponent.
* **Mindre gränssnittspaket** - Du skickar bara de gränssnittskomponenter som du använder (ditt designsystem), inte en fullständig uppsättning bibliotekskomponenter.
* **Lazy loading** - Formulär-JSON kan hämtas vid behov. Initialpaketet kan bli mindre.

Prestanda beror också på hur du implementerar komponenterna (t.ex. undviker onödig återgivning och minnesisering).

### Hur minimerar de återgivningar?

* **Lägesform** - Formulärläget behålls i en struktur som tillåter finkorniga uppdateringar så att endast berörda delar av trädet behöver återges igen.
* **Kopplingsdesign** - Kopplingar som `useRuleEngine` kan implementeras för att prenumerera komponenter enbart på det tillstånd som de använder, så att överordnade och jämställda ändringar inte tvingar alla fält att återges igen.
* **Ditt ansvar** - Du kan minimera återgivningar ytterligare genom att använda React best practices (t.ex. `React.memo`, stabila återanrop) i dina anpassade komponenter.

### Skalar headless-formulär bra för stora flerstegsformulär?

Ja, när den är korrekt utformad:

* **Formulärdefinition** - Stora formulär kan delas upp i steg eller avsnitt i JSON. Det är bara det synliga steget/avsnittet som behöver vara helt aktivt i användargränssnittet, med en lat utvärdering av reglerna för dolda avsnitt om det stöds.
* **Läge** - Körningsmiljön innehåller ett sammanhängande formulärläge. Stegnavigering visar/döljer bara avsnitt eller uppdaterar&quot;aktuellt steg&quot; utan att duplicera data.
* **Chunking and lazy load** - Du kan hämta formulär-JSON i segment eller läsa in ytterligare avsnitt i steg framåt för att hålla den initiala nyttolasten och tolkningskostnaden låg.

För mycket stora formulär bör du överväga struktur (t.ex. guidesteg), serverdrivna formulärvarianter och mäta återgivning och regelkörning med verkliga nyttolaster.

## Integrering och ekosystem {#integration-ecosystem}

### Kan headless-formulär fungera med Next.js/SSR/Server Actions?

* **Next.js / React** - Ja. Reaktionsåtergivning och krokar fungerar i en React-miljö. Använd Forms Web SDK i klientkomponenterna. Hämta formulär-JSON på servern eller klienten efter behov.
* **SSR** - Du kan hämta formulär-JSON på servern och skicka det till klienten så att formuläret fylls med data. Formulärinteraktivitet (tillstånd, validering, regler) körs på den klient där SDK läses in. Undvik återgivning av formulärfält som är beroende av klientens tillstånd under SSR, eller använd en platshållare som är beroende av klientens tillstånd.
* **Serveråtgärder (Next.js)** - Du kan anropa serveråtgärder från din sändningshanterare: när användaren skickar in data, samlar klientkoden in formulärdata (från det headless-läget) och anropar en serveråtgärd i stället för eller utöver AEM sändningsslutpunkter.

### Hur integreras headless-formulär med CMS, headless commerce eller backend-system?

* **CMS** - AEM är CMS för formulärdefinitionen: författare skapar och publicerar formulär-JSON. Andra CMS-system kan referera till eller länka till formulärets URL/API. Din app hämtar formuläret från AEM (eller ett CDN) och hämtar eventuellt text eller layout från en annan CMS.
* **Förifyll och skicka** - [Förifyll](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples—prefill-form-with-personalized-data) och skicka kan träffa REST-slutpunkter, så att du kan förifylla från en CRM-, DAM- eller e-handelsserver och skicka till samma eller olika system. AEM Forms har även stöd för [Microsoft Dynamics och Salesforce](faq.md), REST, e-post och anpassade skicka-åtgärder.
* **Forms datamodell** - AEM Forms tillhandahåller en Forms datamodell för att ansluta till olika datakällor. Huvudlösa formulär kan använda dessa funktioner för förifyllning, validering och sändning utan att du själv behöver skapa varje integrering.

För mobil- och offlinescenarier rekommenderar vi att du [bygger din egen app och hämtar formulärdefinitioner via det Headless Adaptive Forms API](mobile-forms-best-practices.md).

## Se även {#see-also}

* [Ökning](overview.md)
* [Arkitektur](architecture.md)
* [Frågor och svar](faq.md)
* [Skapa och publicera ett headless-formulär](create-and-publish-a-headless-form.md)
* [Headless adaptive forms APIs](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [Kodspelaren](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
