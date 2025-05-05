---
title: Skapa ett Headless-formulär med Adaptive Forms editor
description: Skapa ett Headless-formulär med Adaptive Forms editor
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 0214dc2e-52ce-40e9-bef3-f4f4a7ff266f
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---

# Skapa ett Headless-formulär med Adaptive Forms editor {#create-a-headless-adaptive-form-using-adaptive-forms-editor}

AEM Forms as a Cloud Service har en användarvänlig redigerare för att skapa Headless Adaptive Forms. Med över 24 kärnkomponenter kan du enkelt skapa ett formulär genom att dra och släppa komponenter i redigeraren. I Regelredigeraren kan du dessutom lägga till valideringar i formulärfälten.

>[!NOTE]
>
> 
>Om du inte har använt Headless Adaptive Forms tidigare rekommenderar Adobe att du går igenom självstudiekursen [Skapa och publicerar ett headless-formulär med hjälp av startkit](create-and-publish-a-headless-form.md) för att lära dig grunderna och skapa ett headless adaptivt formulär innan du använder Adaptiv Forms-redigerare för Headless-formulär.

Så här skapar du ett Headless-formulär med Adaptive Forms Editor:

## Innan du börjar:

Du behöver följande för att skapa ett adaptivt formulär med hjälp av den adaptiva Forms-redigeraren:

**För AEM 6.5 Forms:**

* Åtkomst till en AEM 6.5.16.0 eller senare Forms-författarinstans.

* Adaptiva Forms Core-komponenter

* Adaptiv Forms Core Components-mall

* Ett adaptivt formulärtema för en mall baserad på kärnkomponenter

* Lägg till dina användare i gruppen [!DNL forms-users]. Medlemmarna i gruppen [!DNL forms-users] har behörighet att skapa ett anpassat formulär.


**För AEM Forms as a Cloud Service:**

* Åtkomst till en [AEM Forms as a Cloud Service author-instans](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service.html?lang=en) eller en [lokal AEM Forms as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-local-development-environment.html?lang=en) -miljö.

* **En mall för adaptiva formulär**: En mall innehåller en grundläggande struktur och definierar utseendet (layouter och format) för ett adaptivt formulär. Den har förformaterade komponenter som innehåller vissa egenskaper och innehållsstruktur. Här finns också alternativ för att definiera ett tema och en skicka-åtgärd. Temat definierar utseendet, känslan och skickaåtgärden definierar vilken åtgärd som ska vidtas när ett adaptivt formulär skickas in. Du kan till exempel skicka insamlade data till en datakälla. Molntjänsten tillhandahåller en OOTB-mall med namnet blank:

   * Mallen `blank Adaptive Forms (Core Components)` ingår i alla nya as a Cloud Service AEM Forms-program.
   * Du kan också [skapa en ny anpassad Forms-mall (kärnkomponenter)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/template-editor.html) från början.

* **Ett adaptivt formulärtema**: Ett tema innehåller formatinformation för komponenterna och panelerna. Format innehåller egenskaper som bakgrundsfärger, lägesfärger, genomskinlighet, justering och storlek. När du använder ett tema återspeglas det angivna formatet i motsvarande komponenter.  Mallen `Canvas` ingår i alla nya as a Cloud Service AEM Forms-program.

* **Behörigheter**: Lägg till dina användare i gruppen [!DNL forms-users]. Medlemmarna i gruppen [!DNL forms-users] har behörighet att skapa ett anpassat formulär. Detaljerad lista över formulärspecifika användargrupper finns i [Grupper och behörigheter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html).


## Skapa ett adaptivt formulär  {#create-an-adaptive-form-components}

1. Logga in på din [!DNL Experience Manager Forms] Author-instans.

1. Ange dina uppgifter på inloggningssidan för Experience Manager. När du är inloggad trycker du på **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** i det övre vänstra hörnet.

1. Tryck på **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]**. Guiden öppnas. På fliken Source väljer du en mall:

   ![Mall](/help/assets/core-components-template.png)

   När du väljer en mall markeras automatiskt ett tema och en skicka-åtgärd som anges i mallen och knappen **[!UICONTROL Create]** aktiveras. Du kan gå till flikarna **[!UICONTROL Style]** eller **[!UICONTROL Submission]** och välja ett annat tema eller skicka-åtgärd. Om den valda mallen inte anger något tema förblir knappen Skapa inaktiverad. Du kan gå till fliken **[!UICONTROL Styles]** och välja ett tema manuellt.

1. Välj ett tema på fliken **[!UICONTROL Style]**:

   * När den valda mallen anger ett tema väljs temat automatiskt i guiden. Du kan också välja ett annat tema på fliken Format.

   * Om den valda mallen inte anger något tema kan du använda fliken Format för att välja ett tema. Knappen **[!UICONTROL Create]** aktiveras först när ett tema har valts.

1. (Valfritt) Välj en datamodell på fliken Data:

   * **Formulärdatamodell**: Med en [formulärdatamodell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/data-integration.html) kan du integrera entiteter och tjänster från olika datakällor i ett adaptivt formulär. Välj Formulärdatamodell om det adaptiva formulär du skapar inbegriper att hämta och skriva data från och till flera datakällor.

   * **JSON-schema**: [JSON-schema](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html?lang=en) Adaptiv form tillåter sömlös integrering med din organisations back-end-system genom att ge möjlighet att associera ett JSON-schema, som representerar strukturen för de data som produceras eller förbrukas. Den här kopplingen gör det möjligt för författare att dynamiskt lägga till innehåll i det adaptiva formuläret med elementen i schemat. Elementen i schemat är enkelt tillgängliga på fliken Datamodellsobjekt i innehållsläsaren under redigeringsprocessen, och alla fält läggs automatiskt till i alla nya adaptiva formulär.

   Som standard markeras alla fält i det associerade JSON-schemat automatiskt och konverteras till motsvarande adaptiva formulärkomponenter, vilket effektiviserar redigeringsprocessen. I guiden kan du välja vilka fält som ska inkluderas i det anpassade formuläret med hjälp av kryssrutor.

1. Välj en sändningsåtgärd på fliken **[!UICONTROL Submission]**:

   * När du väljer en mall markeras åtgärden Skicka som anges i mallen automatiskt. Du kan välja en annan skickaåtgärd på fliken Skicka. Fliken **[!UICONTROL &#x200B; Submission]** visar alla tillgängliga skicka-åtgärder.

   * När den valda mallen inte anger någon skicka-åtgärd kan du använda fliken **[!UICONTROL Submission]** för att välja en skicka-åtgärd

1. (Valfritt) På fliken **[!UICONTROL Delivery]** kan du ange ett publicerings- eller avpubliceringsdatum för ett adaptivt formulär.

1. Tryck på **[!UICONTROL Create]**. En dialogruta där du kan ange namn, namn och plats för att spara det adaptiva formuläret visas:

   * **[!UICONTROL Title]** Anger formulärets visningsnamn. Titeln hjälper dig att identifiera formuläret i användargränssnittet för [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Anger formulärets namn. En nod med det angivna namnet skapas i databasen. När du börjar skriva en titel genereras värdet för namnfältet automatiskt. Du kan ändra det föreslagna värdet. Namnfältet får endast innehålla alfanumeriska tecken, bindestreck och understreck. Alla ogiltiga indata ersätts med ett bindestreck.
   * **[!UICONTROL Path:]** Anger platsen där det adaptiva formuläret ska sparas. Du kan spara det adaptiva formuläret direkt på `/content/dam/formsanddocuments` eller skapa en mapp som `/content/dam/formsanddocuments/adaptiveforms` om du vill spara ett adaptivt formulär. Se till att du skapar mappen innan du använder den i sökvägen. Fältet **[!UICONTROL Path]** skapar inte en mapp automatiskt.

1. Tryck på **[!UICONTROL Create]**. Ett adaptivt formulär skapas och öppnas i den adaptiva Forms-redigeraren. Redigeraren visar det innehåll som är tillgängligt i mallen.  Baserat på typen av adaptivt formulär visas formulärelementen i det associerade <!--XFA form template, XML schema or --> JSON-schemat eller formulärdatamodellen på fliken **[!UICONTROL Data Model Objects]** i **[!UICONTROL Content Browser]** i sidlisten. Du kan också dra och släppa dessa element för att skapa ett anpassat formulär.

Nu kan du dra och släppa de adaptiva Forms-komponenterna till den adaptiva Forms-behållaren för att utforma och skapa formuläret.


## Visa JSON-återgivning av ett adaptivt formulär {#preview-form}

Markera det adaptiva formuläret och tryck på **Förhandsgranska**. Förhandsgranskningen av formuläret visas. Om du vill visa formulärdefinitionen (JSON) för tillägget replace.html i URL:en med .model.json

Till exempel http://[author-server]:[port]/editor.html/content/forms/af/contact-us.model.json

Du kan använda API:t [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition) för Headless Adaptive Forms för att hämta formulärdefinitionen (JSON) och använda den i ditt program.

![Visa formulärdefination (JSOI)](assets/json-definantion.png)

