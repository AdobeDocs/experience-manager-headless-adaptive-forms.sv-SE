---
title: Aktivera Headless Adaptive Forms i AEM Forms as a Cloud Service
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: Lär dig hur du aktiverar headless adaptive forms på AEM Forms as a Cloud Service med vår steg-för-steg-guide. I vår självstudiekurs får du hjälp med processen så att du enkelt kan aktivera den här kraftfulla funktionen i din AEM Forms-miljö.
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# Aktivera Headless Adaptive Forms i AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

Om du aktiverar Headless Adaptive Forms på AEM Forms as a Cloud Service kan du börja skapa, publicera och leverera Headless Forms med AEM Forms Cloud Service-instanserna i flera kanaler. Du behöver en adaptiv Forms Core Components-aktiverad miljö för att kunna använda Headless Adaptive Forms.

## Överväganden

* När du skapar ett nytt as a Cloud Service AEM Forms-program är [Headless Adaptive Forms redan aktiverat för dina miljöer](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Om du har ett äldre as a Cloud Service Forms-program där Core Components [inte är aktiverade](#enable-components) kan du [lägga till adaptiva Forms Core Components-beroenden](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) i din AEM as a Cloud Service-databas och distribuera databasen till dina Cloud Service för att aktivera Headless Adaptive Forms.

* Om din befintliga Cloud Service-miljö innehåller alternativ för att [skapa Core Components-baserade Adaptive Forms](create-a-headless-adaptive-form.md) är Headless Adaptive Forms redan aktiverat för din miljö och du kan använda Core Component-baserad Adaptive Forms som headless-formulär för kanaler som mobil, webb, inbyggda appar och tjänster som kräver en huvudlös representation av Adaptive Forms.


>[!NOTE]
>
>
> Adobe tillhandahåller adaptiv Forms [starter kit (React App)](create-and-publish-a-headless-form.md) som hjälper utvecklare att snabbt komma igång med Headless Adaptive Forms-utveckling, utan att aktivera Headless Adaptive Forms i AEM Forms as a Cloud Service-miljö. Du kan aktivera den adaptiva Forms-miljön utan headless på en Forms as a Cloud Service-miljö senare efter en [snabbstart med utveckling av headless-formulär](create-and-publish-a-headless-form.md).

## Aktivera Headless Adaptive Forms för en as a Cloud Service AEM Forms-miljö

Utför följande steg i listad ordning för att aktivera Headless Adaptive Forms för en as a Cloud Service AEM Forms-miljö


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Klona din AEM Forms as a Cloud Service Git-databas {#clone-git-repository}

1. Logga in på [Cloud Manager](https://my.cloudmanager.adobe.com/) och välj organisation och program.

1. Gå till **pipelines**-kortet på sidan **Programöversikt** och klicka på knappen **Åtkomstrepoinformation** för att få tillgång till och hantera din Git-databas. Sidan innehåller följande information:

   * URL till Cloud Manager Git-databasen.
   * Autentiseringsuppgifter för Git-databasen (användarnamn och lösenord) Git-användarnamn.

   Klicka på **Generera lösenord** för att visa eller generera lösenordet.

1. Öppna terminalen eller kommandotolken på den lokala datorn och kör följande kommando:

   ```Shell
   git clone [Git Repository URL]
   ```

   Ange inloggningsuppgifterna när du uppmanas att göra det. Databasen klonas till din lokala dator.


## 2. Lägg till adaptiva Forms Core-komponentberoenden i Git-databasen {#add-adaptive-forms-core-components-dependencies}

1. Öppna Git-databasmappen i en kodredigerare för oformaterad text. Exempel: VS-kod.
1. Öppna filen `[AEM Repository Folder]\pom.xml` för redigering.
1. Ersätt versioner av komponenterna `core.forms.components.version`, `core.forms.components.af.version` och `core.wcm.components.version` med versioner som anges i [dokumentationen för kärnkomponenter](https://github.com/adobe/aem-core-forms-components). Om komponenten inte finns lägger du till dessa komponenter.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Uppge den senaste versionen av Forms Core Components](/help/assets/latest-forms-component-version.png)

1. Lägg till följande beroenden i avsnittet Beroenden i filen `[AEM Repository Folder]\pom.xml` och spara filen.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Öppna filen `[AEM Repository Folder]/all/pom.xml` för redigering. Lägg till följande beroenden i avsnittet `<embeddeds>` och spara filen.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Ersätt `${appId}` med ditt appId.
   >
   >  Om du vill hitta din `${appId}` söker du efter termen `-packages/application/install` i filen `[AEM Repository Folder]/all/pom.xml`. Texten före termen `-packages/application/install` är din `${appId}`. Följande kod, `myheadlessform`, är till exempel `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Lägg till följande beroenden i `<dependencies>`-delen av filen `[AEM Repository Folder]/all/pom.xml` och spara filen:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Öppna `[AEM Repository Folder]/ui.apps/pom.xml` för redigering. Lägg till `af-core bundle`-beroendet och spara filen.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Kontrollera att följande adaptiva Forms Core Components-artefakter inte ingår i ditt projekt.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > och
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Spara och stäng filen.

## 3. Uppdatera projektet så att det innehåller den senaste versionen av Forms Core Components:

1. Öppna projektmappen [AEM Archetype]/pom.xml för redigering.


1. Spara och stäng filen.

## 4. Implementera uppdateringarna i din Git-databas och kör pipeline för att distribuera databasen {#Commit-the-updates-to-your-git-repository}

1. Så här implementerar du kod i din Git-databas:
   1. Öppna terminalen eller kommandotolken.
   1. Navigera till `[AEM Repository Folder]` och kör följande kommandon i den ordning som visas

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. [Kör pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=sv-SE) när filerna har implementerats i Git-databasen.

   När pipeline-körningen har slutförts aktiveras adaptiva Forms Core-komponenter för motsvarande miljö. Dessutom har en adaptiv Forms-mall (Core Components) och Canvas 3.0-temat lagts till i Forms as a Cloud Service miljö, med alternativ för att anpassa och skapa Core Components-baserade Adaptive Forms.


## Vanliga frågor {#faq}

### Vad är kärnkomponenter? {#core-components}

[Kärnkomponenterna](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=sv-SE) är en uppsättning standardiserade WCM-komponenter (Web Content Management) för AEM som snabbar upp utvecklingstiden och minskar underhållskostnaderna för dina webbplatser.

### Vilka funktioner finns det för att aktivera kärnkomponenter? {#core-components-capabilities}

När de adaptiva Forms Core-komponenterna är aktiverade för din miljö läggs en tom Core Components-baserad Adaptive Form-mall och Canvas 3.0-tema till i din miljö. När du har aktiverat adaptiva Forms Core-komponenter för din miljö kan du:

* Skapa grundkomponentbaserade adaptiva Forms.
* Skapa grundkomponentbaserade adaptiva formulärmallar.
* Skapa egna teman för grundkomponentbaserade adaptiva formulärmallar.
* Servera Core Component-baserade Adaptive Form JSON-representationer för kanaler som mobiler, webben, inbyggda appar och tjänster som kräver att ett formulär visas utan rubrik.

### Är adaptiva Forms Core-komponenter aktiverade för min miljö? {#enable-components}

Så här kontrollerar du att adaptiva Forms Core-komponenter är aktiverade för din miljö:

1. [Klona din AEM Forms as a Cloud Service-databas](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Öppna `[AEM Repository Folder]/all/pom.xml`-filen för din AEM Forms Cloud Service Git-databas.

1. Sök efter följande beroenden:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![leta reda på artefakten core-forms-components-af-core i all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Om det finns beroenden aktiveras adaptiva Forms Core-komponenter för din miljö.
