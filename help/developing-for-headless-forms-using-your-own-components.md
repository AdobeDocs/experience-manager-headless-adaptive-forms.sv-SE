---
title: Använd anpassade komponenter för att återge ett headless-formulär
description: Lär dig hur du skapar anpassade komponenter och mappar dem till fält för Headless Adaptive Forms. I den här handboken beskrivs hur du mappar komponenter efter fälttyp och resurstyp för att få anpassad återgivning och beteende.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Använd anpassade komponenter för att återge ett headless-formulär {#developing-for-headless-forms-using-your-own-components}

I Headless Adaptive Forms kan du skapa och implementera anpassade komponenter för att definiera formulärens utseende och funktion. Standardkomponenterna har standardbeteende, men du kan behöva specifika gränssnittselement eller interaktioner, till exempel en anpassad&quot;Announcement&quot;-komponent eller ett specialiserat&quot;Scribble Signature&quot;-fält.

I den här artikeln får du hjälp med att skapa en anpassad React-komponent och mappa den till ditt Headless Adaptive-formulär.

## &#x200B;1. Skapa en anpassad reaktionskomponent

Skapa först komponenten React som återger formulärfältet. Komponenten kan använda vilket React-bibliotek som helst (som materialgränssnitt, Ant Design eller dina egna anpassade format).

Låt oss till exempel skapa en anpassad **Announcement**-komponent som återger ett skrivskyddat meddelande med en viss formatering.

1. Navigera till komponentkatalogen för ditt React-projekt (t.ex. `src/components`).
2. Skapa en ny mapp och fil för komponenten, till exempel `Announcement/index.tsx`.
3. Implementera komponenten. Den ska acceptera `props` som är kompatibel med den Headless Forms-miljön (som oftast tar emot fältets tillstånd).

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. Mappa den anpassade komponenten

Om du vill använda den anpassade komponenten måste du mappa den i filen `mappings.ts`. Den Headless Forms-miljön använder den här mappningen för att avgöra vilken React-komponent som ska återges för varje fält i formuläret JSON.

Det finns två primära sätt att mappa komponenter: av **fälttyp** eller av **resurstyp**.

### Mappning efter fälttyp

Standardmappningen baseras på egenskapen `fieldType` i Form JSON (t.ex. `text-input`, `checkbox`, `button`). Detta är användbart när du vill ersätta *alla* -instanser av en standardkomponent med din anpassade version.

1. Öppna `src/utils/mappings.ts` (eller var dina mappningar är definierade).
2. Importera den anpassade komponenten.
3. Lägg till den i mappningsobjektet med `fieldType` som nyckel.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### Mappning efter resurstyp (anpassade komponenter)

Om du har skapat en anpassad komponent i AEM (t.ex. en meddelandekomponent som utökar en standardtextkomponent) och du bara vill återge *den specifika komponenten* på ett annat sätt i React-appen, bör du mappa den efter dess **Resurstyp** eller en unik identifierare.

På så sätt kan du ha standardtextkomponenter som återges normalt, medan den anpassade meddelandekomponenten använder den specialiserade React-implementeringen.

1. Identifiera komponentens unika identifierare. I den Headless Form JSON finns detta ofta i egenskapen `:type` eller i en anpassad `fieldType` om den är konfigurerad.
2. Lägg till mappningen med denna identifierare.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **Obs!** Kontrollera att AEM-formulärmodellen exporterar rätt `:type` eller identifierare som matchar nyckeln som du använder i `mappings.ts`.

## &#x200B;3. Använd mappningarna

Kontrollera slutligen att Headless Form-instansen använder dessa anpassade mappningar.

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

Med dessa steg kan du utöka funktionaliteten i din Headless Adaptive Forms med komponenter som matchar dina specifika design- och funktionskrav.
